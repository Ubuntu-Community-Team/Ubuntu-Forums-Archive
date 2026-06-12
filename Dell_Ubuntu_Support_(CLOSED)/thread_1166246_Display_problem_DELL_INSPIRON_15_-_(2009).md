---
title: "Display problem DELL INSPIRON 15 - (2009)"
date: 2009-05-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rajinikanth.sree on 2009-05-21
Hi All, 

I recently brought Dell INSPIRON 15'' laptop. And wanted to install Ubuntu in my laptop. All went fine (i am a admirer of linux but not too techi so bare with me) 

 - I created a 60 GB partition in HDD
 - Ubuntu was installed successfully 
 - System restarted to load Ubuntu for the 1st time 

(Problem starts from here)

 - All setting were checked by Ubuntu and the result was OK for all of them 
 - When it came to display check Ubuntu started to show the trouble.
 - There was no display - the screen was distracted 

Suggest me what should be my next steps so that i can use and enjoy Ubuntu in my laptop.

Other details 
Display adapter in laptop is "Mobile Intel(R) 4 Series Express Chipset Family"
Laptop brought in India 

Awaiting valueable inputs.

Regards, 
Rajini
DELL INSPIRON 15 | 2009 | Win Vista Basic | 350 GB | 4 GB RAM | UBUNTU (not fully installed)

---

### Post by coffeeaddict22 on 2009-05-23
Hi,
 and welcome to Ubuntu!  
Easy first step is boot up with your Ubuntu CD in the drive.  Running the system off the CD will show you whether it will run OK or not; if you get the same problem when the CD is in there may be a problem with the setup.  Graphics in particular are a problem, although on a new machine less so.  A whole lot of ATI cards got deprecated recently, although that shouldn't stop your system working at a basic level.

Next step is try booting into a recovery console- it's the second option on the list.  In there, you have a choice to "Repair my graphics setup".  Try that and see what happens.

If you can get into a recovery console this way and it's still not fixed, type in ```
dmesg
``` and have a look at the output.  That may help localise the problem.

---

### Post by rajinikanth.sree on 2009-05-25
Hi - Thanks a lot for you input and suggestion. Will try it and let you know if i was able to fix the issue.

Regards, 
Rajini

---

### Post by Mike1949 on 2010-06-03
Is there a list of which ATI cards have been deprecated?  When I upgraded to 10.04 my display stoped working correctly.  It sort of works, but not correctly.  Is it possible to use an older driver from an earlier version?  9.10 worked fine.

Thanks,

Mike

---

