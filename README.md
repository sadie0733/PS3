# PS3

#Problem 1
try:
    csv_file = open("/blue/bsc4452/sadiyahu.chatham/homework/CO-OPS__8729108__wl.csv")
    print("data file opened")
except:pwd
    print('cant open')        
csv_file.readline()
lines = csv_file.read().splitlines()
[highest_datime, highest_level, *_] = lines[0].split(",")
for i in range(1, len(lines)):
    [datime, level, *_] = lines[i].split(",")
    level = float(level)
    if level > highest_level:
        highest_level = level
        highest_datime = datime
print("Highest water level:", highest_level)
print("Date and time observed:", highest_datime)
for i in range(1, len(lines)):
    [datime, level, *_] = lines[i].split(",")
    level = float(level)
    if level > highest_level:
        highest_level = level
        highest_datime = datime
print("Highest water level:", highest_level)
print("Date and time observed:", highest_datime)


#Problem 2
try:
    csv_file = open("/blue/bsc4452/sadiyahu.chatham/homework/CO-OPS__8729108__wl.csv")
    print("data file opened")
except:
    print('cant open') 
csv_file.readline()
[highest_datime, highest_level, *_] = lines[0].split(",")
highest_level = float(highest_level)
lowest_datime = highest_datime
lowest_level = highest_level
total_level = highest_level
for i in range(1, len(lines)):
     [datime, level, *_] = lines[i].split(",")
if level > highest_level:
    highest_level = level
    highest_datime = datimel
if level < lowest_level:
    lowest_level = level
    lowest_datime = datime
    total_level += level
print("Highest water level:", highest_level)
print("Date and time observed:", highest_datime)


print("Lowest water level:", lowest_level)
print("Date and time observed:", lowest_datime)


average_level = total_level / len(lines)
print("Average water level:", average_level)


csv_file.close()



#Problem 3 (5 pts):
#Write a script (or Jupyter Notebook) that calculates the fastest rise in water level per 6-minute period between measurements (for this assignment, assume that each line of the dataset is a 6-minute interval) and reports the date and time that was observed and the change in water level from the previous recording.
try:
    csv_file = open("/blue/bsc4452/sadiyahu.chatham/homework/CO-OPS__8729108__wl.csv")
    print("data file opened")
except:
    print('cant open')      

csv_file.readline()
lines = csv_file.read().splitlines()
fastest_rise = 0.0
fastest_datime = ""
for i in range(1, len(lines)):
    [current_datime, current_level, *_] = lines[i].split(",")
    [previous_datime, previous_level, *_] = lines[i - 1].split(",")
    current_level = float(current_level)
    previous_level = float(previous_level)
    rise = current_level - previous_level
    if rise > fastest_rise:
        fastest_rise = rise
        fastest_datime = current_datime
print("Fastest rise:", fastest_rise)
print("Date and time observed:", fastest_datime)
csv_file.close()    


#Problem 4 (5 pts):
#Imagine that the file is providing live readings of the water level. Write a script (or Jupyter Notebook) to print a line of text with a warning if any of these events occur:
#The water level increases more than 0.25 since the previous recording.
#The water level is over 5.0.
csv_file.readline()
lines = csv_file.read().splitlines()
previous_datime = ""
    

for i in range(1, len(lines)):
    [current_datime, current_level, *_] = lines[i].split(",")
    [previous_datime, previous_level, *_] = lines[i - 1].split(",")
    current_level = float(current_level)
    previous_level = float(previous_level)
    rise = current_level - previous_level
    if rise > 0.25:
        print("WARNING: Water rise is more than 0.25.")
    if current_level > 5.0:
        print("WARNING: Water level is over 5.0.")
    [current_d, current_t] = current_datime.split()
    [current_h, current_m] = current_t.split(":")
    [previous_d, previous_t] = previous_datime.split()
    [previous_h, previous_m] = previous_t.split(":")
    current_m = int(current_m)
    previous_m = int(previous_m)
    expected_min = (previous_m + 6) % 60
    if current_m != expected_min:
        print("WARNING: No reading was received.")
csv_file.close()

