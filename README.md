# multiplication_practice
Multiplication. Because why not.
import random,sys
score_card={}
'''score_card is a dictionary that contains the various equations that the user 
has been asked as well as a list containing the correct answer and various user responses) '''

playing=True

while playing:
    #if it is the user's first time playing the game
    if len(score_card)<1:
        print("Welcome to Multiplication Practice!")
    
    #here is where the range of numbers is stored for the two numbers
    num1= random.randint(2,4)
    num2= random.randint(2,4)
    product= num1*num2
    
    #the string form of the two numbers (stored as the key in score_card)
    str_product= str(num1)+"x"+str(num2)
    
    #if this question has been asked before
    #still need to figure out how to switch the order of the two numbers to check if it has been asked before
    if str_product in score_card.keys():
        #if the user got the question right when it was first asked
        if score_card[str_product][0]==score_card[str_product][-1]:
            continue
        else:
            user_input=(input("You've gotten this wrong before, so really be careful this time. Enter the product of "+str_product+" : "))
            score_card[str_product].append(user_input)
            #if the user got the product right or wrong
            if user_input==product:
                print("Yay!")
            else:
                print("Nope.")  
    #if the question has not been asked before               
    else:  
        user_input=input("Enter the product of "+str_product+" : ")
        #add it as a key into score_card and create an empty list as the value
        score_card[str_product]=[]
        #then add the correct answer as the first (0th) item in the list
        score_card[str_product].append(product)
        #then add in the user's answer as the second (1st) item in the list
        score_card[str_product].append(user_input)
        if user_input==product:
            print("Yay!")
        else:
            print("Nope.")
    #take out this print statement in the final version
    print(score_card)
