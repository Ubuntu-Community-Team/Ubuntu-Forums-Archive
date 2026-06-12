---
title: "How do I fully go from GNOME to KDE?"
date: 2009-07-03
forum: Desktop Environments
---

### Post by Fzang on 2009-07-03
I've tried installing KDE, packages, metapackages and all that's required. Now, when I load KDE from the login I enter some halfway done enviroment. All applications are defaulted to GNOME variants, applications try to do it GNOME-style and heck, it still hangs onto metacity's theme

So how do I fully kill GNOME (preferably without messing up anything :O) and go to KDE? Is there a script? A command? Do I have to uninstall every GNOME component to ensure maximum KDE'ness?

---

### Post by leef on 2009-07-03
did you install kde using "sudo apt-get install kubuntu-desktop"? that command should set the defaults up for you.

---

### Post by tvtech on 2009-07-03
This is what I did.  

I built one partition for KDE, and another for GNOME.  I have two instances of ubuntu installed.  and have a bunch of virtual links from one instance to the other for things I want the same in both. Seems kinda crazy but otherwise you have to install a lot LOT of KDE dependencies.

---

### Post by aged hippy on 2009-07-04
As you have two separate partitions, i would recommend keeping one for Gnome and installing Kubuntu afresh in the other, sharing a common **/home.**

If you installed Kubuntu alongside Gnome by *sudo apt-get install kubuntu-desktop,* during the install you should have been given the choice to use GDM _or_ KDM as a window manager ... and you should have chosen KDM, but maybe you chose GDM.... ??

---

### Post by Fzang on 2009-07-04
I don't know, it's possible... I'll try again in a moment. I can't make multiple partitions as I'm already dual booting with Windows. And since I have no means of backup (lost my last USB :O!) I don't want to mess around with partitions. I once had all my school work deleted because I did something wrong, so not taking chances ever again :p

---

### Post by aged hippy on 2009-07-04
It's possible to create more partitions, there are 10 on my sda, including one for swap. :)

How much room do you have on the drive? put 
```

df -h

```
into a terminal and post the output here.

---

### Post by Flash858 on 2009-07-04
What I am not getting is why you have 2 seperate installs. It is very easy to install the KDE desktop and then just choose Gnome or KDE at boot. The dependencies you are concerned with would have to be installed irrespective of whether you only had Kubuntu, or if you had both (or multiple) desktops. I once had Gnome, KDE, XFCE, and IceWM all selectable at start-up.

Your second partition seems redundant, and a waste of space to me...

---

