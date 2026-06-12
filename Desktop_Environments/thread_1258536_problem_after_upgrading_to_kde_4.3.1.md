---
title: "problem after upgrading to kde 4.3.1"
date: 2009-09-05
forum: Desktop Environments
---

### Post by anyone2009 on 2009-09-05
[CENTER]Hi guys ,, 
yesterday you help me to upgrade my kde on kubuntu 9.04 to kde4.3.1 
and I follow the instruction and every thing is ok ,,
after the upgrading has been finished and require restart there is  a big problem hapened to me 

this is the picture in the attachments ,, 

really I tried to solve it by going to root shell and write 
```
sudo apt-get remove kde
```
but the result that there is no kde packages in your system to be removed 

so I try to install it from the shell another time 
but the result doesn't change 

there is any solution for my problem ? :(

thanks for everybody
[/CENTER]

---

### Post by anyone2009 on 2009-09-05
here is an other picture 
[http://i28.tinypic.com/2lut8hv.jpg]("http://i28.tinypic.com/2lut8hv.jpg")

---

### Post by anyone2009 on 2009-09-05
any one have a solution ? 

i'm on the live cd from the morning !

---

### Post by 3n!Gma on 2009-09-05
hey, 

your thread@linuxac is clozed becauze of that english, nvr mind
try to do the followin it may help ya to solve ur prob 

First you need to edit 

 ```
/etc/apt/sources.list file
```[INDENT]```
sudo gedit /etc/apt/sources.list
```[/INDENT]add the following line[INDENT]```
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main
```[/INDENT]Save and exit the file
 Add the GPG Keys
```
[INDENT]gpg --keyserver keyserver.ubuntu.com --recv 2836CB0A8AC93F7A
[/INDENT][INDENT]gpg --export --armor 2836CB0A8AC93F7A | sudo apt-key add -
[/INDENT]
```Update source list```
[INDENT]sudo apt-get update
[/INDENT][INDENT]sudo apt-get dist-upgrade
[/INDENT]
```[[COLOR=Red]**check out this thread**[/COLOR]]("http://www.linuxac.org/forum/linuxac55/thread29848.html")

peace !

---

### Post by daboochmeister on 2009-09-07
Same problem, btw.  I also had it set so a right-mouse-click on the desktop brought up a menu that let me change desktop settings, and that's gone, and I can't figure out how to get back to the settings dialog (it's not one of the applets off of the System Settings).

---

### Post by _sleeper on 2009-09-08
same here. after fighting for a day over this, i've switched back to 4.2. actually i went one step further from anyone2009. after the initial screen which was the same as anyone2009's, i managed to get my original wallpaper background and put a task manager on the desktop. only that the task manager took almost half of the screen and it was impossible to resize it or manage it at all, which means: useless. and in the top of it all, when i tried to remove it from the desktop, kde kinda crashed.

---

