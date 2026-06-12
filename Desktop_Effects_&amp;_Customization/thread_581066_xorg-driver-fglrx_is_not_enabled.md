---
title: "xorg-driver-fglrx is not enabled"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by ash4ever on 2007-10-19
I installed ubuntu 7.10 today and got the following error when trying to enable the ATI accelerated graphics driver: **xorg-driver-fglrx is not enabled**

Please assist, as i'm a newbie, with step by step points to resolve, please, please!!!!

---

### Post by Stemp on 2007-10-19
Are you connected to Internet ? 
What is your card ?

---

### Post by RedfishBluefish on 2007-10-19
If you were using the restricted drivers manager to do this (and probably even if you weren't) you should be able to fix this by opening System/Administration/Software Sources and ticking "Proprietary drivers for devices".
I had this exact same problem.

---

### Post by mats-a on 2007-10-19
I did this then I got a new message saying "Could not apply changes, Please fix broken packages first"

Any idea what to do?

---

### Post by Forlong on 2007-10-19
Try this:
```
sudo apt-get -f install
```

---

### Post by mats-a on 2007-10-19
didnt do anything

---

### Post by ash4ever on 2007-10-19
I'm using a ati X700 on my laptop which use to work fine on 7.04 (feisty)

---

### Post by ash4ever on 2007-10-19
yes i have internet access

---

### Post by RedfishBluefish on 2007-10-19
I think if you go into Software Sources again, and tick the source "Community-Maintained Open Source software", that should fix it,
And if that don't work tick "Software restricted by copyright or legal issues".


"Broken packages" typically means that the package you're trying to install depends on another package which can't be installed for various reasons, one of those reasons being that that package is in a disabled repository ("Software Source").
[/Technical Details]

---

### Post by ash4ever on 2007-10-22
Thanks for getting back and sorry for the late reply.

Tried both of that and got the following error message: "The software source for the package xorg-driver-fglrx is not enabled."

Please advise?:(

---

### Post by ash4ever on 2007-10-22
A big thank you to everyone trying to help me, fixed the problem.

I re-installed 7.10 and made sure that my internet connection was active before the installation.

Once installed i didn't get any errors. I then followed the following instructions: 

Re: The Composite extension is not available? 

--------------------------------------------------------------------------------

Quote:
Originally Posted by meindian523  

To install Xgl:
Code:
sudo apt-get install xserver-xgl 

And this fixed my problem :)

A big thanks to everyone who tried to help.

Thanks
Ash

---

### Post by Stemp on 2007-10-22
This link will help you : 

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)


[Edit] : too late :D

---

### Post by RedfishBluefish on 2007-10-22
> Tried both of that and got the following error message: "The software source for the package xorg-driver-fglrx is not enabled."
Again? You still had the restricted drivers enabled, right? If so that might be a bit of a bug..

Anyway it's good to know you fixed the problem!:)

---

### Post by ash4ever on 2007-10-22
Thanks for all the help guys, much appreaciated.

Ubuntu rocks and windows sucks as usual...lol

---

### Post by Jeeverz on 2007-10-26
I had the same problem, and i got this error in terminal 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  xserver-xgl: Depends: libglitz-glx1 but it is not installable
               Depends: libglitz1 (>= 0.4.3+cvs20050728) but it is not installable
E: Broken packages



and everytime i try to enable the graphics thing, it says that there are 'broken packages'

---

### Post by GordonFrohm on 2007-11-04
*****@*****-desktop:~$ sudo apt-get install xserver-xgl 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xgl
*****@*****-desktop:~$

---

### Post by Forlong on 2007-11-04
Go to *System &#8594; Administration &#8594; Software Sources* and make sure (at least) **main** and **universe** are checked.

---

### Post by Redenbacher on 2007-11-09
I had this same problem and ticking all of the software sources fixed it. Thanks!

---

### Post by nschive on 2007-12-04
*

---

### Post by Peryl on 2007-12-05
had the same error a while ago XP

---

