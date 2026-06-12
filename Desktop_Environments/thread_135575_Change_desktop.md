---
title: "Change desktop"
date: 2006-02-24
forum: Desktop Environments
---

### Post by lengguard on 2006-02-24
Is there a link that will tell me how to turn Ubuntu into Kubuntu

---

### Post by andrewsawyer on 2006-02-24
You should just be able to download KDE from Synaptic, and then choose it as the default login - I think.  Can someone pls confirm?

---

### Post by gingermark on 2006-02-24
There are several meta-packages available, that will install a multitude of other packages.

'kde-core' will give you just a basic kde desktop.
'kde' will give you the default kde desktop.
'kubuntu-desktop' will install the default Kubuntu desktop - if you want to try Kubuntu this is probably the one you want.

When you install the Kubuntu packages you will be given the choice of whether to use KDM or GDM - either is fine. The main difference, apart from aesthetic differences in the login screen, is the ability to shut down the computer from within the Desktop Environment - KDM allows this for KDE, and GDM for GNOME.

Using Synaptic to install Kubuntu is probably the best way to go, as the log feature will help you determine what packages to remove if you want to get rid of KDE at a later date, although there are other threads about that provide a commandline option to do this.

---

### Post by dropper on 2006-02-24
[QUOTE=lengguard]Is there a link that will tell me how to turn Ubuntu into Kubuntu[/QUOTE]

Just go to synaptic and download/install kubuntu-desktop. I just did the opposite a couple days ago (ubuntu-desktop)...

---

### Post by greatshape on 2006-02-24
[QUOTE=dropper]Just go to synaptic and download/install kubuntu-desktop. I just did the opposite a couple days ago (ubuntu-desktop)...[/QUOTE]

Yes, but you will still have the gnome display manager at login.
If you want to change this do
```
sudo apt-get install kdm
```


Steve

---

### Post by Sparticuz on 2006-02-24
If I want to remove a desktop what apps do I have to remove...I want to remove KDE...I've already tried 

```
sudo apt-get remove kubuntu-desktop
```

but it only removed about 40kb, and If I remember correctly the install for that package was around 600mb. I also want to change my default login screen back to gdm. How do I do that? Right now I can't even log in to my computer. I go to log in at the kubuntu login screen, and no matter which session I choose (besides failsafe), It kicks me right back to the login.

---

### Post by bluevoodoo1 on 2006-02-24
Here's a great how-to about removing the kubuntu-desktop meta-package.

[http://www.ubuntuforums.org/showthread.php?t=96048](http://www.ubuntuforums.org/showthread.php?t=96048)

---

### Post by bluevoodoo1 on 2006-02-24
EDIT: double post (please delete)

---

### Post by RJ Hythloday on 2008-02-26
> **gingermark said:**
> There are several meta-packages available, that will install a multitude of other packages.
 
'kde-core' will give you just a basic kde desktop.
'kde' will give you the default kde desktop.
'kubuntu-desktop' will install the default Kubuntu desktop - if you want to try Kubuntu this is probably the one you want.
 
When you install the Kubuntu packages you will be given the choice of whether to use KDM or GDM - either is fine. The main difference, apart from aesthetic differences in the login screen, is the ability to shut down the computer from within the Desktop Environment - KDM allows this for KDE, and GDM for GNOME.
 
Using Synaptic to install Kubuntu is probably the best way to go, as the log feature will help you determine what packages to remove if you want to get rid of KDE at a later date, although there are other threads about that provide a commandline option to do this.
 
I'm working on a build for a friend, I installed xdm and made it default, I lost the ability to shut down. It has restart, hibernate, etc but no shutdown.
 
I also installed the edubuntu light (xfce) desktop and fluxbox but I don't have an option to choose the desktop at login. I think it's because of xdm. Is there another way to set the default desktop?

---

