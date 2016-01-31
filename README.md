# practicalmachinelearning
Coursera Project submission

To the grader:

I am having trouble to generate a R markdown file, therefore I copy all the R script and results in this readme file to be graded,  Thanks for understanding. 

# calling 
library(caret)
library(e1071)
testingDataClean<-read.csv("pml-testing.csv")
trainingDataClean<-read.csv("pml-training-clean.csv")
trainingDataClean
summary(trainingDataClean)
inTrain<-createDataPartition(y=trainingDataClean$classe,p=0.8,list=FALSE)
trainData<-trainingDataClean[inTrain,]
testing<-trainingDataClean[-inTrain,]
modelfitSVM<-svm(classe~.,data=trainData)
validation<-predict(modelfitSVM,testing)
confusionMatrix(testing$classe,validation)
prediction<-predict(modelfitSVM,testingDataClean)