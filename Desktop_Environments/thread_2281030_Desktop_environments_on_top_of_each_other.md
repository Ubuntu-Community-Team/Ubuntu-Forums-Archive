---
title: "Desktop environments on top of each other"
date: 2015-06-03
forum: Desktop Environments
---

### Post by roy27 on 2015-06-03
When I start my system I get an old splash screen from Xubuntu (even though I've just recently installed KDE), after I enter my pass, I then get another splash screen, for Kubuntu. And when I leave my laptop running, or I close the lid, the Xubuntu login screen then resumes, I type in my password, then I get another login screen! Now I have to enter my pass again, but for KDE. Lets say I decided to remove Xubuntu, would some of the programs go with it?  I found this code "sudo apt-get remove plymouth-theme-xubuntu-logo" but I'm not sure if I should try it to try resolve my problem. I'm kind of scared of removing stuff from Xubuntu since that was the desktop environment I've used for the longest time (after I uninstalled Unity, and installed it), and also because I'm scared of deleting something that Kubuntu now uses. 
Here's where I got the steps for installing my Xubuntu: [http://www.pcworld.com/article/2028896/how-to-make-ubuntu-linux-look-like-windows-7.html](http://www.pcworld.com/article/2028896/how-to-make-ubuntu-linux-look-like-windows-7.html) (don't h8 m8). 
tl;dr: I want everything to look like Kubuntu instead of Xubuntu (possibly without removing the Xubuntu desktop environment itself, in case I get bored of KDE), so tell me what to delete (what commands to use).

---

### Post by Copper Bezel on 2015-06-03
The fact that you're seeing the Xubuntu boot screen is the Plymouth thing - technically, you haven't loaded any desktop environment until you log in, which is why some login screens (like the default Ubuntu one) can allow you to choose between them. That part's easy to fix - just install a new Plymouth theme. (I hate that the Xubuntu desktop metapackage does this - installing a desktop shouldn't change things that don't pertain to it - but in the future, you can get around it by installing xfce from the package manager instead of the Xubuntu branded version.)

The other part is odder - you're somehow getting the screen lock from both desktops. XFCE is doing something dumb and not keeping its components and settings to itself. = P Try this, though: log into xfce, and follow [these steps]("http://askubuntu.com/questions/544818/how-do-i-disable-automatic-screen-locking-in-xubuntu") to disable the screen lock, then jump back to KDE and see what happens.

_____

ARGHLEBLAH

Stupid connection on my end, poor error handling on the forum end, and massive multipost results. = /

---

### Post by roy27 on 2015-06-04
Well, I'll get back to you on that later. I upgraded to 15.04, and the longer it runs, the more applications are crashing. Sometimes it's just the application I'm using...sometimes it's the entire desktop.

Edit: Okay, at this point I'm just happy my computer booted up.  : )     
By the way, I looked at that link before, I don't want turn off lightlock, I just want to switch it to the Kubuntu version.

---

### Post by Copper Bezel on 2015-06-04
Eek, sorry to hear about the extra trouble. = . Obviously, I hope you get that resolved in the other thread, even if you have to roll back to 14.04 or something. I'm having some issues with my desktop (which is my secondary machine,) but I've been messing with 15.04 over there, and I plan to install it once I get some hardware stuff sorted. Fingers crossed.

And yeah, I know you wanted to remove / disable as little as possible, it just seemed that if XFCE and KDE were storing their settings separately anyway, you'd still have the KDE lock screen when in KDE.

Thanks to whoever removed my massive multiple post, btw.

---

