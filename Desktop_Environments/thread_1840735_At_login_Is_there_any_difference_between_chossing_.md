---
title: "At login: Is there any difference between chossing Xubuntu Session or Xfce Session?"
date: 2011-09-08
forum: Desktop Environments
---

### Post by mikodo on 2011-09-08
Hi,

As an Ubuntu 10.04 user, I see no differences between choosing at login:

**Xubuntu Session  **    (Use this session to boot in Xubuntu) 

and ...

**Xfce Session**     (Use this session to run Xfce as your desktop environment) 

Is there any differences between the two, or any advantages, over one from the other?

Thanks.

---

### Post by ajgreeny on 2011-09-08
I am not sure, but there could be differences in the various apps and daemons that are started at session startup.

Start up a xubuntu session and run terminal command ```
ps -e > process.txt
```then logout and in again to an xfce session and use command ```
ps -e > process2.txt
``` Now compare the two files process.txt and process2.txt  to see if there are big or important differences.

If you maximise a terminal you can run ```
diff -y process.txt process2.txt
``` and see the files side by side to make the comparison easier

---

### Post by Toz on 2011-09-08
> **mikodo said:**
> Is there any differences between the two, or any advantages, over one from the other?

The xfce session is the default xfce setup. The Xubuntu session includes all of the special "goodies" that the xubuntu team puts together to customize the base xfce setup to give it that xubuntu "look and feel". Try them both out to see the differences.

---

### Post by mikodo on 2011-09-08
Thank you for the replies.

@ ajgreeny:

I couldn't get these commands singularly to show output:
 
```
ps -e > process.txt
```or ...```
ps -e > process2.txt
```When I went into xfce session and ran:
```
ps -e > process2.txt
``` and then:
```
diff -y process.txt process2.txt
```I got output, but both columns of processes appeared the same?

@ Toz,

So far, both Xubuntu session and xfce session, look the same; but I will keep comparing.

I installed Xubuntu on top of Ubuntu 10.04. Would this, make Xubuntu and Xfce sessions' look similar?

Thanks.

---

### Post by Toz on 2011-09-08
> **mikodo said:**
> @ Toz,

So far, both Xubuntu session and xfce session, look the same; but I will keep comparing.

I installed Xubuntu on top of Ubuntu 10.04. Would this, make Xubuntu and Xfce sessions' look similar?

Thanks.

Possibly, I don't know. I've never installed xubuntu on top of ubuntu. I can tell you that from a fresh xubuntu install, the two sessions are visibily different (different themes/layouts).

---

### Post by mikodo on 2011-09-08
> **Toz said:**
> Possibly, I don't know. I've never installed xubuntu on top of ubuntu. I can tell you that from a fresh xubuntu install, the two sessions are visibily different (different themes/layouts).

Thanks. :^)

---

### Post by mikodo on 2011-09-09
> **ajgreeny said:**
> I am not sure, but there could be differences in the various apps and daemons that are started at session startup.

Start up a xubuntu session and run terminal command ```
ps -e > process.txt
```then logout and in again to an xfce session and use command ```
ps -e > process2.txt
``` Now compare the two files process.txt and process2.txt  to see if there are big or important differences.

If you maximise a terminal you can run ```
diff -y process.txt process2.txt
``` and see the files side by side to make the comparison easier

I found the the processes in my /home. I will compare the two from there and see if there are any important differences. Then, I will compare the two lists from the ```
diff -y process.txt process2.txt
``` terminal output, just to see if they are the same lists. 

But not right now, I have to go.

Thanks.

---

### Post by smssms on 2011-10-04
From my personal experience in the past few minutes:

Xubuntu - VERY slow i.e. seconds for right-click to respond, minutes for a simple uninstall. Hight processor and swap usage.

Xfce - normal speed but not noticeable faster than the stock Ubuntu Gnome interface

Don't know why, just saying what I saw...

---

