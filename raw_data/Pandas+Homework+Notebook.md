

```python
import pandas as pd
import numpy as np

schooldf = pd.read_csv ("schools_complete.csv")
studentdf = pd.read_csv ("students_complete.csv")

schooldf.rename_axis({'name':'school'},axis=1,inplace=True)
schoolnewdf = schooldf.copy()

```


```python
schooldf.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>school</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Figueroa High School</td>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Shelton High School</td>
      <td>Charter</td>
      <td>1761</td>
      <td>1056600</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Hernandez High School</td>
      <td>District</td>
      <td>4635</td>
      <td>3022020</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Griffin High School</td>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
    </tr>
  </tbody>
</table>
</div>




```python
schooldf.columns.tolist()
```




    ['School ID', 'school', 'type', 'size', 'budget']




```python
studentdf.head
```




    <bound method NDFrame.head of        Student ID                 name gender grade              school  \
    0               0         Paul Bradley      M   9th   Huang High School   
    1               1         Victor Smith      M  12th   Huang High School   
    2               2      Kevin Rodriguez      M  12th   Huang High School   
    3               3    Dr. Richard Scott      M  12th   Huang High School   
    4               4           Bonnie Ray      F   9th   Huang High School   
    5               5        Bryan Miranda      M   9th   Huang High School   
    6               6        Sheena Carter      F  11th   Huang High School   
    7               7         Nicole Baker      F  12th   Huang High School   
    8               8         Michael Roth      M  10th   Huang High School   
    9               9       Matthew Greene      M  10th   Huang High School   
    10             10     Andrew Alexander      M  10th   Huang High School   
    11             11        Daniel Cooper      M  10th   Huang High School   
    12             12      Brittney Walker      F   9th   Huang High School   
    13             13         William Long      M   9th   Huang High School   
    14             14         Tammy Hebert      F  10th   Huang High School   
    15             15    Dr. Jordan Carson      M  11th   Huang High School   
    16             16        Donald Zamora      M   9th   Huang High School   
    17             17    Kimberly Santiago      F   9th   Huang High School   
    18             18        Kevin Stevens      M   9th   Huang High School   
    19             19         Brandi Lyons      F   9th   Huang High School   
    20             20           Lisa Davis      F  10th   Huang High School   
    21             21        Kristen Lopez      F  10th   Huang High School   
    22             22     Kimberly Stewart      F  11th   Huang High School   
    23             23   Christopher Parker      M   9th   Huang High School   
    24             24     Chelsea Griffith      F  11th   Huang High School   
    25             25         Cesar Morris      M   9th   Huang High School   
    26             26       Melanie Decker      F   9th   Huang High School   
    27             27       Tracey Oconnor      F  10th   Huang High School   
    28             28          Kelly James      F  11th   Huang High School   
    29             29         Nicole Brown      F  12th   Huang High School   
    ...           ...                  ...    ...   ...                 ...   
    39140       39140   Cheyenne Hernandez      F   9th  Thomas High School   
    39141       39141    Jonathan Sullivan      M  10th  Thomas High School   
    39142       39142  Deborah Higgins DDS      F  10th  Thomas High School   
    39143       39143       Steven Jackson      M  11th  Thomas High School   
    39144       39144     Cristian Webster      M  12th  Thomas High School   
    39145       39145           Audrey Fry      F  10th  Thomas High School   
    39146       39146      Michael Carroll      M   9th  Thomas High School   
    39147       39147      Raymond Hawkins      M  10th  Thomas High School   
    39148       39148   Christopher Wilson      M  10th  Thomas High School   
    39149       39149      Glenda Fletcher      F  11th  Thomas High School   
    39150       39150    Jennifer Hamilton      F  11th  Thomas High School   
    39151       39151     Shannon Williams      F  10th  Thomas High School   
    39152       39152           Lori Moore      F   9th  Thomas High School   
    39153       39153      William Hubbard      M   9th  Thomas High School   
    39154       39154      Bradley Johnson      M  12th  Thomas High School   
    39155       39155          John Brooks      M  10th  Thomas High School   
    39156       39156  Stephanie Contreras      F  11th  Thomas High School   
    39157       39157     Kristen Gonzalez      F   9th  Thomas High School   
    39158       39158        Kari Holloway      F  10th  Thomas High School   
    39159       39159     Kimberly Cabrera      F  11th  Thomas High School   
    39160       39160         Katie Weaver      F  11th  Thomas High School   
    39161       39161          April Reyes      F  10th  Thomas High School   
    39162       39162          Derek Weeks      M  12th  Thomas High School   
    39163       39163           John Reese      M  11th  Thomas High School   
    39164       39164       Joseph Anthony      M   9th  Thomas High School   
    39165       39165         Donna Howard      F  12th  Thomas High School   
    39166       39166            Dawn Bell      F  10th  Thomas High School   
    39167       39167       Rebecca Tanner      F   9th  Thomas High School   
    39168       39168         Desiree Kidd      F  10th  Thomas High School   
    39169       39169      Carolyn Jackson      F  11th  Thomas High School   
    
           reading_score  math_score  
    0                 66          79  
    1                 94          61  
    2                 90          60  
    3                 67          58  
    4                 97          84  
    5                 94          94  
    6                 82          80  
    7                 96          69  
    8                 95          87  
    9                 96          84  
    10                90          70  
    11                78          77  
    12                64          79  
    13                71          79  
    14                85          67  
    15                94          88  
    16                88          55  
    17                74          75  
    18                64          69  
    19                89          80  
    20                91          89  
    21                90          77  
    22                99          84  
    23                81          68  
    24                85          73  
    25                92          70  
    26                63          85  
    27                80          58  
    28                73          55  
    29                90          88  
    ...              ...         ...  
    39140             76          99  
    39141             86          93  
    39142             96          83  
    39143             71          93  
    39144             77          87  
    39145             94          74  
    39146             69          95  
    39147             88          81  
    39148             89          89  
    39149             82          93  
    39150             80          75  
    39151             84          73  
    39152             98          84  
    39153             80          75  
    39154             91          71  
    39155             92          98  
    39156             79          95  
    39157             79          94  
    39158             87          90  
    39159             85          72  
    39160             89          86  
    39161             70          84  
    39162             94          77  
    39163             90          75  
    39164             97          76  
    39165             99          90  
    39166             95          70  
    39167             73          84  
    39168             99          90  
    39169             95          75  
    
    [39170 rows x 7 columns]>




```python
studentdf.columns.tolist()
```




    ['Student ID',
     'name',
     'gender',
     'grade',
     'school',
     'reading_score',
     'math_score']




```python
#District Summary

Dschooldf = schooldf[schooldf['type'] == 'District']
Totalschools = Dschooldf.shape[0]

DStudenttotal = Dschooldf['size'].sum()

DBudget = Dschooldf['budget'].sum()

DSchoolStudentMerge = Dschooldf.merge(studentdf,how='outer',on='school')

DMathAVG = DSchoolStudentMerge.groupby(['type'])['math_score'].mean()[0]

DReadingAVG = DSchoolStudentMerge.groupby(['type'])['reading_score'].mean()[0]

DMathPass = DSchoolStudentMerge[DSchoolStudentMerge['math_score'] >= 70]

DReadingPass = DSchoolStudentMerge[DSchoolStudentMerge['reading_score'] >= 70]

DNumReading = DReadingPass.groupby(['type'])['Student ID'].count()[0]

DNumMath = DMathPass.groupby(['type'])['Student ID'].count()[0]

#PercentMath = (DMathPass/DStudenttotal)*100

#PercentReading = (DReadingPass/DStudenttotal)*100


DOverallPassing = (DReadingAVG+DMathAVG)/2

d = {'Total_School': [Totalschools],
     'Total_Students': [DStudenttotal],
     'Total_Budget': [DBudget],
     'Average_Math_score':[DMathAVG],
     'Average_Reading_score':[DReadingAVG],
    # '%Passing Math': [PercentMath],
    # '%Passing Reading': [PercentReading],
     '%Overall Passing Rate': [DOverallPassing]}

DSummary = pd.DataFrame(d)

DSummary = DSummary[['Total_School',
                     'Total_Students',
                     'Total_Budget',
                     'Average_Math_score',
                     'Average_Reading_score',
                     #'%Passing Math',
                    # '%Passing Reading',
                     '%Overall Passing Rate' ]]

DSummary
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Total_School</th>
      <th>Total_Students</th>
      <th>Total_Budget</th>
      <th>Average_Math_score</th>
      <th>Average_Reading_score</th>
      <th>%Overall Passing Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7</td>
      <td>26976</td>
      <td>17347923</td>
      <td>76.987026</td>
      <td>80.962485</td>
      <td>78.974755</td>
    </tr>
  </tbody>
</table>
</div>




```python
#School Summary

Dschooldf['Per Student Budget'] = Dschooldf['budget']/Dschooldf['size']

pd.options.mode.chained_assignment = None

del Dschooldf['School ID']

AVGPassMR = studentdf.groupby(['school'])['reading_score','math_score'].mean().reset_index()

Dschooldf = Dschooldf.merge(AVGPassMR,on='school',how='outer')

PassR = studentdf[studentdf['reading_score'] >= 70]
PassM = studentdf[studentdf['math_score'] >= 70]

PassRSummary =PassR.groupby(['school'])['reading_score'].count().reset_index()
PassRSummary.rename_axis({'reading_score':'reading_count'},axis=1,inplace=True)

PassMSummary = PassM.groupby(['school'])['math_score'].count().reset_index()
PassMSummary.rename_axis({'math_score':'math_count'},axis=1,inplace=True)

PassCount = PassMSummary.merge(PassMSummary,on='school',how='inner')

Dschooldf = Dschooldf.merge(PassCount,on='school',how='outer')

#Dschooldf['% Passing Math'] = (Dschooldf['math_count']/Dschooldf['size'])*100
#Dschooldf['% Passing Reading'] = (Dschooldf['reading_count']/Dschooldf['size'])*100

#Dschooldf['% Overall Passing'] = (Dschooldf['% Passing Math'] + Dschooldf['% Passing Reading'])/2

Dschooldf.rename_axis({'reading_score':'Average Reading Score',
                       'math_score': 'Average Math Score'},axis= 1 , inplace= True)

Dschooldf
                                                    
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>school</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
      <th>Per Student Budget</th>
      <th>Average Reading Score</th>
      <th>Average Math Score</th>
      <th>math_count_x</th>
      <th>math_count_y</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917.0</td>
      <td>1910635.0</td>
      <td>655.0</td>
      <td>81.182722</td>
      <td>76.629414</td>
      <td>1916</td>
      <td>1916</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Figueroa High School</td>
      <td>District</td>
      <td>2949.0</td>
      <td>1884411.0</td>
      <td>639.0</td>
      <td>81.158020</td>
      <td>76.711767</td>
      <td>1946</td>
      <td>1946</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Hernandez High School</td>
      <td>District</td>
      <td>4635.0</td>
      <td>3022020.0</td>
      <td>652.0</td>
      <td>80.934412</td>
      <td>77.289752</td>
      <td>3094</td>
      <td>3094</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Bailey High School</td>
      <td>District</td>
      <td>4976.0</td>
      <td>3124928.0</td>
      <td>628.0</td>
      <td>81.033963</td>
      <td>77.048432</td>
      <td>3318</td>
      <td>3318</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Rodriguez High School</td>
      <td>District</td>
      <td>3999.0</td>
      <td>2547363.0</td>
      <td>637.0</td>
      <td>80.744686</td>
      <td>76.842711</td>
      <td>2654</td>
      <td>2654</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Johnson High School</td>
      <td>District</td>
      <td>4761.0</td>
      <td>3094650.0</td>
      <td>650.0</td>
      <td>80.966394</td>
      <td>77.072464</td>
      <td>3145</td>
      <td>3145</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Ford High School</td>
      <td>District</td>
      <td>2739.0</td>
      <td>1763916.0</td>
      <td>644.0</td>
      <td>80.746258</td>
      <td>77.102592</td>
      <td>1871</td>
      <td>1871</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Cabrera High School</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>83.975780</td>
      <td>83.061895</td>
      <td>1749</td>
      <td>1749</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Griffin High School</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>83.816757</td>
      <td>83.351499</td>
      <td>1371</td>
      <td>1371</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Holden High School</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>83.814988</td>
      <td>83.803279</td>
      <td>395</td>
      <td>395</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Pena High School</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>84.044699</td>
      <td>83.839917</td>
      <td>910</td>
      <td>910</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Shelton High School</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>83.725724</td>
      <td>83.359455</td>
      <td>1653</td>
      <td>1653</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Thomas High School</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>83.848930</td>
      <td>83.418349</td>
      <td>1525</td>
      <td>1525</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Wilson High School</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>83.989488</td>
      <td>83.274201</td>
      <td>2143</td>
      <td>2143</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Wright High School</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>83.955000</td>
      <td>83.682222</td>
      <td>1680</td>
      <td>1680</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Top Performing Schools by passing rate
TopSchool_PassRatedf = Dschooldf.sort_values(by=['% Overall Passing'],ascending=False).head(5)

TopSchool_PassRatedf.style.background_gradient(cmap=cm,subset=['% Overall Passing'])


```


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    ~/anaconda3/lib/python3.6/site-packages/pandas/core/indexes/base.py in get_loc(self, key, method, tolerance)
       2441             try:
    -> 2442                 return self._engine.get_loc(key)
       2443             except KeyError:


    pandas/_libs/index.pyx in pandas._libs.index.IndexEngine.get_loc()


    pandas/_libs/index.pyx in pandas._libs.index.IndexEngine.get_loc()


    pandas/_libs/hashtable_class_helper.pxi in pandas._libs.hashtable.PyObjectHashTable.get_item()


    pandas/_libs/hashtable_class_helper.pxi in pandas._libs.hashtable.PyObjectHashTable.get_item()


    KeyError: '% Overall Passing'

    
    During handling of the above exception, another exception occurred:


    KeyError                                  Traceback (most recent call last)

    <ipython-input-96-4b76c146ac14> in <module>()
          1 #Top Performing Schools by passing rate
    ----> 2 TopSchool_PassRatedf = Dschooldf.sort_values(by=['% Overall Passing'],ascending=False).head(5)
          3 
          4 TopSchool_PassRatedf.style.background_gradient(cmap=cm,subset=['% Overall Passing'])
          5 


    ~/anaconda3/lib/python3.6/site-packages/pandas/core/frame.py in sort_values(self, by, axis, ascending, inplace, kind, na_position)
       3184 
       3185             by = by[0]
    -> 3186             k = self.xs(by, axis=other_axis).values
       3187             if k.ndim == 2:
       3188 


    ~/anaconda3/lib/python3.6/site-packages/pandas/core/generic.py in xs(self, key, axis, level, drop_level)
       2021 
       2022         if axis == 1:
    -> 2023             return self[key]
       2024 
       2025         self._consolidate_inplace()


    ~/anaconda3/lib/python3.6/site-packages/pandas/core/frame.py in __getitem__(self, key)
       1962             return self._getitem_multilevel(key)
       1963         else:
    -> 1964             return self._getitem_column(key)
       1965 
       1966     def _getitem_column(self, key):


    ~/anaconda3/lib/python3.6/site-packages/pandas/core/frame.py in _getitem_column(self, key)
       1969         # get column
       1970         if self.columns.is_unique:
    -> 1971             return self._get_item_cache(key)
       1972 
       1973         # duplicate columns & possible reduce dimensionality


    ~/anaconda3/lib/python3.6/site-packages/pandas/core/generic.py in _get_item_cache(self, item)
       1643         res = cache.get(item)
       1644         if res is None:
    -> 1645             values = self._data.get(item)
       1646             res = self._box_item_values(item, values)
       1647             cache[item] = res


    ~/anaconda3/lib/python3.6/site-packages/pandas/core/internals.py in get(self, item, fastpath)
       3588 
       3589             if not isnull(item):
    -> 3590                 loc = self.items.get_loc(item)
       3591             else:
       3592                 indexer = np.arange(len(self.items))[isnull(self.items)]


    ~/anaconda3/lib/python3.6/site-packages/pandas/core/indexes/base.py in get_loc(self, key, method, tolerance)
       2442                 return self._engine.get_loc(key)
       2443             except KeyError:
    -> 2444                 return self._engine.get_loc(self._maybe_cast_indexer(key))
       2445 
       2446         indexer = self.get_indexer([key], method=method, tolerance=tolerance)


    pandas/_libs/index.pyx in pandas._libs.index.IndexEngine.get_loc()


    pandas/_libs/index.pyx in pandas._libs.index.IndexEngine.get_loc()


    pandas/_libs/hashtable_class_helper.pxi in pandas._libs.hashtable.PyObjectHashTable.get_item()


    pandas/_libs/hashtable_class_helper.pxi in pandas._libs.hashtable.PyObjectHashTable.get_item()


    KeyError: '% Overall Passing'



```python
#Bottom Performing schools by passing rate

BottomSchool_PassRatedf = Dschooldf.sort_values(by=['% Overall Passing']).head(5)

BottomSchool_PassRatedf.style.background_gradient(cmap=cm,subset=['% Overall Passing'])
```


```python
#math scores by grade
MScoreAVGdf =pd.pivot_table(studentdf,values=['math_score'],index=['school'],columns=['grade'])
MScoreAVGdf = MScoreAVGdf.reindex_axis(labels=['9th',
                                               '10th',
                                               '11th',
                                               '12th'],axis=1,level=1)
MScoreAVGdf
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th></th>
      <th colspan="4" halign="left">math_score</th>
    </tr>
    <tr>
      <th>grade</th>
      <th>9th</th>
      <th>10th</th>
      <th>11th</th>
      <th>12th</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>77.083676</td>
      <td>76.996772</td>
      <td>77.515588</td>
      <td>76.492218</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>83.094697</td>
      <td>83.154506</td>
      <td>82.765560</td>
      <td>83.277487</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>76.403037</td>
      <td>76.539974</td>
      <td>76.884344</td>
      <td>77.151369</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>77.361345</td>
      <td>77.672316</td>
      <td>76.918058</td>
      <td>76.179963</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>82.044010</td>
      <td>84.229064</td>
      <td>83.842105</td>
      <td>83.356164</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>77.438495</td>
      <td>77.337408</td>
      <td>77.136029</td>
      <td>77.186567</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>83.787402</td>
      <td>83.429825</td>
      <td>85.000000</td>
      <td>82.855422</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>77.027251</td>
      <td>75.908735</td>
      <td>76.446602</td>
      <td>77.225641</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>77.187857</td>
      <td>76.691117</td>
      <td>77.491653</td>
      <td>76.863248</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>83.625455</td>
      <td>83.372000</td>
      <td>84.328125</td>
      <td>84.121547</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>76.859966</td>
      <td>76.612500</td>
      <td>76.395626</td>
      <td>77.690748</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>83.420755</td>
      <td>82.917411</td>
      <td>83.383495</td>
      <td>83.778976</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>83.590022</td>
      <td>83.087886</td>
      <td>83.498795</td>
      <td>83.497041</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>83.085578</td>
      <td>83.724422</td>
      <td>83.195326</td>
      <td>83.035794</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>83.264706</td>
      <td>84.010288</td>
      <td>83.836782</td>
      <td>83.644986</td>
    </tr>
  </tbody>
</table>
</div>




```python
#reading scores by grade
RScoreAVGdf=pd.pivot_table(studentdf,values=['reading_score'],index=['school'],columns=['grade'])
RScoreAVGdf = RScoreAVGdf.reindex_axis(labels=['9th',
                                               '10th',
                                               '11th',
                                               '12th'],axis=1,level=1)
RScoreAVGdf
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th></th>
      <th colspan="4" halign="left">reading_score</th>
    </tr>
    <tr>
      <th>grade</th>
      <th>9th</th>
      <th>10th</th>
      <th>11th</th>
      <th>12th</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>81.303155</td>
      <td>80.907183</td>
      <td>80.945643</td>
      <td>80.912451</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>83.676136</td>
      <td>84.253219</td>
      <td>83.788382</td>
      <td>84.287958</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>81.198598</td>
      <td>81.408912</td>
      <td>80.640339</td>
      <td>81.384863</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>80.632653</td>
      <td>81.262712</td>
      <td>80.403642</td>
      <td>80.662338</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>83.369193</td>
      <td>83.706897</td>
      <td>84.288089</td>
      <td>84.013699</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>80.866860</td>
      <td>80.660147</td>
      <td>81.396140</td>
      <td>80.857143</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>83.677165</td>
      <td>83.324561</td>
      <td>83.815534</td>
      <td>84.698795</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>81.290284</td>
      <td>81.512386</td>
      <td>81.417476</td>
      <td>80.305983</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>81.260714</td>
      <td>80.773431</td>
      <td>80.616027</td>
      <td>81.227564</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>83.807273</td>
      <td>83.612000</td>
      <td>84.335938</td>
      <td>84.591160</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>80.993127</td>
      <td>80.629808</td>
      <td>80.864811</td>
      <td>80.376426</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>84.122642</td>
      <td>83.441964</td>
      <td>84.373786</td>
      <td>82.781671</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>83.728850</td>
      <td>84.254157</td>
      <td>83.585542</td>
      <td>83.831361</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>83.939778</td>
      <td>84.021452</td>
      <td>83.764608</td>
      <td>84.317673</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>83.833333</td>
      <td>83.812757</td>
      <td>84.156322</td>
      <td>84.073171</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Scores by School Spending

SchoolSpendingdf = Dschooldf.copy()

bins= [0,585000,615000,645000,675000]
group_name=['<$585', '585 to 615', '615 to 645', '645 to 675']

pd.cut(SchoolSpendingdf["Per Student Budget"], bins, labels=group_name)
SchoolSpendingdf["Per Student Budget"] = pd.cut(SchoolSpendingdf["Per Student Budget"], bins, labels=group_name)
spending_group = SchoolSpendingdf.groupby("Per Student Budget")
spending_group.max()

```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>school</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
      <th>Average Reading Score</th>
      <th>Average Math Score</th>
      <th>math_count_x</th>
      <th>math_count_y</th>
    </tr>
    <tr>
      <th>Per Student Budget</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>&lt;$585</th>
      <td>Rodriguez High School</td>
      <td>District</td>
      <td>4976.0</td>
      <td>3124928.0</td>
      <td>81.182722</td>
      <td>77.289752</td>
      <td>3318.0</td>
      <td>3318.0</td>
    </tr>
    <tr>
      <th>585 to 615</th>
      <td>None</td>
      <td>None</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>615 to 645</th>
      <td>None</td>
      <td>None</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>645 to 675</th>
      <td>None</td>
      <td>None</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
# scores by school size

SizeScore = schooldf.copy()

label = np.array(['small','medium','large'])

SizeScore['size'] = pd.qcut(SizeScore['size'],3,labels=label)

SizeScore = SizeScore.groupby(['size'])['Average Reading Score',
                                        'Average Math Score', 
                                        #'% Passing Math',
                                        #'% Passing Reading',
                                       # '% Overall Passing'].mean().reset_index()

SizeScore = SizeScore.reindex_axis(labels=[2,1,0])
SizeScore.set_index(keys=['size'],inplace=True)

SizeScore
```


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    <ipython-input-108-49a44b9b76f0> in <module>()
         11                                         #'% Passing Math',
         12                                         #'% Passing Reading',
    ---> 13                                         '% Overall Passing'].mean().reset_index()
         14 
         15 SizeScore = SizeScore.reindex_axis(labels=[2,1,0])


    ~/anaconda3/lib/python3.6/site-packages/pandas/core/base.py in __getitem__(self, key)
        342                 bad_keys = list(set(key).difference(self.obj.columns))
        343                 raise KeyError("Columns not found: %s"
    --> 344                                % str(bad_keys)[1:-1])
        345             return self._gotitem(list(key), ndim=2)
        346 


    KeyError: "Columns not found: 'Average Math Score', '% Overall Passing', 'Average Reading Score'"



```python
# scores by school type

ScoreSType = schooldf.copy()

ScoreSType = ScoreSType.groupby(['type'])['Average Reading Score',
                                          'Average Math Score',
                                          '% Passing Math',
                                          '% Passing Reading',
                                          '% Overall Passing'].mean().reset_

ScoreSType.set_index('type',inplace=True)

ScoreSType
```


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    <ipython-input-109-fe31b54bca2e> in <module>()
          7                                           '% Passing Math',
          8                                           '% Passing Reading',
    ----> 9                                           '% Overall Passing'].mean().reset_
         10 
         11 ScoreSType.set_index('type',inplace=True)


    ~/anaconda3/lib/python3.6/site-packages/pandas/core/base.py in __getitem__(self, key)
        342                 bad_keys = list(set(key).difference(self.obj.columns))
        343                 raise KeyError("Columns not found: %s"
    --> 344                                % str(bad_keys)[1:-1])
        345             return self._gotitem(list(key), ndim=2)
        346 


    KeyError: "Columns not found: '% Passing Math', '% Overall Passing', '% Passing Reading', 'Average Math Score', 'Average Reading Score'"

