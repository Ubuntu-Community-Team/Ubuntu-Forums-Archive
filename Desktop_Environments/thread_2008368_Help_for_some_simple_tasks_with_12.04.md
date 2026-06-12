---
title: "Help for some simple tasks with 12.04"
date: 2012-06-22
forum: Desktop Environments
---

### Post by virsto on 2012-06-22
Note, I am running a dual-boot 32-bit system (Windows Vista, Ubuntu 12.04).

I have recently installed Ubuntu 12.04 and the new desktop interface looks interesting; but, am having some problems coming from 10.04.

First --- tried to move the help program to the top menu (never succeeded)
Second --- tried to move the help program to the launcher (never succeeded)

I searched the help provided with 12.04 but the information given there did not work as described (at least for my installation),  and I did make a real effort to follow what was in the help.

Are there some tricks or "missing" notes needed to perform these simple tasks?
Is it possible to reconfigure the desktop to something like that used by 10.04? I thought this was an excellent desktop.

---

### Post by mwl128340 on 2012-06-22
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

---

### Post by virsto on 2012-06-22
> **mwl128340 said:**
> [http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

I tried this link and followed the information there as close as possible. But, first of all, the installation of gnome-panel did not follow what was shown at this link -- I saw no button with "Click to install GNOME panel in Precise"  . Second, trying to run greeter did not work, even though it is installed, etc. 

In summary, I was unable to install gnome-panel as per the instructions at this link.

Perhaps, there are some other approaches --- do you have any further suggestions?

---

### Post by 3Miro on 2012-06-22
12.04 uses the new Unity interface. You cannot have launchers on the top panel with Unity. You can open a program in the side panel and then right-click on it to select "Lock to Launcher", which will keep it there.

[http://unity3d.com/support/documentation/Manual/User%20Guide.html](http://unity3d.com/support/documentation/Manual/User%20Guide.html)

---

### Post by black veils on 2012-06-23
open the Terminal application, copy-paste the following in
```
sudo apt-get install gnome-panel
```
press enter to run the command.

logout or restart your computer when it has finished^

then follow the last part from that web page link, about selecting the classic gnome session. you choose the session at login screen, by clicking the little icon within the login box.

---

### Post by virsto on 2012-06-23
> **black veils said:**
> open the Terminal application, copy-paste the following in
```
sudo apt-get install gnome-panel
```press enter to run the command.

logout or restart your computer when it has finished^

then follow the last part from that web page link, about selecting the classic gnome session. you choose the session at login screen, by clicking the little icon within the login box.

This worked fine for me --- thanks!

---

