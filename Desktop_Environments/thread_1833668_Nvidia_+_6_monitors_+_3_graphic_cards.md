---
title: "Nvidia + 6 monitors + 3 graphic cards"
date: 2011-08-26
forum: Desktop Environments
---

### Post by fuchini on 2011-08-26
Hello, 

Just Installed Ubuntu 10.04 in a computer with 3 Nvidia GT430 and 6 monitors. Under Nvidia Settings I can enable a second screen as twinview but dont know how to setup the other 4. I'm an ubuntu noob so please bear with me. I don't know what info. should I post. Any help would be appreciated. Thanks!!!

---

### Post by fuchini on 2011-08-26
Hi, I sorted this by myself, a different X screen for each monitor, enabled xinerama and saved configuration.

---

### Post by realzippy on 2011-08-26
means,everything works as you wanted?
..doesn't xinerama kill desktop effects?

---

### Post by fuchini on 2011-08-26
Haven't tried any effects but with Xinerama I couldn't open Firefox in a different display. Don't know why. But I would like to drag windows around the screens. As soon as I can I'll post the error message. But all i've done has been thanks to you realzippy!!!!

---

### Post by realzippy on 2011-08-26
> **fuchini said:**
> Haven't tried any effects but with Xinerama I couldn't open Firefox in a different display.

Isn't that the nature of [xinerama]("http://en.wikipedia.org/wiki/Xinerama"),as the name says:
You have only 1 big fat screen.
Think you have to go for Twinview.
Suggest some googling,lllllots of stuff...

---

### Post by fuchini on 2011-08-26
Hello, 

Twinview works but between 2 adjacent screens (each pair that's connected to equal cards) and when I maximize a windows it maximizes across both screens. Is there a way to have a different X screen in each monitor but still darg windows or a way to have cinerema and open applications in different screens?

I've learned a lot today, Thanks!!!

---

### Post by fuchini on 2011-08-26
Maybe using Xinerema and wmctrl to move my windows around?

---

### Post by realzippy on 2011-08-27
Maybe...as mentioned,you are pretty alone with this uncommon project.
As far as I understood that [6-monitor-guy]("http://ubuntuforums.org/showthread.php?t=884161"),he used xgl,and kind of fake-xinerama/twinview mix:

*#3 My final solution was a combination of the 3 twinview configurations, enable xinerama, and installing xserver-xgl from the package manager. Once these things were in place i had one large virtual screen with 3D enabled across all 6 monitors! I heard that there were issues with xserver-xgl but I haven't had any issues and I've been running on this for a few weeks now.. I will revisit the original xserver-xorg configuration again in the future to see if I can get it to work - but the limitation seems to be that if I enable xinerama with it - compiz-fusion will no longer work.. and without enabling xinerama - i was stuck with 3 separate xscreens! (so if i can find a solution to merge the 3 twinview screens without using xinerama *

*#4 - the final issue had to do with the fact that now that i had all 6 monitors working as one - xserver-xgl now decided that when i maximize a window - it needs to maximize across all 6 monitors! I looked for various options and the one i came up with was a hack of the xinerama library itself - (do a search on google for fake xinerama) - but.. I now see that compiz-fusion has its own settings for settings monitor arrangements and you can manually enter them. The benefit of the fake xinerama deal was that it also allowed the bootup / login screen to show up in one monitor instead of expanded across all 6..*

---

### Post by realzippy on 2011-08-27
Maybe just ask him for help:

Shane Menshik
D2 GLOBAL INC.

[https://plus.google.com/109118911280249779106/posts](https://plus.google.com/109118911280249779106/posts)

---

### Post by fuchini on 2011-09-01
Thanks for all your help realzippy. I'll try to find out about the fake xinerama but for now it will stay as it is.

---

