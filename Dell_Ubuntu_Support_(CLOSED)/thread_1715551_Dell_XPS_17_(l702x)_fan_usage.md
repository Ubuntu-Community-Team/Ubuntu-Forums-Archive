---
title: "Dell XPS 17 (l702x) fan usage"
date: 2011-03-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wrongman on 2011-03-27
Fan usage on ubuntu seems a lot higher than on windows seven, some missing driver maybe? i7 2nd generation not fully supported yet? someone has the same problem?

---

### Post by Daniel09 on 2011-04-18
Hi All,

I've noticed the same thing with my L701X and i7 core. I'm running Maverik and the fan seems to be spinning constantly. gkrellm places GPU C at around 53 °C for CPU loads below a few percent per thread. Anybody has any ideas if this behaviour is normal?

(Positive effect: I can now use my laptop as an air filtration system.)

Thanks for ideas and help

---

### Post by cbr_king on 2011-05-23
I have the same issue on my L701X. Please, any ideas to solve this? Running Natty 64-bit with latest kernel 2.6.39.

---

### Post by jd.jayded on 2011-05-24
My experience will dells and fans has been the following:
I own an inspiron 1520.
I run ubuntu 10.04 on it (dropped 11.04 like a brick...)

What happened for my was the opposite...the fan didn't run (not entirely true, the BIOS would eventually turn it on an uncomfortable temperature.

Here's a post I just made:
[http://ubuntuforums.org/showthread.php?t=1722080](http://ubuntuforums.org/showthread.php?t=1722080)

Which contains the following:

Assuming you can run i8kutils, this may be helpful:
Here's a script I wrote, and instructions for adding it to auto start up (all users):
Right...I have an inspiron 1520 and had fan issues.
I fixed them using i8kutils, which is derived from the source code of i8k for windows, which was reverse engineered from Dell code.

Note that i8k will let you run a fan on a dell at 0 (off), 1 (slow), or 2 (fast), and that there is a left and a right fan setting. Right and left don't seem to have anything to do with physical location- my machine has a fan on the left and thinks it's the right fan.

i8kfan - 0 sets the right fan to 0 (off), left unchanged
i8kfan - 1 sets the right fan to 1 (slow), left unchanged
i8kfan - 2 sets the right fan to 2 (fast), left unchanged

i8kfan 2 - sets the left fan to 2 (fast), right unchanged.

i8kfan 2 2 sets both to fast

Here are my instructions

Install the i8k utility:
sudo apt-get install i8kutils

Create a fan script (I called it fan.sh), you will need to know the path to it:
#!/bin/sh
#Author jd.jayded
#note: the temperatures set here may be overly conservative. Set as you wish.
fan1=25 #turn fan on to 1
fan2=45 #turn fan on to 2
fanBack1=35 #turn fan back to 1
minFan2=30 #minium time for fan to be spinning on mode two (seconds)
minFan1=0 #minimum time for fan to be spinning on mode one (seconds), set to zero because it can be necessary to increase speeds

while true ; do
    i=`i8kctl temp | tr -dc '[0-9]'` #i8kctl temp gives you current temperature, piped to trim to one numbers
    if [ $i -ge $fan1 ] ; #if it's greater than or equal to fan1
    then
        if [ $i -ge $fan2 ] ;
        then
            i8kfan 2 2
            sleep $minFan2
        else
            if [ $i -ge $fanBack1 ] ;
            then
                sleep $minFan2
            else
                i8kfan 1 1
                sleep $minFan1
            fi
        fi
    else
        i8kfan 0 0
    fi
    sleep 1s #run every second, not counting sleep used as a minimum amount of time to have a fan on
done


Create a start up script. I called it startup.sh
#!/bin/sh
modprobe i8k
/path/to/fan.sh #location of the fan script


Now execute these commands:
sudo ln -s -T /path/to/startup.sh /etc/init.d/startup.sh
sudo update-rc.d [startup script name] defaults

The first command gives you a symbolic link to your startup script in the /etc/init.d directory
The  second command adds the startup script to the default runlevels.  It's  automatically run when you turn on the computer. That will give  you  warnings because I didn't bother learning the proper format for a   System-V init script. man update-rc.d for more about init scripts.

EDIT: sorry about the tabbing dying. I'm new to these forums.

---

### Post by cbr_king on 2011-09-04
Is this working for the Dell L70xxx series? There is no confirmation in this thread.

---

### Post by Zephonim on 2011-09-04
Having this issue myself, machine is running unbelievably hot. Fan is constantly running. It feels like it is actually making my room hotter than it already is...

---

