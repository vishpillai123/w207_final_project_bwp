# W207 Final Project

**Berkeley MIDS Program**

Team:  Blair Witch Project

Sharon Wu, Kevin Ngo, Vish Pillai, Blair Jones

Date:  11 April 2021


## Contents

| Folder | Description |
| --- | --- |
| 0_experiments | Individual team folders for EDA and model development. |
| 2021_03_09 | Initial draft of report.  |
| 2021_04_11_Final | Final version of report and team notebook. |

#### Final Report Presentation

<a href='https://docs.google.com/presentation/d/1klo51vk3mqWeEWL_n4Mk5A6Ugdcz_W--Bsz37IYno78/edit?usp=sharing'>
  <img src='./final_thumbnail.png' alt='Final Presentation' width=200/>
  <br>Presentation
</a>


## Introduction

The challenge is to predict seven different forest cover types in four different wilderness areas of the Roosevelt National Forest of Northern Colorado with the best accuracy.  These areas represent forests with minimal human-caused disturbances, so that existing forest cover types are more a result of ecological processes rather than forest management practices.

Each 30 x 30 square meter section of land is described by 54 attributes (ex. elevation, area, soil type, distance to water, aspect, etc.).

The 4 wilderness areas:
- Rawah Wilderness Area
- Neota Wilderness Area
- Comanche Peak Wilderness Area
- Cache la Poudre Wilderness Area

![Roosevelt National Forest](./forest_aerial.png)

The 7 forest cover types:
1. Spruce/Fir
2. Lodgepole Pine
3. Ponderosa Pine
4. Cottonwood/Willow
5. Aspen
6. Douglas-fir
7. Krummholz


## Summary

After thorough EDA, we decided to apply several transformations to the data to highlight key differences between the cover types across the explanatory variables.

With the transformed data, we analyzed the characteristics of several different machine learning models for this type of classification problem.

After some iterations to tune the features and hyperparameter, we conducted a final comparison, shown below.  The **Extra Trees Classifier** achieved the best performance in terms of accuracy and execution time.

We also experimented with a hybrid model, using the Voting Classifier, which takes the output from 2 or more models and determines the best prediction for each sample from across the input models.  *Extra Trees* alone still outperformed the hybrid model.

The full analysis is described in the final report notebook and presentation.


| Model | Accuracy | Time | Comments |
| --- | --- | --- | --- |
| KNN | 0.811 | - | k=1 |
| Decision Tree | 0.771 | - | trees=19 |
| Random Forest | 0.868 | 12 sec | - |
| <span style="font-size:1.5em; color:green;">Extra Trees</span> | <span style="font-size:1.5em; color:green; ">0.910</span> | <span style="font-size:1.5em; color:green; ">15 sec</span> | <span style="font-size:1.5em; color:green; ">trees=600</span> |
| XGBoost | 0.865 | 193 sec | - |
| LightGBM | - | - | - |
| CatBoost | - | - | - |
| Neural Network | 0.865 | 192 sec | layers=6 |
| Hybrid | 0.885 | 79 sec | - |


Hybrid model (Voting Classifier):
- ExtraTrees
- HistGradBoost
- RandomForest
