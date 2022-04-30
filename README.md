# MatPlotLib-Challenge: The Power of Plots
Using MatPlotLib and Pandas, a study of 249 mice undergoing 45 days of squamous cell carcinoma treatment was analyzed. The performance of the drug Capomulin was compared to that of the other drug regimens.

## Data Preparation and Analyses
### Data Preparation
[Mouse data](Resources/mouse_metadata.csv) and [study results](Resources/study_results.csv) were merged into a single DataFrame and rows with duplicate data (based on a mouse ID with duplicate time points) were removed.

### Summary Statistics
Using both Pandas' `DataFrame.groupby()` and `DataFrame.agg()` methods, a table including the mean, median, variance, standard deviation, and SEM (standard error of the mean) of the tumor volume was created for each drug regimen.

### Bar Plots and Pie Charts
Using both Pandas' `DataFrame.plot(kind='bar')` and MatPlotLib's `pyplot.bar()`, bar plots of timepoints observed per drug regimen were created.

Using both Pandas' `DataFrame.plot(kind='pie')` and MatPlotLib's `pyplot.pie()`, pie charts of gender distribution were created.

### Quartiles, Outliers, and Box Plots
Using a for loop over drug regimens Capomulin, Ramicane, Infubinol, and Ceftamin, the 0.25, 0.50, and 0.75 quartiles were calculated for each mouse's final tumor volume. From the lower and upper quartiles, lower and upper bounds were determined as cuttoff values for potential outliers. All outliers values were extracted and displayed. 

The final tumor volumes boxplots for each of the four drug regimens were compared on a single plot, using MatPlotLib's `pyplot.boxplot()`, with outliers marked with a red 'X'. Boxes represent the IQR (range between the upper and lower quartiles), the orange lines the median value for each drug regimen, and the whiskers the upper and lower boundaries.

### Line and Scatter Plots
For a single mouse undergoing Capomulin treatment, a line graph was generated to show the tumor volume over time using MatPlotLib's `pyplot.plot()`. 

For the Capomulin regimen, a scatterplot was created to show the average tumor volumes for each mouse weight using MatPlotLib's `pyplot.scatter()`.

### Correlation and Regression
The correlation coefficient for mouse weight and average tumor volume of the Capomulin regimen was calculated using Scipy's `stats.pearsonr()` and obtaining the output of the first value.

Using Scipy's `stats.linregress()` function, the slope, intercept, r-value, p-value, and standard error was obtained for the average tumor volume vs. mouse weight scatterplot. The regression line was overlayed on the original scatterplot in red, along with the equation of the line (using MatPlotLib's `pyplot.annotate()'). The r<sup>2</sup> value for the regression oine was printed separately.

## Observations
The Summary Statistics table indicates that Capomulin and Ramicane are the most effective drug treatments because their mean tumor volume (in mm<sup>3</sup>) is the lowest at 40.675741 and 40.216745, respectively. Their lower standard deviations and variances also imply that Capomulin and Ramican produce more precise results.

Outliers are data points that fall outsid of the IQR: the range of each dataset that encompasses 25-75% of the data. Of the four drug regimens (Capomulin, Ramicane, Infubinol, and Ceftamin) selected, Infubinol was the only regimen to have an outlier when looking at final tumor volume (in mm<sup>3</sup>). Along with its higher final tumor volume, this suggests that Infubinol may be less successful than the other three drugs tested.

Correlation coefficients greater than or equal to 0.7 indicate a strong correlation between the two factors being compared. Looking at the scatterplot comparing a mouse's weight (in g) and their average tumor volumes (in mm<sup>3</sup>) under Capomulin treatment, the tight slope predicts a relatively strong correlation. The correlation coefficient of around 0.84 confirms this prediction.
