---
title: "Wake Up and Go To Sleep"
date: 2009-02-04
forum: General Help
---

### Post by ZimmtheElder on 2009-02-04
I have just taken delivery on an 8G eeePC and it's really a lot of fun...runs Easy Peasy, an 8.10 Ubuntu derivitive.  I'm interested in getting it to sleep at a certain time of day and wake up the next morning at xx AM.  In other words, I'd like to turn it into a clock radio of sorts.  There's a package in the repositories called shutdown-at-night which apparently does something along this line, but there's no apparent documentation with it.  I'm not interested in writing code to make this happen...just check a couple of items in a UI and go about my business.  Is this the right package?  Any suggestions for how to accomplish this?

---

### Post by cariboo on 2009-02-04
You might want to look at gshutdown, it has a  gui, whereas the first program you  mentioned is a command line app.

Jim

---

### Post by ZimmtheElder on 2009-02-04
Thanks, Jim...does it handle the wake up duties as well?

---

### Post by Aisteru on 2010-11-07
I think you should look at this: [https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)
I had to do some careful reading to get mine working that way. Some of the info seems to be outdated, or just inaccurate (or maybe I just didn't understand it.). I still  don't know how to keep it set properly after a Linux shutdown, but as  long as it is hibernating, it works.

Here is a script I wrote to do it for my laptop. It might work with yours. You should still read the above article in any case. You will still have to hibernate/shut it down yourself, I don't know how to automate that.

#script to set the wakealarm for 2010-11-08 08:25:00.
#I should figure out how to get it use the next day's date automatically, instead of setting #it manually.
#This must run as root. 

SECS=`date -u --date "2010-11-08 08:25:00" +%s`
sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"
sh -c "echo $SECS > /sys/class/rtc/rtc0/wakealarm"
cat /proc/driver/rtc

---

