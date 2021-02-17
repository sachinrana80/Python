# Python Miscllineous 
# Program 'a' asks the user to enter three numbers (use three separate input statements). Create variables called total and average that hold the sum and average of the three numbers and print out the values of total and average.

# Import libraries
import numpy as np
import pandas as pd
import statsmodels.api as sm
import matplotlib as mp
import matplotlib.pyplot as plt

%matplotlib inline

my_list = []
for i in range(1,4):
    num = int(input('Enter number ' + str(i) +' : '))
    my_list.append(num)

total = np.sum(my_list)
average = np.mean(my_list)

print ('Total = %d and Average = %d' %(total, average))

# Enter number 1 : 1
# Enter number 2 : 3
# Enter number 3 : 5
# Total = 9 and Average = 3

# Program 'b' generates a list of 50 random integers such that the first integer number is between 1 and 2 (including 2), the second is between 1 and 3, the third is between 1 and 4, . . . , and the last is between 1 and 51.
import random
rand_list = []

for i in range(2,52):
    rand_list.append(random.randrange(1, i))

print (rand_list)

# [1, 2, 2, 2, 5, 6, 1, 7, 4, 7, 4, 3, 5, 13, 6, 5, 13, 2, 14, 20, 3, 1, 6, 11, 9, 14, 9, 11, 6, 25, 29, 6, 33, 7, 6, 25, 5, 20, 25, 19, 14, 5, 19, 26, 12, 45, 2, 32, 32, 19]


# Program 'c' is function that asks the user to enter a positive integer  𝑛 , and then computes  (1+12+13+...+1𝑛)−ln(𝑛) . It Plots the the value of the function for different values of n=10,100,500,1000,10000.

import math
inp_num = int(input('Enter a positive number :'))

def y_fun(n):
    sum_y = 0
    for i in range(1,n+1):
        sum_y += 1/i
    return(sum_y - math.log(i))

print (y_fun(inp_num))
# Enter a positive number :8
# 0.6384156011773068

# Plot a bar chart
objects = [10,100,500,1000,10000]
y = []
for i in objects:
    y.append(y_fun(i))
y_pos = np.arange(len(objects))
score_y = []

for i in range(len(objects)):
    score_y.append(((y[i] - min(y))/(max(y) - min(y))* max(y))+.07)

y_pos = np.arange(len(objects))
y_lab = np.round(np.linspace(min(y),max(y),10),2)
score = y
plt.yticks(np.linspace(min(score_y), max(score_y),10),y_lab)

like_scores = np.array(range(0,len(objects)))
data_norm = mp.colors.Normalize()
color_map = mp.colors.LinearSegmentedColormap("my_map",{"red": [(0, 1.0, 1.0),(1.0, .5, .5)], 
                                                        "green": [(0, 0.5, 0.5), (1.0, 0, 0)],
                                                        "blue": [(0, 0.50, 0.5),(1.0, 0, 0)]})

y_pos
plt.bar(y_pos, score_y, align='center', alpha=0.5, color=color_map(data_norm(like_scores)))
plt.yticks(np.linspace(min(score_y), max(score_y),10),y_lab)

plt.xticks(y_pos, objects)
plt.ylabel('Function Value')
plt.xlabel('X -->')
plt.title('Function')
plt.grid(True)
locs, labels = plt.xticks()
plt.setp(labels, rotation=90)

plt.show()

