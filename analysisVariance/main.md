


Varianzanalyse im linearen Modell
========================================================
## data given page 666 in Statisik, Sachs
[lm intro](http://data.princeton.edu/R/linearModels.html "Princeton R intro")

```
##  diameter      drug      Conc 
## "numeric"  "factor"  "factor"
```

```
##   diameter drug Conc
## 1     13.2    A high
## 2     14.1    A high
## 3      7.8    A high
## 4     11.7    A high
## 5     15.9    B high
## 6     16.2    B high
```


# linear model

```
## Analysis of Variance Table
## 
## Response: diameter
##           Df Sum Sq Mean Sq F value Pr(>F)   
## drug       2  135.5    67.7    13.1 0.0022 **
## Residuals  9   46.7     5.2                  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

```
## 
## Call:
## lm(formula = diameter ~ drug, data = exp1)
## 
## Residuals:
##    Min     1Q Median     3Q    Max 
##  -3.90  -1.22  -0.02   1.61   2.93 
## 
## Coefficients:
##             Estimate Std. Error t value Pr(>|t|)    
## (Intercept)    11.70       1.14   10.28  2.8e-06 ***
## drugB           5.64       1.53    3.69    0.005 ** 
## drugC          -2.23       1.74   -1.28    0.231    
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 2.28 on 9 degrees of freedom
## Multiple R-squared:  0.744,	Adjusted R-squared:  0.687 
## F-statistic: 13.1 on 2 and 9 DF,  p-value: 0.00218
```

```
## 
## 	 Simultaneous Tests for General Linear Hypotheses
## 
## Fit: lm(formula = diameter ~ drug, data = exp1)
## 
## Linear Hypotheses:
##            Estimate Std. Error t value Pr(>|t|)   
## drugB == 0     5.64       1.53    3.69   0.0092 **
## drugC == 0    -2.23       1.74   -1.28   0.3730   
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## (Adjusted p values reported -- single-step method)
```

```
##              2.5 % 97.5 %
## (Intercept)  9.125 14.275
## drugB        2.185  9.095
## drugC       -6.167  1.701
```

```
## 
## 	 Simultaneous Tests for General Linear Hypotheses
## 
## Fit: lm(formula = diameter ~ drug, data = exp1)
## 
## Linear Hypotheses:
##                  Estimate Std. Error t value Pr(>|t|)    
## (Intercept) == 0    11.70       1.14   10.28   <0.001 ***
## drugB == 0           5.64       1.53    3.69    0.011 *  
## drugC == 0          -2.23       1.74   -1.28    0.434    
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## (Adjusted p values reported -- single-step method)
```

```
##   2 3
## 1 0 0
## 2 1 0
## 3 0 1
```

```
##    (Intercept) drugB drugC
## 1            1     0     0
## 2            1     0     0
## 3            1     0     0
## 4            1     0     0
## 5            1     1     0
## 6            1     1     0
## 7            1     1     0
## 8            1     1     0
## 9            1     1     0
## 10           1     0     1
## 11           1     0     1
## 12           1     0     1
## attr(,"assign")
## [1] 0 1 1
## attr(,"contrasts")
## attr(,"contrasts")$drug
## [1] "contr.treatment"
```

# multiple pairwise comparisons using glht


```
##             Df Sum Sq Mean Sq F value Pr(>F)   
## drug         2  135.5    67.7    13.1 0.0022 **
## Residuals    9   46.7     5.2                  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

![plot of chunk glht](figure/glht.png) 





```
##  diameter      drug      Conc 
## "numeric"  "factor"  "factor"
```

```
##   diameter drug Conc
## 1     10.4    A  low
## 2     12.6    A  low
## 3      6.3    A  low
## 4     11.5    B  low
## 5     13.7    B  low
## 6     10.9    B  low
```


![plot of chunk fm1abc](figure/fm1abc1.png) ![plot of chunk fm1abc](figure/fm1abc2.png) 

# compare models * and :
![plot of chunk fma](figure/fma.png) 

```
## 
## 	 Simultaneous Tests for General Linear Hypotheses
## 
## Multiple Comparisons of Means: Tukey Contrasts
## 
## 
## Fit: lm(formula = diameter ~ drug + Conc + drug:Conc, data = exp12)
## 
## Linear Hypotheses:
##            Estimate Std. Error t value Pr(>|t|)    
## B - A == 0     5.64       1.64    3.44   0.0082 ** 
## C - A == 0    -2.23       1.87   -1.20   0.4700    
## C - B == 0    -7.87       1.78   -4.41   <0.001 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## (Adjusted p values reported -- single-step method)
```

```
## Analysis of Variance Table
## 
## Response: diameter
##           Df Sum Sq Mean Sq F value Pr(>F)   
## drug       2   91.0    45.5    7.62 0.0043 **
## Conc       1    7.6     7.6    1.28 0.2732   
## drug:Conc  2   71.8    35.9    6.01 0.0106 * 
## Residuals 17  101.4     6.0                  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

```
## 
## Call:
## lm(formula = diameter ~ drug + Conc + drug:Conc, data = exp12)
## 
## Residuals:
##    Min     1Q Median     3Q    Max 
##  -3.90  -1.37   0.00   1.73   3.25 
## 
## Coefficients:
##               Estimate Std. Error t value Pr(>|t|)    
## (Intercept)      11.70       1.22    9.58  2.9e-08 ***
## drugB             5.64       1.64    3.44   0.0031 ** 
## drugC            -2.23       1.87   -1.20   0.2477    
## Conclow          -1.93       1.87   -1.04   0.3145    
## drugB:Conclow    -2.61       2.48   -1.05   0.3085    
## drugC:Conclow     5.92       2.64    2.24   0.0385 *  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 2.44 on 17 degrees of freedom
## Multiple R-squared:  0.627,	Adjusted R-squared:  0.517 
## F-statistic: 5.71 on 5 and 17 DF,  p-value: 0.00286
```




![plot of chunk fmb](figure/fmb.png) 

```
## 
## 	 Simultaneous Tests for General Linear Hypotheses
## 
## Multiple Comparisons of Means: Tukey Contrasts
## 
## 
## Fit: lm(formula = diameter ~ drug + drug:Conc, data = exp12)
## 
## Linear Hypotheses:
##            Estimate Std. Error t value Pr(>|t|)    
## B - A == 0     5.64       1.64    3.44   0.0083 ** 
## C - A == 0    -2.23       1.87   -1.20   0.4699    
## C - B == 0    -7.87       1.78   -4.41   <0.001 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## (Adjusted p values reported -- single-step method)
```

```
## Analysis of Variance Table
## 
## Response: diameter
##           Df Sum Sq Mean Sq F value Pr(>F)   
## drug       2   91.0    45.5    7.62 0.0043 **
## drug:Conc  3   79.4    26.5    4.44 0.0177 * 
## Residuals 17  101.4     6.0                  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

```
## 
## Call:
## lm(formula = diameter ~ drug + drug:Conc, data = exp12)
## 
## Residuals:
##    Min     1Q Median     3Q    Max 
##  -3.90  -1.37   0.00   1.73   3.25 
## 
## Coefficients:
##               Estimate Std. Error t value Pr(>|t|)    
## (Intercept)      11.70       1.22    9.58  2.9e-08 ***
## drugB             5.64       1.64    3.44   0.0031 ** 
## drugC            -2.23       1.87   -1.20   0.2477    
## drugA:Conclow    -1.93       1.87   -1.04   0.3145    
## drugB:Conclow    -4.54       1.64   -2.77   0.0131 *  
## drugC:Conclow     3.98       1.87    2.14   0.0476 *  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 2.44 on 17 degrees of freedom
## Multiple R-squared:  0.627,	Adjusted R-squared:  0.517 
## F-statistic: 5.71 on 5 and 17 DF,  p-value: 0.00286
```





![plot of chunk fmc](figure/fmc.png) 

```
## 
## 	 Simultaneous Tests for General Linear Hypotheses
## 
## Multiple Comparisons of Means: Tukey Contrasts
## 
## 
## Fit: lm(formula = diameter ~ drug + Conc + drug:Conc, data = exp12)
## 
## Linear Hypotheses:
##            Estimate Std. Error t value Pr(>|t|)   
## B - A == 0     5.64       1.64    3.44   0.0083 **
## C - A == 0    -2.23       1.87   -1.20   0.4700   
## C - B == 0    -7.87       1.78   -4.41   0.0011 **
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## (Adjusted p values reported -- single-step method)
```

```
## Analysis of Variance Table
## 
## Response: diameter
##           Df Sum Sq Mean Sq F value Pr(>F)   
## drug       2   91.0    45.5    7.62 0.0043 **
## Conc       1    7.6     7.6    1.28 0.2732   
## drug:Conc  2   71.8    35.9    6.01 0.0106 * 
## Residuals 17  101.4     6.0                  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

```
## 
## Call:
## lm(formula = diameter ~ drug + Conc + drug:Conc, data = exp12)
## 
## Residuals:
##    Min     1Q Median     3Q    Max 
##  -3.90  -1.37   0.00   1.73   3.25 
## 
## Coefficients:
##               Estimate Std. Error t value Pr(>|t|)    
## (Intercept)      11.70       1.22    9.58  2.9e-08 ***
## drugB             5.64       1.64    3.44   0.0031 ** 
## drugC            -2.23       1.87   -1.20   0.2477    
## Conclow          -1.93       1.87   -1.04   0.3145    
## drugB:Conclow    -2.61       2.48   -1.05   0.3085    
## drugC:Conclow     5.92       2.64    2.24   0.0385 *  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 2.44 on 17 degrees of freedom
## Multiple R-squared:  0.627,	Adjusted R-squared:  0.517 
## F-statistic: 5.71 on 5 and 17 DF,  p-value: 0.00286
```











- AH=AH
- BH=AH+BHmAH
- CH=AH+CHmAH
- AL=AH+ALmAH
- BL=AH+BHmAH+ALmAH+BLmBHmALmAH
- CL=AH+CHmAH+ALmAH+CLmCHmALmAH)

BL-BH-(AL-AH)= BL-BH-AL+AH=(BL-AL)-(BH-AH)

A=log(Ref)
B=log(Gene)
(BL-AL)-(BH-AH) = log(Gene/Ref)L - log(Gene/Ref)H =log((Gene/Ref)L /(Gene/Ref)H)

fold increase of Gene/Ref by changing from H to L


- AH=AH
- BH=AH+BHmAH
- CH=AH+CHmAH
- AL=AH+ALmAH
- BL=BH+BLmBH= AH+BHmAH +BLmBH = AH+BH-AH + BL-BH
- CL=AH+CHmAH+ALmAH+CLmCHmALmAH)

c0[4]=AL-AH = log(RefL/RefH)
c0[5]=BL-BH = BL-BH + AH -AH = (BL-AH)-(BH-AH)= log((GeneL/RefH) /(Gene/Ref)H)
c0[6]=CL-CH

fold increase of Gene  by changing from H to L

Gene 



# Conclusion

- the difference between diameter A high Conc vs  diameter A low Conc is -1.9333
- the difference between diameter B high Conc vs  diameter B low Conc is -4.54  
 - drug B adds a difference of -2.6067 to the A difference -1.9333
- the difference between diameter C high Conc vs  diameter C low Conc is 3.9833
 - drug C adds a difference of 5.9167 to the A difference -1.9333


