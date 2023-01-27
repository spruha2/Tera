# Tera Data

This is a jupyter file  format that contains code in Python language and comments in markdown language. The souce data here is Tera Data. Terapixel images offer an intuitive, accessible way to present information sets to stakeholders, allowing viewers to interactively browse big data across multiple scales. This code is for data analysis of three datasets: GPU, Task-x-y, and Application-checkpoints. 

It first imports necessary libraries such as re, numpy, pandas, and nltk, and also imports seaborn and matplotlib for data visualization. Then it loads the data from the CSV files using the pandas read_csv function. The code then examines the shape and structure of each dataset, printing the shape and calling the .info() function for each one. It also prints the first few entries of each dataset using the .head() function. Next, the code attempts to merge the three datasets together, but since the kernel died in the first attempt(due to some extra \ wrong parameter usage ) it instead chooses to work with the separate datasets and  merge them as and when required. It then checks for and removes any duplicate entries in the datasets.

The first goal of the analysis is to determine which event types dominate task runtimes. The code first checks the number of unique events in the Application-checkpoints dataset and then converts the timestamp column to datetime for easier duration calculation. It then converts the timestamp to seconds and drops unnecessary columns. The code then groups the data by event name and event type and calculates the duration between the START and STOP of each event. It then drops the unnecessary entry, 'Total Render', and creates a bar plot of the event names and their corresponding durations using the seaborn library.

Goal 2 is to analyze the relationship between the GPU usage and the task runtime. This can be done by first obtaining the GPU usage statistics for each task, such as average usage and maximum usage. The GPU usage data can then be joined with the task runtime data from the other datasets to form a single table. This table can then be visualized using plots such as scatter plots or line plots to observe the relationship between the GPU usage and the task runtime. Additionally, statistical tests such as correlation coefficient can be used to quantify the strength of the relationship between the two variables. This analysis will provide insights on how the GPU usage affects the task runtime and can be used to optimize the use of GPU resources to improve performance.

Goal 3 defines the interplay between increased power draw and render time can be seen by analyzing the powerDrawWatt and time_seconds columns in the merged dataframe ac_gpu. As the power draw increases, the render time (time_seconds) may also increase. However, the relationship may not be linear and could depend on various factors such as the specific render settings, the complexity of the scene being rendered, and the efficiency of the GPU.
It is possible to quantify the variation in computation requirements for particular tiles by grouping the data by taskId and analyzing the mean or median power draw and render time for each group. This can give an idea of how much computation is required for different types of tiles and how it varies.

Goal 4 of this analysis is to identify any particular GPU cards, identified by their serial numbers, whose performance differs significantly from other cards. The analysis will be based on various performance parameters such as powerDrawWatt, gpuTempC, gpuMemUtilPerc, and gpuUtilPerc. The data is grouped by the GPU serial number and the average of each performance parameter is calculated for each unique GPU card. Bar plots are then generated to visualize the average performance of each GPU card for each performance parameter. This analysis can help to identify any GPU cards that may be performing poorly and in need of replacement.
