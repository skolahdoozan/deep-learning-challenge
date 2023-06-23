# deep-learning-challenge
Overview:
    The nonprofit foundation Alphabet Soup wants a tool that can help it select the applicants for funding with the best chance of success in their ventures. In this challenge, we're trying to use machine learning and neural networks techinques to create a binary classifier that can predict whether applicants will be successful if funded by Alphabet Soup. In order to achieve this goal, the features in the provided dataset is going to be used.

Data Processing:
    The provided dataset has the following information regarding organization received the funding:
        1- EIN and NAME—Identification columns
        2- APPLICATION_TYPE—Alphabet Soup application type
        3- AFFILIATION—Affiliated sector of industry
        4- CLASSIFICATION—Government organization classification
        5- USE_CASE—Use case for funding
        6- ORGANIZATION—Organization type
        7- STATUS—Active status
        8- INCOME_AMT—Income classification
        9- SPECIAL_CONSIDERATIONS—Special considerations for application
        10- ASK_AMT—Funding amount requested
        11- IS_SUCCESSFUL—Was the money used effectively

    From the provided data, the EIN and name of the organization removed as they are not a determining factor for this process. Also, the targeted value for this project is "IS_SUCCESSFUL" values showing if the funding was used effectively or not. Furthermore, the rest of variables were considered as relevant data information regarding the success of the funding.

    Categorial variables with a large number of unique values can affect the accuracy and running time of models. Therefore, the number of unique values for each data feature needs to be determined. It's observed that there more than 10 values for Application Type, and Classification. After looking closely to the uinque values of these two attirbutes, the application types less than 156 and classifications with less than 1,883 occurances were moved to the other category. The cutoff values were determined based on the percentage of data falling into OTHER categories (less than 3%). 

    In the next step, the categorial data were converted to numeric values using pd.get_dummies. Then, the dummy data were added to the original dataframe and the original data for them were dropped. 

    Lastly, the next step was to divide the dataset into a training and testing datasets. Then, a StandardScalar instances were made to scale the data. 

Compiling, Training, and Evaluating the Model:
    A deep neural net was created and 2 hidden layers and 1 output layer were defined. For the first hidden layer, 80 nodes and the 2nd layer 30 nodes were considered. For the 1st try, some moderate numbers based on the size of the dataset were selected to measure the accuracy of the model. These numbers might need to be changed based on the model' accuracy. Below, a summary of the model's structure is shown:


                                                Model: "sequential_1"
_________________________________________________________________
                            Layer (type)                Output Shape              Param #   
                            =================================================================
                            dense_3 (Dense)             (None, 80)                5520      
                                                                                            
                            dense_4 (Dense)             (None, 30)                2430      
                                                                                            
                            dense_5 (Dense)             (None, 1)                 31        
                                                                                            
                            =================================================================
                            Total params: 7,981
                            Trainable params: 7,981
                            Non-trainable params: 0

    Based on this summary, 7,981 trainable parameters are going to be used for the model training. 

    The next step is compiling the model and the accuracy were defined for the model compilation. Then, the model was trained based on the compilation, and 100 epochs were used for the 1st round. 

    Based on the evaluation of the developed model on the test dataset, the accuracy and loss were 72% and 56%, respectively. 

Optimization:
    As the accuracy of the 1st model is 72%, the model needs to be optimized to to achieve a target predictive accuracy higher than 75%.

    The 1st Optimization:
        The cutoff values for Classification and Application Types were lowered, so more data variables can be used for the model training. The result of this method did not change the accuracy and loss values. 

    The 2nd Optimization:
        Adding 1 more hidden layer and more neurons to hidden layers were tried. The accuracy and loss of this model were 72% and 57%, respectively. This try showed that the model's loss increased.

    The 3rd Optimization:
        As increasing the number of nodes made the model's performance worse, the number of nodes were decreased in the 3rd try. However, the accuracy stayed the same as the original model. 


Summary:
    It's observed that the accuracy of the model didn't reach to the 75% threshold by trying different optimization methods. Below, you can find some suggestions regarding the model improvement:
        1- Dataset doesn't reflect all of the factors contributing to the scuccess of the funding. Therefore, more information regarding each company is requires. These factors can be the number of employees, the employees specialty and background, and the number of years that the entity has been in the business. 
        2- Different optimization methods might need to be tried. 
        
        


