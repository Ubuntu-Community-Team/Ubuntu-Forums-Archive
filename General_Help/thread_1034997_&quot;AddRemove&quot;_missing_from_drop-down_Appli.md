---
title: "&quot;Add/Remove&quot; missing from drop-down Application Menu &amp; no access to &quot;User &amp; Groups&quot;"
date: 2009-01-09
forum: General Help
---

### Post by cradson2000 on 2009-01-09
Hi all,

It has recently become a source of frustration that my "Add/Remove" tab has disappeared from the "Applications" drop-down menu.

I have already re-installed Ubuntu a couple of times and am able to get a couple of things from the software suppository, but then the everything disappears and I am not able to download additional software....

In addition, I am unable to get back into the "Users and Groups" tab, as it keeps telling me that an error has occured and that I have been denied access. Even when I try to log in on the "root" account I get the same message :(

That is equally frustrating since I am unable to download the updates without my root account being recognised.

For the record, I am running Ubuntu 8.10 Desktop Edition, 32-bit.

I love Ubuntu, as I was stuck with Windows Me & XP for 4 years! I want to continue to love it, so would someone please help me with this so that I can continue to love Ubuntu as much as I did before I encountered these problems?


Thank you in advance for any assistance you can offer me :)

Craig :)

---

### Post by eder.apt-get on 2009-01-09
Do you have the latest version of Synaptic? Maybe you should install it via comand shell.
```
sudo apt-get update
```
```
sudo apt-get install synaptic
```

---

### Post by ajgreeny on 2009-01-09
I remember reading of some problem with Add/Remove when other people had installed Adobe Air (have you done that recently?) and a reinstall of *gnome-app-install* and a refresh of the repos with ```
sudo apt-get update
```sorted the problem.  I can't remember what exactly the problem was in these cases, but it will do no harm so give it a try.

---

### Post by ruggles on 2009-05-24
> **eder.apt-get said:**
> Do you have the latest version of Synaptic? Maybe you should install it via comand shell.
```
sudo apt-get update
```
```
sudo apt-get install synaptic
```


This is what occurred during the session: 

jimmy-margaret@ubuntu:~$ sudo apt-get update
[sudo] password for jimmy-margaret: 
jimmy-margaret is not in the sudoers file.  This incident will be reported.
jimmy-margaret@ubuntu:~$ 


This is a computer that I am trying to fix up for my friends who are very computer illiterate (including myself it seems) and I wanted to make sure they  didn't have administer controls so that they don't accidently mess things up like I did. 

I was creating a "root" password in the "Users and Group". That was fine, I closed it and then I tried to re open it and the dialog box to authenticate the process of opening the program kept flickering and I tried to close the program, after several tries it closed but the screen kept flickering, so I thought a reboot was in order. Once rebooted, I can't access "Users and Groups", "Add/Remove" is gone, and I do not have administer rights to the "Synaptic Packages". 

Please don't tell me that I have to reformat.:-({|=

---

