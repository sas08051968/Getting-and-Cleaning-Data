---
output: html_document
---
# CodeBook

### Author: Salvatore Lenza 
##### (https://github.com/sas08051968/Getting-and-Cleaning-Data)
##### Saturday, July 25, 2015




## Data Set Information:

The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data. 

The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain.

## Dataset structure




```r
str(tidy_data)
```

```
## 'data.frame':	180 obs. of  81 variables:
##  $ subject                        : int  1 1 1 1 1 1 2 2 2 2 ...
##  $ Activity_Label                 : Factor w/ 6 levels "LAYING","SITTING",..: 1 2 3 4 5 6 1 2 3 4 ...
##  $ tBodyAcc-mean()-X              : num  0.222 0.261 0.279 0.277 0.289 ...
##  $ tBodyAcc-mean()-Y              : num  -0.04051 -0.00131 -0.01614 -0.01738 -0.00992 ...
##  $ tBodyAcc-mean()-Z              : num  -0.113 -0.105 -0.111 -0.111 -0.108 ...
##  $ tBodyAcc-std()-X               : num  -0.928 -0.977 -0.996 -0.284 0.03 ...
##  $ tBodyAcc-std()-Y               : num  -0.8368 -0.9226 -0.9732 0.1145 -0.0319 ...
##  $ tBodyAcc-std()-Z               : num  -0.826 -0.94 -0.98 -0.26 -0.23 ...
##  $ tGravityAcc-mean()-X           : num  -0.249 0.832 0.943 0.935 0.932 ...
##  $ tGravityAcc-mean()-Y           : num  0.706 0.204 -0.273 -0.282 -0.267 ...
##  $ tGravityAcc-mean()-Z           : num  0.4458 0.332 0.0135 -0.0681 -0.0621 ...
##  $ tGravityAcc-std()-X            : num  -0.897 -0.968 -0.994 -0.977 -0.951 ...
##  $ tGravityAcc-std()-Y            : num  -0.908 -0.936 -0.981 -0.971 -0.937 ...
##  $ tGravityAcc-std()-Z            : num  -0.852 -0.949 -0.976 -0.948 -0.896 ...
##  $ tBodyAccJerk-mean()-X          : num  0.0811 0.0775 0.0754 0.074 0.0542 ...
##  $ tBodyAccJerk-mean()-Y          : num  0.003838 -0.000619 0.007976 0.028272 0.02965 ...
##  $ tBodyAccJerk-mean()-Z          : num  0.01083 -0.00337 -0.00369 -0.00417 -0.01097 ...
##  $ tBodyAccJerk-std()-X           : num  -0.9585 -0.9864 -0.9946 -0.1136 -0.0123 ...
##  $ tBodyAccJerk-std()-Y           : num  -0.924 -0.981 -0.986 0.067 -0.102 ...
##  $ tBodyAccJerk-std()-Z           : num  -0.955 -0.988 -0.992 -0.503 -0.346 ...
##  $ tBodyGyro-mean()-X             : num  -0.0166 -0.0454 -0.024 -0.0418 -0.0351 ...
##  $ tBodyGyro-mean()-Y             : num  -0.0645 -0.0919 -0.0594 -0.0695 -0.0909 ...
##  $ tBodyGyro-mean()-Z             : num  0.1487 0.0629 0.0748 0.0849 0.0901 ...
##  $ tBodyGyro-std()-X              : num  -0.874 -0.977 -0.987 -0.474 -0.458 ...
##  $ tBodyGyro-std()-Y              : num  -0.9511 -0.9665 -0.9877 -0.0546 -0.1263 ...
##  $ tBodyGyro-std()-Z              : num  -0.908 -0.941 -0.981 -0.344 -0.125 ...
##  $ tBodyGyroJerk-mean()-X         : num  -0.1073 -0.0937 -0.0996 -0.09 -0.074 ...
##  $ tBodyGyroJerk-mean()-Y         : num  -0.0415 -0.0402 -0.0441 -0.0398 -0.044 ...
##  $ tBodyGyroJerk-mean()-Z         : num  -0.0741 -0.0467 -0.049 -0.0461 -0.027 ...
##  $ tBodyGyroJerk-std()-X          : num  -0.919 -0.992 -0.993 -0.207 -0.487 ...
##  $ tBodyGyroJerk-std()-Y          : num  -0.968 -0.99 -0.995 -0.304 -0.239 ...
##  $ tBodyGyroJerk-std()-Z          : num  -0.958 -0.988 -0.992 -0.404 -0.269 ...
##  $ tBodyAccMag-mean()             : num  -0.8419 -0.9485 -0.9843 -0.137 0.0272 ...
##  $ tBodyAccMag-std()              : num  -0.7951 -0.9271 -0.9819 -0.2197 0.0199 ...
##  $ tGravityAccMag-mean()          : num  -0.8419 -0.9485 -0.9843 -0.137 0.0272 ...
##  $ tGravityAccMag-std()           : num  -0.7951 -0.9271 -0.9819 -0.2197 0.0199 ...
##  $ tBodyAccJerkMag-mean()         : num  -0.9544 -0.9874 -0.9924 -0.1414 -0.0894 ...
##  $ tBodyAccJerkMag-std()          : num  -0.9282 -0.9841 -0.9931 -0.0745 -0.0258 ...
##  $ tBodyGyroMag-mean()            : num  -0.8748 -0.9309 -0.9765 -0.161 -0.0757 ...
##  $ tBodyGyroMag-std()             : num  -0.819 -0.935 -0.979 -0.187 -0.226 ...
##  $ tBodyGyroJerkMag-mean()        : num  -0.963 -0.992 -0.995 -0.299 -0.295 ...
##  $ tBodyGyroJerkMag-std()         : num  -0.936 -0.988 -0.995 -0.325 -0.307 ...
##  $ fBodyAcc-mean()-X              : num  -0.9391 -0.9796 -0.9952 -0.2028 0.0382 ...
##  $ fBodyAcc-mean()-Y              : num  -0.86707 -0.94408 -0.97707 0.08971 0.00155 ...
##  $ fBodyAcc-mean()-Z              : num  -0.883 -0.959 -0.985 -0.332 -0.226 ...
##  $ fBodyAcc-std()-X               : num  -0.9244 -0.9764 -0.996 -0.3191 0.0243 ...
##  $ fBodyAcc-std()-Y               : num  -0.834 -0.917 -0.972 0.056 -0.113 ...
##  $ fBodyAcc-std()-Z               : num  -0.813 -0.934 -0.978 -0.28 -0.298 ...
##  $ fBodyAcc-meanFreq()-X          : num  -0.1588 -0.0495 0.0865 -0.2075 -0.3074 ...
##  $ fBodyAcc-meanFreq()-Y          : num  0.0975 0.0759 0.1175 0.1131 0.0632 ...
##  $ fBodyAcc-meanFreq()-Z          : num  0.0894 0.2388 0.2449 0.0497 0.2943 ...
##  $ fBodyAccJerk-mean()-X          : num  -0.9571 -0.9866 -0.9946 -0.1705 -0.0277 ...
##  $ fBodyAccJerk-mean()-Y          : num  -0.9225 -0.9816 -0.9854 -0.0352 -0.1287 ...
##  $ fBodyAccJerk-mean()-Z          : num  -0.948 -0.986 -0.991 -0.469 -0.288 ...
##  $ fBodyAccJerk-std()-X           : num  -0.9642 -0.9875 -0.9951 -0.1336 -0.0863 ...
##  $ fBodyAccJerk-std()-Y           : num  -0.932 -0.983 -0.987 0.107 -0.135 ...
##  $ fBodyAccJerk-std()-Z           : num  -0.961 -0.988 -0.992 -0.535 -0.402 ...
##  $ fBodyAccJerk-meanFreq()-X      : num  0.132 0.257 0.314 -0.209 -0.253 ...
##  $ fBodyAccJerk-meanFreq()-Y      : num  0.0245 0.0475 0.0392 -0.3862 -0.3376 ...
##  $ fBodyAccJerk-meanFreq()-Z      : num  0.02439 0.09239 0.13858 -0.18553 0.00937 ...
##  $ fBodyGyro-mean()-X             : num  -0.85 -0.976 -0.986 -0.339 -0.352 ...
##  $ fBodyGyro-mean()-Y             : num  -0.9522 -0.9758 -0.989 -0.1031 -0.0557 ...
##  $ fBodyGyro-mean()-Z             : num  -0.9093 -0.9513 -0.9808 -0.2559 -0.0319 ...
##  $ fBodyGyro-std()-X              : num  -0.882 -0.978 -0.987 -0.517 -0.495 ...
##  $ fBodyGyro-std()-Y              : num  -0.9512 -0.9623 -0.9871 -0.0335 -0.1814 ...
##  $ fBodyGyro-std()-Z              : num  -0.917 -0.944 -0.982 -0.437 -0.238 ...
##  $ fBodyGyro-meanFreq()-X         : num  -0.00355 0.18915 -0.12029 0.01478 -0.10045 ...
##  $ fBodyGyro-meanFreq()-Y         : num  -0.0915 0.0631 -0.0447 -0.0658 0.0826 ...
##  $ fBodyGyro-meanFreq()-Z         : num  0.010458 -0.029784 0.100608 0.000773 -0.075676 ...
##  $ fBodyAccMag-mean()             : num  -0.8618 -0.9478 -0.9854 -0.1286 0.0966 ...
##  $ fBodyAccMag-std()              : num  -0.798 -0.928 -0.982 -0.398 -0.187 ...
##  $ fBodyAccMag-meanFreq()         : num  0.0864 0.2367 0.2846 0.1906 0.1192 ...
##  $ fBodyBodyAccJerkMag-mean()     : num  -0.9333 -0.9853 -0.9925 -0.0571 0.0262 ...
##  $ fBodyBodyAccJerkMag-std()      : num  -0.922 -0.982 -0.993 -0.103 -0.104 ...
##  $ fBodyBodyAccJerkMag-meanFreq() : num  0.2664 0.3519 0.4222 0.0938 0.0765 ...
##  $ fBodyBodyGyroMag-mean()        : num  -0.862 -0.958 -0.985 -0.199 -0.186 ...
##  $ fBodyBodyGyroMag-std()         : num  -0.824 -0.932 -0.978 -0.321 -0.398 ...
##  $ fBodyBodyGyroMag-meanFreq()    : num  -0.139775 -0.000262 -0.028606 0.268844 0.349614 ...
##  $ fBodyBodyGyroJerkMag-mean()    : num  -0.942 -0.99 -0.995 -0.319 -0.282 ...
##  $ fBodyBodyGyroJerkMag-std()     : num  -0.933 -0.987 -0.995 -0.382 -0.392 ...
##  $ fBodyBodyGyroJerkMag-meanFreq(): num  0.176 0.185 0.334 0.191 0.19 ...
```

## Attribute Information:

For each record in the dataset it is provided: 
* Triaxial acceleration from the accelerometer (total acceleration) and the estimated body acceleration. 
*Triaxial Angular velocity from the gyroscope. 
* A 561-feature vector with time and frequency domain variables. 
* Its activity label. 
* An identifier of the subject who carried out the experiment.


## head of the dataset


```r
head(tidy_data, n=2L)
```

```
##   subject Activity_Label tBodyAcc-mean()-X tBodyAcc-mean()-Y
## 1       1         LAYING         0.2215982      -0.040513953
## 2       1        SITTING         0.2612376      -0.001308288
##   tBodyAcc-mean()-Z tBodyAcc-std()-X tBodyAcc-std()-Y tBodyAcc-std()-Z
## 1        -0.1132036       -0.9280565       -0.8368274       -0.8260614
## 2        -0.1045442       -0.9772290       -0.9226186       -0.9395863
##   tGravityAcc-mean()-X tGravityAcc-mean()-Y tGravityAcc-mean()-Z
## 1           -0.2488818            0.7055498            0.4458177
## 2            0.8315099            0.2044116            0.3320437
##   tGravityAcc-std()-X tGravityAcc-std()-Y tGravityAcc-std()-Z
## 1          -0.8968300          -0.9077200          -0.8523663
## 2          -0.9684571          -0.9355171          -0.9490409
##   tBodyAccJerk-mean()-X tBodyAccJerk-mean()-Y tBodyAccJerk-mean()-Z
## 1            0.08108653          0.0038382040           0.010834236
## 2            0.07748252         -0.0006191028          -0.003367792
##   tBodyAccJerk-std()-X tBodyAccJerk-std()-Y tBodyAccJerk-std()-Z
## 1           -0.9584821           -0.9241493           -0.9548551
## 2           -0.9864307           -0.9813720           -0.9879108
##   tBodyGyro-mean()-X tBodyGyro-mean()-Y tBodyGyro-mean()-Z
## 1        -0.01655309        -0.06448612         0.14868944
## 2        -0.04535006        -0.09192415         0.06293138
##   tBodyGyro-std()-X tBodyGyro-std()-Y tBodyGyro-std()-Z
## 1        -0.8735439        -0.9510904        -0.9082847
## 2        -0.9772113        -0.9664739        -0.9414259
##   tBodyGyroJerk-mean()-X tBodyGyroJerk-mean()-Y tBodyGyroJerk-mean()-Z
## 1            -0.10727095            -0.04151729            -0.07405012
## 2            -0.09367938            -0.04021181            -0.04670263
##   tBodyGyroJerk-std()-X tBodyGyroJerk-std()-Y tBodyGyroJerk-std()-Z
## 1            -0.9186085            -0.9679072            -0.9577902
## 2            -0.9917316            -0.9895181            -0.9879358
##   tBodyAccMag-mean() tBodyAccMag-std() tGravityAccMag-mean()
## 1         -0.8419292        -0.7951449            -0.8419292
## 2         -0.9485368        -0.9270784            -0.9485368
##   tGravityAccMag-std() tBodyAccJerkMag-mean() tBodyAccJerkMag-std()
## 1           -0.7951449             -0.9543963            -0.9282456
## 2           -0.9270784             -0.9873642            -0.9841200
##   tBodyGyroMag-mean() tBodyGyroMag-std() tBodyGyroJerkMag-mean()
## 1          -0.8747595         -0.8190102              -0.9634610
## 2          -0.9308925         -0.9345318              -0.9919763
##   tBodyGyroJerkMag-std() fBodyAcc-mean()-X fBodyAcc-mean()-Y
## 1             -0.9358410        -0.9390991        -0.8670652
## 2             -0.9883087        -0.9796412        -0.9440846
##   fBodyAcc-mean()-Z fBodyAcc-std()-X fBodyAcc-std()-Y fBodyAcc-std()-Z
## 1        -0.8826669       -0.9244374       -0.8336256       -0.8128916
## 2        -0.9591849       -0.9764123       -0.9172750       -0.9344696
##   fBodyAcc-meanFreq()-X fBodyAcc-meanFreq()-Y fBodyAcc-meanFreq()-Z
## 1            -0.1587927            0.09753484            0.08943766
## 2            -0.0495136            0.07594608            0.23882987
##   fBodyAccJerk-mean()-X fBodyAccJerk-mean()-Y fBodyAccJerk-mean()-Z
## 1            -0.9570739            -0.9224626            -0.9480609
## 2            -0.9865970            -0.9815795            -0.9860531
##   fBodyAccJerk-std()-X fBodyAccJerk-std()-Y fBodyAccJerk-std()-Z
## 1           -0.9641607           -0.9322179           -0.9605870
## 2           -0.9874930           -0.9825139           -0.9883392
##   fBodyAccJerk-meanFreq()-X fBodyAccJerk-meanFreq()-Y
## 1                 0.1324191                0.02451362
## 2                 0.2566108                0.04754378
##   fBodyAccJerk-meanFreq()-Z fBodyGyro-mean()-X fBodyGyro-mean()-Y
## 1                0.02438795         -0.8502492         -0.9521915
## 2                0.09239200         -0.9761615         -0.9758386
##   fBodyGyro-mean()-Z fBodyGyro-std()-X fBodyGyro-std()-Y fBodyGyro-std()-Z
## 1         -0.9093027        -0.8822965         -0.951232        -0.9165825
## 2         -0.9513155        -0.9779042         -0.962345        -0.9439178
##   fBodyGyro-meanFreq()-X fBodyGyro-meanFreq()-Y fBodyGyro-meanFreq()-Z
## 1           -0.003546796            -0.09152913             0.01045813
## 2            0.189153021             0.06312707            -0.02978392
##   fBodyAccMag-mean() fBodyAccMag-std() fBodyAccMag-meanFreq()
## 1         -0.8617676        -0.7983009             0.08640856
## 2         -0.9477829        -0.9284448             0.23665501
##   fBodyBodyAccJerkMag-mean() fBodyBodyAccJerkMag-std()
## 1                 -0.9333004                -0.9218040
## 2                 -0.9852621                -0.9816062
##   fBodyBodyAccJerkMag-meanFreq() fBodyBodyGyroMag-mean()
## 1                      0.2663912              -0.8621902
## 2                      0.3518522              -0.9584356
##   fBodyBodyGyroMag-std() fBodyBodyGyroMag-meanFreq()
## 1             -0.8243194               -0.1397750127
## 2             -0.9321984               -0.0002621867
##   fBodyBodyGyroJerkMag-mean() fBodyBodyGyroJerkMag-std()
## 1                  -0.9423669                 -0.9326607
## 2                  -0.9897975                 -0.9870496
##   fBodyBodyGyroJerkMag-meanFreq()
## 1                       0.1764859
## 2                       0.1847759
```


## Summary of variables


```r
summary(tidy_data)
```

```
##     subject                Activity_Label tBodyAcc-mean()-X
##  Min.   : 1.0   LAYING            :30     Min.   :0.2216   
##  1st Qu.: 8.0   SITTING           :30     1st Qu.:0.2712   
##  Median :15.5   STANDING          :30     Median :0.2770   
##  Mean   :15.5   WALKING           :30     Mean   :0.2743   
##  3rd Qu.:23.0   WALKING_DOWNSTAIRS:30     3rd Qu.:0.2800   
##  Max.   :30.0   WALKING_UPSTAIRS  :30     Max.   :0.3015   
##  tBodyAcc-mean()-Y   tBodyAcc-mean()-Z  tBodyAcc-std()-X 
##  Min.   :-0.040514   Min.   :-0.15251   Min.   :-0.9961  
##  1st Qu.:-0.020022   1st Qu.:-0.11207   1st Qu.:-0.9799  
##  Median :-0.017262   Median :-0.10819   Median :-0.7526  
##  Mean   :-0.017876   Mean   :-0.10916   Mean   :-0.5577  
##  3rd Qu.:-0.014936   3rd Qu.:-0.10443   3rd Qu.:-0.1984  
##  Max.   :-0.001308   Max.   :-0.07538   Max.   : 0.6269  
##  tBodyAcc-std()-Y   tBodyAcc-std()-Z  tGravityAcc-mean()-X
##  Min.   :-0.99024   Min.   :-0.9877   Min.   :-0.6800     
##  1st Qu.:-0.94205   1st Qu.:-0.9498   1st Qu.: 0.8376     
##  Median :-0.50897   Median :-0.6518   Median : 0.9208     
##  Mean   :-0.46046   Mean   :-0.5756   Mean   : 0.6975     
##  3rd Qu.:-0.03077   3rd Qu.:-0.2306   3rd Qu.: 0.9425     
##  Max.   : 0.61694   Max.   : 0.6090   Max.   : 0.9745     
##  tGravityAcc-mean()-Y tGravityAcc-mean()-Z tGravityAcc-std()-X
##  Min.   :-0.47989     Min.   :-0.49509     Min.   :-0.9968    
##  1st Qu.:-0.23319     1st Qu.:-0.11726     1st Qu.:-0.9825    
##  Median :-0.12782     Median : 0.02384     Median :-0.9695    
##  Mean   :-0.01621     Mean   : 0.07413     Mean   :-0.9638    
##  3rd Qu.: 0.08773     3rd Qu.: 0.14946     3rd Qu.:-0.9509    
##  Max.   : 0.95659     Max.   : 0.95787     Max.   :-0.8296    
##  tGravityAcc-std()-Y tGravityAcc-std()-Z tBodyAccJerk-mean()-X
##  Min.   :-0.9942     Min.   :-0.9910     Min.   :0.04269      
##  1st Qu.:-0.9711     1st Qu.:-0.9605     1st Qu.:0.07396      
##  Median :-0.9590     Median :-0.9450     Median :0.07640      
##  Mean   :-0.9524     Mean   :-0.9364     Mean   :0.07947      
##  3rd Qu.:-0.9370     3rd Qu.:-0.9180     3rd Qu.:0.08330      
##  Max.   :-0.6436     Max.   :-0.6102     Max.   :0.13019      
##  tBodyAccJerk-mean()-Y tBodyAccJerk-mean()-Z tBodyAccJerk-std()-X
##  Min.   :-0.0386872    Min.   :-0.067458     Min.   :-0.9946     
##  1st Qu.: 0.0004664    1st Qu.:-0.010601     1st Qu.:-0.9832     
##  Median : 0.0094698    Median :-0.003861     Median :-0.8104     
##  Mean   : 0.0075652    Mean   :-0.004953     Mean   :-0.5949     
##  3rd Qu.: 0.0134008    3rd Qu.: 0.001958     3rd Qu.:-0.2233     
##  Max.   : 0.0568186    Max.   : 0.038053     Max.   : 0.5443     
##  tBodyAccJerk-std()-Y tBodyAccJerk-std()-Z tBodyGyro-mean()-X
##  Min.   :-0.9895      Min.   :-0.99329     Min.   :-0.20578  
##  1st Qu.:-0.9724      1st Qu.:-0.98266     1st Qu.:-0.04712  
##  Median :-0.7756      Median :-0.88366     Median :-0.02871  
##  Mean   :-0.5654      Mean   :-0.73596     Mean   :-0.03244  
##  3rd Qu.:-0.1483      3rd Qu.:-0.51212     3rd Qu.:-0.01676  
##  Max.   : 0.3553      Max.   : 0.03102     Max.   : 0.19270  
##  tBodyGyro-mean()-Y tBodyGyro-mean()-Z tBodyGyro-std()-X tBodyGyro-std()-Y
##  Min.   :-0.20421   Min.   :-0.07245   Min.   :-0.9943   Min.   :-0.9942  
##  1st Qu.:-0.08955   1st Qu.: 0.07475   1st Qu.:-0.9735   1st Qu.:-0.9629  
##  Median :-0.07318   Median : 0.08512   Median :-0.7890   Median :-0.8017  
##  Mean   :-0.07426   Mean   : 0.08744   Mean   :-0.6916   Mean   :-0.6533  
##  3rd Qu.:-0.06113   3rd Qu.: 0.10177   3rd Qu.:-0.4414   3rd Qu.:-0.4196  
##  Max.   : 0.02747   Max.   : 0.17910   Max.   : 0.2677   Max.   : 0.4765  
##  tBodyGyro-std()-Z tBodyGyroJerk-mean()-X tBodyGyroJerk-mean()-Y
##  Min.   :-0.9855   Min.   :-0.15721       Min.   :-0.07681      
##  1st Qu.:-0.9609   1st Qu.:-0.10322       1st Qu.:-0.04552      
##  Median :-0.8010   Median :-0.09868       Median :-0.04112      
##  Mean   :-0.6164   Mean   :-0.09606       Mean   :-0.04269      
##  3rd Qu.:-0.3106   3rd Qu.:-0.09110       3rd Qu.:-0.03842      
##  Max.   : 0.5649   Max.   :-0.02209       Max.   :-0.01320      
##  tBodyGyroJerk-mean()-Z tBodyGyroJerk-std()-X tBodyGyroJerk-std()-Y
##  Min.   :-0.092500      Min.   :-0.9965       Min.   :-0.9971      
##  1st Qu.:-0.061725      1st Qu.:-0.9800       1st Qu.:-0.9832      
##  Median :-0.053430      Median :-0.8396       Median :-0.8942      
##  Mean   :-0.054802      Mean   :-0.7036       Mean   :-0.7636      
##  3rd Qu.:-0.048985      3rd Qu.:-0.4629       3rd Qu.:-0.5861      
##  Max.   :-0.006941      Max.   : 0.1791       Max.   : 0.2959      
##  tBodyGyroJerk-std()-Z tBodyAccMag-mean() tBodyAccMag-std()
##  Min.   :-0.9954       Min.   :-0.9865    Min.   :-0.9865  
##  1st Qu.:-0.9848       1st Qu.:-0.9573    1st Qu.:-0.9430  
##  Median :-0.8610       Median :-0.4829    Median :-0.6074  
##  Mean   :-0.7096       Mean   :-0.4973    Mean   :-0.5439  
##  3rd Qu.:-0.4741       3rd Qu.:-0.0919    3rd Qu.:-0.2090  
##  Max.   : 0.1932       Max.   : 0.6446    Max.   : 0.4284  
##  tGravityAccMag-mean() tGravityAccMag-std() tBodyAccJerkMag-mean()
##  Min.   :-0.9865       Min.   :-0.9865      Min.   :-0.9928       
##  1st Qu.:-0.9573       1st Qu.:-0.9430      1st Qu.:-0.9807       
##  Median :-0.4829       Median :-0.6074      Median :-0.8168       
##  Mean   :-0.4973       Mean   :-0.5439      Mean   :-0.6079       
##  3rd Qu.:-0.0919       3rd Qu.:-0.2090      3rd Qu.:-0.2456       
##  Max.   : 0.6446       Max.   : 0.4284      Max.   : 0.4345       
##  tBodyAccJerkMag-std() tBodyGyroMag-mean() tBodyGyroMag-std()
##  Min.   :-0.9946       Min.   :-0.9807     Min.   :-0.9814   
##  1st Qu.:-0.9765       1st Qu.:-0.9461     1st Qu.:-0.9476   
##  Median :-0.8014       Median :-0.6551     Median :-0.7420   
##  Mean   :-0.5842       Mean   :-0.5652     Mean   :-0.6304   
##  3rd Qu.:-0.2173       3rd Qu.:-0.2159     3rd Qu.:-0.3602   
##  Max.   : 0.4506       Max.   : 0.4180     Max.   : 0.3000   
##  tBodyGyroJerkMag-mean() tBodyGyroJerkMag-std() fBodyAcc-mean()-X
##  Min.   :-0.99732        Min.   :-0.9977        Min.   :-0.9952  
##  1st Qu.:-0.98515        1st Qu.:-0.9805        1st Qu.:-0.9787  
##  Median :-0.86479        Median :-0.8809        Median :-0.7691  
##  Mean   :-0.73637        Mean   :-0.7550        Mean   :-0.5758  
##  3rd Qu.:-0.51186        3rd Qu.:-0.5767        3rd Qu.:-0.2174  
##  Max.   : 0.08758        Max.   : 0.2502        Max.   : 0.5370  
##  fBodyAcc-mean()-Y  fBodyAcc-mean()-Z fBodyAcc-std()-X  fBodyAcc-std()-Y  
##  Min.   :-0.98903   Min.   :-0.9895   Min.   :-0.9966   Min.   :-0.99068  
##  1st Qu.:-0.95361   1st Qu.:-0.9619   1st Qu.:-0.9820   1st Qu.:-0.94042  
##  Median :-0.59498   Median :-0.7236   Median :-0.7470   Median :-0.51338  
##  Mean   :-0.48873   Mean   :-0.6297   Mean   :-0.5522   Mean   :-0.48148  
##  3rd Qu.:-0.06341   3rd Qu.:-0.3183   3rd Qu.:-0.1966   3rd Qu.:-0.07913  
##  Max.   : 0.52419   Max.   : 0.2807   Max.   : 0.6585   Max.   : 0.56019  
##  fBodyAcc-std()-Z  fBodyAcc-meanFreq()-X fBodyAcc-meanFreq()-Y
##  Min.   :-0.9872   Min.   :-0.63591      Min.   :-0.379518    
##  1st Qu.:-0.9459   1st Qu.:-0.39165      1st Qu.:-0.081314    
##  Median :-0.6441   Median :-0.25731      Median : 0.007855    
##  Mean   :-0.5824   Mean   :-0.23227      Mean   : 0.011529    
##  3rd Qu.:-0.2655   3rd Qu.:-0.06105      3rd Qu.: 0.086281    
##  Max.   : 0.6871   Max.   : 0.15912      Max.   : 0.466528    
##  fBodyAcc-meanFreq()-Z fBodyAccJerk-mean()-X fBodyAccJerk-mean()-Y
##  Min.   :-0.52011      Min.   :-0.9946       Min.   :-0.9894      
##  1st Qu.:-0.03629      1st Qu.:-0.9828       1st Qu.:-0.9725      
##  Median : 0.06582      Median :-0.8126       Median :-0.7817      
##  Mean   : 0.04372      Mean   :-0.6139       Mean   :-0.5882      
##  3rd Qu.: 0.17542      3rd Qu.:-0.2820       3rd Qu.:-0.1963      
##  Max.   : 0.40253      Max.   : 0.4743       Max.   : 0.2767      
##  fBodyAccJerk-mean()-Z fBodyAccJerk-std()-X fBodyAccJerk-std()-Y
##  Min.   :-0.9920       Min.   :-0.9951      Min.   :-0.9905     
##  1st Qu.:-0.9796       1st Qu.:-0.9847      1st Qu.:-0.9737     
##  Median :-0.8707       Median :-0.8254      Median :-0.7852     
##  Mean   :-0.7144       Mean   :-0.6121      Mean   :-0.5707     
##  3rd Qu.:-0.4697       3rd Qu.:-0.2475      3rd Qu.:-0.1685     
##  Max.   : 0.1578       Max.   : 0.4768      Max.   : 0.3498     
##  fBodyAccJerk-std()-Z fBodyAccJerk-meanFreq()-X fBodyAccJerk-meanFreq()-Y
##  Min.   :-0.993108    Min.   :-0.57604          Min.   :-0.60197         
##  1st Qu.:-0.983747    1st Qu.:-0.28966          1st Qu.:-0.39751         
##  Median :-0.895121    Median :-0.06091          Median :-0.23209         
##  Mean   :-0.756489    Mean   :-0.06910          Mean   :-0.22810         
##  3rd Qu.:-0.543787    3rd Qu.: 0.17660          3rd Qu.:-0.04721         
##  Max.   :-0.006236    Max.   : 0.33145          Max.   : 0.19568         
##  fBodyAccJerk-meanFreq()-Z fBodyGyro-mean()-X fBodyGyro-mean()-Y
##  Min.   :-0.62756          Min.   :-0.9931    Min.   :-0.9940   
##  1st Qu.:-0.30867          1st Qu.:-0.9697    1st Qu.:-0.9700   
##  Median :-0.09187          Median :-0.7300    Median :-0.8141   
##  Mean   :-0.13760          Mean   :-0.6367    Mean   :-0.6767   
##  3rd Qu.: 0.03858          3rd Qu.:-0.3387    3rd Qu.:-0.4458   
##  Max.   : 0.23011          Max.   : 0.4750    Max.   : 0.3288   
##  fBodyGyro-mean()-Z fBodyGyro-std()-X fBodyGyro-std()-Y fBodyGyro-std()-Z
##  Min.   :-0.9860    Min.   :-0.9947   Min.   :-0.9944   Min.   :-0.9867  
##  1st Qu.:-0.9624    1st Qu.:-0.9750   1st Qu.:-0.9602   1st Qu.:-0.9643  
##  Median :-0.7909    Median :-0.8086   Median :-0.7964   Median :-0.8224  
##  Mean   :-0.6044    Mean   :-0.7110   Mean   :-0.6454   Mean   :-0.6577  
##  3rd Qu.:-0.2635    3rd Qu.:-0.4813   3rd Qu.:-0.4154   3rd Qu.:-0.3916  
##  Max.   : 0.4924    Max.   : 0.1966   Max.   : 0.6462   Max.   : 0.5225  
##  fBodyGyro-meanFreq()-X fBodyGyro-meanFreq()-Y fBodyGyro-meanFreq()-Z
##  Min.   :-0.395770      Min.   :-0.66681       Min.   :-0.50749      
##  1st Qu.:-0.213363      1st Qu.:-0.29433       1st Qu.:-0.15481      
##  Median :-0.115527      Median :-0.15794       Median :-0.05081      
##  Mean   :-0.104551      Mean   :-0.16741       Mean   :-0.05718      
##  3rd Qu.: 0.002655      3rd Qu.:-0.04269       3rd Qu.: 0.04152      
##  Max.   : 0.249209      Max.   : 0.27314       Max.   : 0.37707      
##  fBodyAccMag-mean() fBodyAccMag-std() fBodyAccMag-meanFreq()
##  Min.   :-0.9868    Min.   :-0.9876   Min.   :-0.31234      
##  1st Qu.:-0.9560    1st Qu.:-0.9452   1st Qu.:-0.01475      
##  Median :-0.6703    Median :-0.6513   Median : 0.08132      
##  Mean   :-0.5365    Mean   :-0.6210   Mean   : 0.07613      
##  3rd Qu.:-0.1622    3rd Qu.:-0.3654   3rd Qu.: 0.17436      
##  Max.   : 0.5866    Max.   : 0.1787   Max.   : 0.43585      
##  fBodyBodyAccJerkMag-mean() fBodyBodyAccJerkMag-std()
##  Min.   :-0.9940            Min.   :-0.9944          
##  1st Qu.:-0.9770            1st Qu.:-0.9752          
##  Median :-0.7940            Median :-0.8126          
##  Mean   :-0.5756            Mean   :-0.5992          
##  3rd Qu.:-0.1872            3rd Qu.:-0.2668          
##  Max.   : 0.5384            Max.   : 0.3163          
##  fBodyBodyAccJerkMag-meanFreq() fBodyBodyGyroMag-mean()
##  Min.   :-0.12521               Min.   :-0.9865        
##  1st Qu.: 0.04527               1st Qu.:-0.9616        
##  Median : 0.17198               Median :-0.7657        
##  Mean   : 0.16255               Mean   :-0.6671        
##  3rd Qu.: 0.27593               3rd Qu.:-0.4087        
##  Max.   : 0.48809               Max.   : 0.2040        
##  fBodyBodyGyroMag-std() fBodyBodyGyroMag-meanFreq()
##  Min.   :-0.9815        Min.   :-0.45664           
##  1st Qu.:-0.9488        1st Qu.:-0.16951           
##  Median :-0.7727        Median :-0.05352           
##  Mean   :-0.6723        Mean   :-0.03603           
##  3rd Qu.:-0.4277        3rd Qu.: 0.08228           
##  Max.   : 0.2367        Max.   : 0.40952           
##  fBodyBodyGyroJerkMag-mean() fBodyBodyGyroJerkMag-std()
##  Min.   :-0.9976             Min.   :-0.9976           
##  1st Qu.:-0.9813             1st Qu.:-0.9802           
##  Median :-0.8779             Median :-0.8941           
##  Mean   :-0.7564             Mean   :-0.7715           
##  3rd Qu.:-0.5831             3rd Qu.:-0.6081           
##  Max.   : 0.1466             Max.   : 0.2878           
##  fBodyBodyGyroJerkMag-meanFreq()
##  Min.   :-0.18292               
##  1st Qu.: 0.05423               
##  Median : 0.11156               
##  Mean   : 0.12592               
##  3rd Qu.: 0.20805               
##  Max.   : 0.42630
```
