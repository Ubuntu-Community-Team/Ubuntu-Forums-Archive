---
title: "XGL + Beryl not working.."
date: 2007-05-13
forum: Desktop Effects &amp; Customization
---

### Post by RobotAlligator on 2007-05-13
I got Linux last night and ive probably been tinkering with it for the last 6 hours.  They just won't install...

I'm using a ATI Radeon 9550 and i've followed numerous guides.  The latest was [http://ubuntuforums.org/showpost.php?p=2564461&postcount=13](http://ubuntuforums.org/showpost.php?p=2564461&postcount=13)

Everything I try and enable desktop effects it gives me The Composite Extension is not available.  Beryl doesn't do anything, and when I followed the guide to log into XGL + Gnome the monitor just goes black and logs me back out.  I've enabled the restricted drivers..

Another error i kept getting earlier was when i tried to do the download xgl it would say I couldn't get it...i forgot the exact wording

---

### Post by x64Jimbo on 2007-05-13
Which driver are you using with that card, and are you sure that it's supported?

---

### Post by overdrank on 2007-05-13
> **RobotAlligator said:**
> I got Linux last night and ive probably been tinkering with it for the last 6 hours.  They just won't install...

I'm using a ATI Radeon 9550 and i've followed numerous guides.  The latest was [http://ubuntuforums.org/showpost.php?p=2564461&postcount=13](http://ubuntuforums.org/showpost.php?p=2564461&postcount=13)

Everything I try and enable desktop effects it gives me The Composite Extension is not available.  Beryl doesn't do anything, and when I followed the guide to log into XGL + Gnome the monitor just goes black and logs me back out.  I've enabled the restricted drivers..

Another error i kept getting earlier was when i tried to do the download xgl it would say I couldn't get it...i forgot the exact wording

Hi you do know that how to is for KDE and breeze. What version of ubuntu are you running?

---

### Post by RobotAlligator on 2007-05-13
Heh...that might be why, I'm using Ubuntu

Any guides around that you know of?


I'm using the ATI restricted drivers thing..

Thanks so far :)

---

### Post by RobotAlligator on 2007-05-13
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550/X1050 Series
OpenGL version string: 2.0.6334 (8.34.8)

I follow a different guide at [http://ubuntuforums.org/showthread.php?t=399643&highlight=xgl+feisty](http://ubuntuforums.org/showthread.php?t=399643&highlight=xgl+feisty)


3rd step in...Am I missing something thats major?

tux@Tux:~$ sudo apt-get install xserver-xgl
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xgl

---

### Post by overdrank on 2007-05-13
> **RobotAlligator said:**
> Heh...that might be why, I'm using Ubuntu

Any guides around that you know of?


I'm using the ATI restricted drivers thing..

Thanks so far :)

Hi and again I ask which version are you using dapper 6.06 or edgy 6.10, or fesity. 7.04?
Dapper no longer supports beryl and edgy does this link will help
[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)
Feisty I have not used   YET ! :popcorn:

---

### Post by emodro on 2007-05-14
> **RobotAlligator said:**
> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550/X1050 Series
OpenGL version string: 2.0.6334 (8.34.8)

I follow a different guide at [http://ubuntuforums.org/showthread.php?t=399643&highlight=xgl+feisty](http://ubuntuforums.org/showthread.php?t=399643&highlight=xgl+feisty)


3rd step in...Am I missing something thats major?

tux@Tux:~$ sudo apt-get install xserver-xgl
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xgl

Yes, you are missing something HUGE, make sure that the universe repository is enabled and that you have an internet connection.. you can make sure my going to software sources, or repositories in synaptic, don't forget to reload.

---

