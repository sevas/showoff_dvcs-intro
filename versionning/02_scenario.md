!SLIDE transition=toss

# Let's talk about a non-revisionned collaborative software project
## Bad patterns in non-revisionned code


!SLIDE 

# Start a new project,
# create a file 
## (``.py``, ``.c``, ``.m``, whatever)



!SLIDE

# Add some code 

    @@@ python
    # sum.py    
    def compute_sum(a_list):
        sum = 0
        for i in range(len(a_list)):
            sum += a_list[i]
        return sum

!SLIDE
# Try out a new approach, comment out the old version

    @@@ python
    # sum.py    
    def compute_sum(a_list):
        sum = 0
        #for i in range(len(a_list)):
        #    sum += a_list[i]
        for value in a_list:
            sum += value
        return sum


!SLIDE

# Oh wait, cool new idea


    @@@ python
    # sum.py    
    def compute_sum(a_list):
        #sum = 0
        ##for i in range(len(a_list)):
        ##    sum += a_list[i]
        #for value in a_list:
        #    sum += value
        #return sum
        from operator import add
        return reduce(add, a_list, 0)

!SLIDE

# Looks familiar ?
## The poor readability should strike you


!SLIDE transition=scrollLeft

# Popquizz

!SLIDE small

# What does this program do ?

    @@@ python
    #import sys
    #import time
    from time import sleep

    #i = 0
    ## print "i=", i
    #while i < 10:
    #    print i
    #    #i+=1    # 2010-05-02
    #    i = i+1
    #    time.sleep(1) 
    for i in range(10):
        print i
        # time.sleep(1)
        sleep(1)
    #print "done"    
       
    

!SLIDE

# Try again
 
    @@@ python
    from time import sleep

    for i in range(10):
        print i
        sleep(1)

    
!SLIDE  transition=scrollRight

# Readability is important for productivity
## Don't undermine this


!SLIDE smaller 

# Code hoarding
## I don't want to throw away code !


    @@@ python
    # sum.py, v0.3
    def compute_sum_v1(a_list):
        sum = 0
        for i in range(len(a_list)):
            sum += a_list[i]
        return sum


    def compute_sum_v2(a_list):
        sum = 0
        for value in a_list:
            sum += value
        return sum


    def compute_sum_v3(a_list):
        from operator import add
        return reduce(add, a_list, 0)



!SLIDE

# On a sufficiently small project, this might work
## But who cares about having 3 versions of the same function ?

!SLIDE

# This is not good


!SLIDE 

# Now, for the bad part
## What if you **need** to go back to an older, working version?


!SLIDE bullets incremental

# Reverting commented parts one by one!

* This will be very error prone
* and unproductive.
* You will probably make a mistake



!SLIDE

## Keypoint:
# Don't manage different versions of your source files **in** the source files



!SLIDE transition=toss

# Enters collaborative work

!SLIDE center transition=slideY

![Yay, collaboration!](mice_shadow.png)


!SLIDE bullets incremental


# Sharing changes with your team ?

* USB Flashdrive !
* EMail !

!SLIDE center

# Handling concurrent changes ?
## ``ctrl-C``,  ``ctrl V``

![](files_shadow.png)


!SLIDE

## Keypoint:
# Highlighting and resolving differences in text files is easy to do for a computer 
## Let it do the work 

!SLIDE

# **Repeat** :
# *"Anything that can go wrong, will go wrong."*



!SLIDE

# There has to be a better way


