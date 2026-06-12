---
title: "Ubuntu 12.04 Running Unity hangs while running browser along Terminal"
date: 2014-08-03
forum: Desktop Environments
---

### Post by Dawood_Shahid on 2014-08-03
Whenever I run my Firefox Browser a long the terminal, my Ubuntu Unity  desktop hangs for a lot of time. It's pretty annoying. Is there a fix to  it or should I try some other desktop environment like Xfce or Lxde.  Maybe Gnome 3?

---

### Post by ajgreeny on 2014-08-03
> **Dawood_Shahid said:**
> [COLOR=#ff0000]Whenever I run my Firefox Browser a long the terminal, my Ubuntu Unity  desktop hangs for a lot of time.[/COLOR] It's pretty annoying. Is there a fix to  it or should I try some other desktop environment like Xfce or Lxde.  Maybe Gnome 3?
What on earth do you mean by that comment in [COLOR=#ff0000]red[/COLOR]?

What hardware do you have?

More information please.

---

### Post by Dawood_Shahid on 2014-08-04
I have a Hp Laptop running at 1.8 Gigs of ram with a 2.4 Ghz cpu. I meant to say that my Ubuntu, running Unity, hangs a lot. Whenever there a terminal process going on, it hangs and I have to restart my laptop.

---

### Post by ajgreeny on 2014-08-04
It sounds as if your computer specs are not quite up to the needs of the unity desktop. I would suggest that you try another DE such as xfce (xubuntu) which needs fewer system resources.

What, in detail, is the hardware you have, particularly the graphic card and cpu (more than just a 2.4GHz; is it dual core, single core, Intel, AMD?

---

### Post by oldfred on 2014-08-04
My laptop is from two weeks before Vista came out, and only has 1.5GB of RAM and Intel video. Full Ubuntu with Unity runs so slow as to be unusable, but I install Classic/fallback/flashback, gnome-panel or whatever it is called and it works well. Name changes with every release and internals have changed from older versions. In 12.04 it is based on gnome3 but has gnome2 panels and menus.

       Precise Gnome Classic Tweaks and Tricks - Cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
From this thread by kansasnoob
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)
But fallback discontinured but rename flashback very similar
[http://www.webupd8.org/2013/02/a-quick-look-at-new-gnome-classic.html](http://www.webupd8.org/2013/02/a-quick-look-at-new-gnome-classic.html)

Lubuntu or Xubuntu may be other choices.

---

### Post by Dawood_Shahid on 2014-08-05
It's a Core 2 Duo. With a default Intel Chipset or something like that.

---

### Post by Dawood_Shahid on 2014-08-05
I've decided to get the xfce desktop environment on my Ubuntu. I want to know, how can I completely remove my Gnome 3 Evnironment and install Xfce Environment. I want to know the command lines for both of those please.

---

### Post by ajgreeny on 2014-08-05
See the (very long) commands here to remove the other available DEs and get to Xubuntu alone.

Don't forget to refresh your repositories first.

---

### Post by Dawood_Shahid on 2014-08-05
How do I refresh my repositories? By sudo apt-get update ?

---

### Post by oldfred on 2014-08-05
If using command line:

 sudo apt-get update
sudo apt-get upgrade

      
 The key meta packages of Ubuntu are :
ubuntu-base (the whole base system which everybody should install)
ubuntu-desktop (the whole gnome environment)
kubuntu-desktop (the whole kde environment)
xubuntu-desktop (the whole xfce4 environment)
lubuntu-desktop (the whole LXDE desktop environment)
edubuntu-desktop (the whole kids/schools oriented gnome environment)
Or:
sudo apt-get install ubuntu-desktop

But if you uninstall the meta-package it uninstalls everything and usually you break system. I did install two versions once, but could not easily houseclean one version as I liked some apps and wanted to keep those, but they had lots of dependencies.

---

