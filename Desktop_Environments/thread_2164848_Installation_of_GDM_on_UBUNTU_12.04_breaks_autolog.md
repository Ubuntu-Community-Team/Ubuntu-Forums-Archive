---
title: "Installation of GDM on UBUNTU 12.04 breaks autologin"
date: 2013-08-02
forum: Desktop Environments
---

### Post by dieter-erich on 2013-08-02
Hi,
    since I do not get along with UNITY I have installed GDM on a 12.04 box. Everything was fine until I tried to activate autologin ( either by entering the lines below into the file /etc/gdm/custom.conf) or making this file with the users dialog gui.

The result is the lines below in custom.conf

[daemon]
AutomaticLoginEnable=True
AutomaticLogin=Imyself"

On bootup the screen shows the splash but then becomes black with "OK" or some other messages appearing in the upper right corner.
The box is completely unresponsive.

HOWEVER: I can access the box from another PC over the net with ssh and gnome-panel normally (i.e. I do see the GDM screen)!!

when outcommenting "AutomaticLogin" in both lines of custom.conf above I can again login normally again. But, clearly, autologin does not work.

What I want is an unattended box that I can wake when required and work on it remotely showing to a local user what I am doing. This also requires a functional VNC session but this is another chapter of the story......


Thanks for comments, D-E

---

### Post by ibjsb4 on 2013-08-02
> since I do not get along with UNITY I have installed GDM

Gdm is a display manager and not connected with Unity (a desktop environment).

---

### Post by dieter-erich on 2013-08-03
Sorry I mixed up something! I installed gnome3 in order to have a similar screen as in UBUNTU 10.04.  I can now choose gnome classic for login. However, autologin does not work!

---

### Post by ibjsb4 on 2013-08-03
Im running gnome classic, but not using gdm (using lightdm).  However this looks like the answer.

[http://ubuntuforums.org/showthread.php?t=2064778](http://ubuntuforums.org/showthread.php?t=2064778)

---

