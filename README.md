# Ex02-Outlier
## AIM:
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them
## EXPLANATION:
An Outlier is an observation in a given dataset that lies far from the rest of the observations. That means an outlier is vastly larger or smaller than the remaining values in the set. An outlier is an observation of a data point that lies an abnormal distance from other values in a given population. (odd man out). Outliers badly affect mean and standard deviation of the dataset. These may statistically give erroneous results.

## ALGORITHM:

   -  Step1: Read the given Data.
   - Step2: Get the information about the data.
   - Step3: Detect the Outliers using IQR method and Z score.
   - Step4: Remove the outliers.
   - Step5: Plot the datas using Box Plot.
     212222230123
     ROSHINI RK
## CODE:
# bhp.csv:
```
import pandas as pd
import seaborn as sns
import numpy as np
from scipy import stats
from google.colab import files
uploaded=files.upload()
df=pd.read_csv('bhp.csv')
df.info()
print(df.describe())
df.head()
#BEFORE REMOVING OUTLIER
sns.boxplot(y='price_per_sqft',data=df)

# PERFORMING IQR METHOD
q1=df['price_per_sqft'].quantile(0.25)
q3=df['price_per_sqft'].quantile(0.75)
IQR=q3-q1
low=q1-1.5*IQR
high=q3+1.5*IQR
new=df[((df['price_per_sqft']>=low)&(df['price_per_sqft']<=high))]

#AFTER REMOVING OUTLIER using IQR method
sns.boxplot(y='price_per_sqft',data=new)

# PERFORMING Zscore METHOD
z=np.abs(stats.zscore(df['price_per_sqft']))
new2=df[(z<3)]

#AFTER REMOVING OUTLIER using Zscore method
sns.boxplot(y="price_per_sqft",data=new2)
```
# height_weight.csv:
```
import pandas as pd
import seaborn as sns
from google.colab import files
uploaded=files.upload()
df=pd.read_csv('height_weight.csv')
df.info()
df.describe()
df.head()

#BEFORE REMOVING OUTLIER in HEIGHT
sns.boxplot(y='height',data=df)
#PERFORMING IQR METHOD ON HEIGHTS
height_q1 = df['height'].quantile(0.25)
height_q3 = df['height'].quantile(0.75)
height_IQR = height_q3 - height_q1
height_low = height_q1 - 1.5 * height_IQR
height_high = height_q3 + 1.5 * height_IQR
height_new=df[((df['height']>=height_low)&(df['height']<=height_high))]
#AFTER REMOVING OUTLIER in HEIGHT
sns.boxplot(y='height',data=height_new)

#BEFORE REMOVING OUTLIER in WEIGHT
sns.boxplot(y='weight',data=df)
#PERFORMING IQR METHOD ON HEIGHTS
weight_q1 = df['weight'].quantile(0.25)
weight_q3 = df['weight'].quantile(0.75)
weight_IQR = weight_q3 - weight_q1
weight_low = weight_q1 - 1.5 * weight_IQR
weight_high = weight_q3 + 1.5 * weight_IQR
weight_new=df[((df['weight']>=weight_low)&(df['weight']<=weight_high))]
#AFTER REMOVING OUTLIER in WEIGHT
sns.boxplot(y='weight',data=weight_new)
```
## OUTPUT:

bhp.csv:

![265059074-c62482aa-13d3-4e93-84f3-14d77e12ff94](https://github.com/roshiniRK/ODD2023---Datascience---Ex-02/assets/118956165/af96da9c-5b57-49fd-9924-78597e1063b9)
![265059121-550161a2-7e49-4873-b9d3-2dee79909859](https://github.com/roshiniRK/ODD2023---Datascience---Ex-02/assets/118956165/f6b30c9d-e9ad-4a5b-9fff-ae887b5ed822)
![265059155-77006c4a-5f65-4c46-b43d-62da3adeae72](https://github.com/roshiniRK/ODD2023---Datascience---Ex-02/assets/118956165/2fb8bfa2-4c80-47c7-a271-fbcb40ff87c5)
![265059167-6ab44ad1-3d24-49ac-8ed8-0a873ee9094c](https://github.com/roshiniRK/ODD2023---Datascience---Ex-02/assets/118956165/8cbb0795-1872-45d7-8000-63caff13ccd6)
![265059222-699f1ddd-dfb7-4d58-abd5-69614106d9d4](https://github.com/roshiniRK/ODD2023---Datascience---Ex-02/assets/118956165/a6123b71-838c-4acf-9547-95d7dc50e4b5)

weight_height.csv:

![265060058-ea846d57-a472-4b28-8d0a-3c405d80f8e0](https://github.com/roshiniRK/ODD2023---Datascience---Ex-02/assets/118956165/a429df05-e108-414b-8739-571575b4dbab)
![265060068-beead9e7-e4bc-4431-a536-bacdb947e6b6](https://github.com/roshiniRK/ODD2023---Datascience---Ex-02/assets/118956165/22d0056a-8f1b-4925-b980-9967cc7ca37a)
![265060084-952f228c-8518-4f91-b966-fda9215eb959](https://github.com/roshiniRK/ODD2023---Datascience---Ex-02/assets/118956165/f431cd0f-6bd1-4abf-8c11-37e0ef3488fa)
![265060101-35fbb5b8-69b9-4592-9685-d81d4cb0f844](https://github.com/roshiniRK/ODD2023---Datascience---Ex-02/assets/118956165/fe11ff59-41a9-41d0-ac36-2a6c2cd2131c)
![265060107-3606e325-b846-412f-b0c2-e56d74b16427](https://github.com/roshiniRK/ODD2023---Datascience---Ex-02/assets/118956165/81b0b21b-3576-4989-8898-bf05d550066e)
![265060126-14b3b742-5bfe-47c2-954b-7ee7315c6848](https://github.com/roshiniRK/ODD2023---Datascience---Ex-02/assets/118956165/1ab2352e-9859-411b-8b36-2f9ae47928fb)

## RESULT:
Hence the given set of data is read and the outliers are removed using the IQR method and Zscore method.









     



