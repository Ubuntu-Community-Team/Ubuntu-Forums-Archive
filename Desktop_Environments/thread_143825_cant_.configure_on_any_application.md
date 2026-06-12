---
title: "cant ./configure on any application"
date: 2006-03-13
forum: Desktop Environments
---

### Post by chetanthaker on 2006-03-13
hey guys

I've had a strange problem since I installed Breezy 

I've not been able to ./configure any (source files ??) application

Pleaes do help me out


here is the error log attached below

I DID install x-dev and libx11-dev

Please do help ASAP

I'm trying to install **Taskbar v2**

Anyone got its debian package ??

please do PM me if you do have a .deb file

Regards

CeeTee

---

### Post by dresnu on 2006-03-13
Taskbar v2 is included in kde 3.5 and 3.5.1. You can just upgrade in order to have it.

---

### Post by chetanthaker on 2006-03-13
I DO have KDE 3.5.0

What do I do ??

Is there any apt-get for taskbar v2 ??

---

### Post by dresnu on 2006-03-13
Right Click on Panel-> Add Applet to Panel-> Scroll down and you should see it then click add to panel

---

### Post by sweeney276 on 2006-03-13
Have you downloaded build-essential?

Unfortunately Kubuntu (or Ubuntu) doesn't come with these tools installed as standard in the base package.  Once this package is downloaded you should be able to compile any program from source.

---

### Post by chetanthaker on 2006-03-14
Hey guys

@dresnu - Dude, i dont see Taskbar v2 on my applets - Just see the regular Taskbar

@sweeney276 - Dude, i did build-essential, installed 2 packages -- still gettin da same problem 

Please do make a deb file of Taskbar v2 and PM the link to me.. :)

Thanx

CeeTee

---

### Post by htinn on 2006-03-14
You have "xlibs-dev"?

---

### Post by chetanthaker on 2006-03-14
The ./configure went past the X server checks

Now I get an error that says 

> 
checking for Qt... configure: error: Qt (>= Qt 3.0) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.


Please do help me 

CeeTee

---

### Post by rattking on 2006-03-14
sudo apt-get install libqt3-mt-dev
should help that

---

### Post by chetanthaker on 2006-03-14
hey there

the qt thing did get solved

but now a diff error !! (:evil:)[B]

checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix![/B]

Now WHAT ??

gettin TOO pi$$3d now !


CeeTee

---

### Post by rattking on 2006-03-14
kde-devel
is the correct set of packages i think
on the brighter side you wont have to do this next time you compile a kde app

btw i am finding these dev packages buy useing
apt-cache search whatever |grep dev

---

