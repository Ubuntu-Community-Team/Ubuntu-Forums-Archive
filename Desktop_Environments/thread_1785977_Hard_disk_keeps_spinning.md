---
title: "Hard disk keeps spinning"
date: 2011-06-19
forum: Desktop Environments
---

### Post by adit on 2011-06-19
I am a regular ubuntu user from 7.10 till now.  Now I am using 11.04.  This problem never happened with previous releases.  When I open more than 4 windows in firefox or whenever I open "Ubuntu Software Center" the hard disk keeps spinning, mouse and keyboard are frozen.  I tried to reboot from tty1.  It takes around 3 minutes to get the command prompt after pressing Ctrl + Alt + F1.
I reinstalled 11.04 several times.  This problem is not solved.  I have applied all the updates.
What program is exactly causing this problem?  How to diagnose?

---

### Post by wildmanne39 on 2011-06-19
> **adit said:**
> I am a regular ubuntu user from 7.10 till now.  Now I am using 11.04.  This problem never happened with previous releases.  When I open more than 4 windows in firefox or whenever I open "Ubuntu Software Center" the hard disk keeps spinning, mouse and keyboard are frozen.  I tried to reboot from tty1.  It takes around 3 minutes to get the command prompt after pressing Ctrl + Alt + F1.
I reinstalled 11.04 several times.  This problem is not solved.  I have applied all the updates.
What program is exactly causing this problem?  How to diagnose?
Hi, it sounds like you are running low on memory and ubuntu is writing to the swap file on the hard drive to keep you going. It could be that your swap is being used when it does not need to be used. You can open system monitor and see what program are using your resources and how your memory is doing. Also you could run top from a terminal.

---

### Post by adit on 2011-06-19
I don't have a swap partition.  This is the status of my memory just before the system freezes
```
:~$ free
             total       used       free     shared    buffers     cached
Mem:       1012904     975944      36960          0      44848     292900
-/+ buffers/cache:     638196     374708
Swap:            0          0          0
```
Is it a problem really with the memory?  Any solutions? (installing additional memory or creating a swap partition).
For me it doesn't appear to be a problem with the memory.  It is the "Ubuntu Software Center" that exactly causes this problem. Whenever I start this program the keyboard and mouse freeze and hard disk lights show continuous activity.

---

### Post by Slovak on 2011-06-19
Try running memtest to test your memory. If it is good, try a swap partition, it does have a few uses.

---

### Post by wildmanne39 on 2011-06-19
> **adit said:**
> I don't have a swap partition.  This is the status of my memory just before the system freezes
```
:~$ free
             total       used       free     shared    buffers     cached
Mem:       1012904     975944      36960          0      44848     292900
-/+ buffers/cache:     638196     374708
Swap:            0          0          0
```
Is it a problem really with the memory?  Any solutions? (installing additional memory or creating a swap partition).
For me it doesn't appear to be a problem with the memory.  It is the "Ubuntu Software Center" that exactly causes this problem. Whenever I start this program the keyboard and mouse freeze and hard disk lights show continuous activity.
Hi, it looks like you may be running low on memory, a swap partition would help most likely. Also I have seen one person saying you can set up a swap file instead but you would have to do a search on that, I do not know how to do that. I am not sure you can create a swap partition easily,  I am going to give you a link to look at.
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by dFlyer on 2011-06-19
> **adit said:**
> I don't have a swap partition.  This is the status of my memory just before the system freezes
```
:~$ free
             total       used       free     shared    buffers     cached
Mem:       1012904     975944      36960          0      44848     292900
-/+ buffers/cache:     638196     374708
Swap:            0          0          0
```
Is it a problem really with the memory?  Any solutions? (installing additional memory or creating a swap partition).
For me it doesn't appear to be a problem with the memory.  It is the "Ubuntu Software Center" that exactly causes this problem. Whenever I start this program the keyboard and mouse freeze and hard disk lights show continuous activity.

You might want to add more ram and maybe create a swap partition.

---

