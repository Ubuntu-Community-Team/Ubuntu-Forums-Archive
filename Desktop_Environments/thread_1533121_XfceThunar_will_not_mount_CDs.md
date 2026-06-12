---
title: "Xfce/Thunar will not mount CDs"
date: 2010-07-17
forum: Desktop Environments
---

### Post by hhh on 2010-07-17
I have Volume Management enabled in Thunar, and I have Removable Storage set to "Mount removable media when inserted". If I insert a DVD I get an icon on my desktop and in the side-pane of Thunar and a folder appears in /media. If I insert a CD I get... nothing. I can play an audio CD in gxine or mplayer or Decibel, but I can't browse the contents with Thunar. The same drive is used for both CDs and DVDs.

Any ideas?

---

### Post by bobcollard on 2010-07-17
> **hhh said:**
> I have Volume Management enabled in Thunar, and I have Removable Storage set to "Mount removable media when inserted". If I insert a DVD I get an icon on my desktop and in the side-pane of Thunar and a folder appears in /media. If I insert a CD I get... nothing. I can play an audio CD in gxine or mplayer or Decibel, but I can't browse the contents with Thunar. The same drive is used for both CDs and DVDs.

Any ideas?
In Setting>Xfce Settings Manager>Removeable Drives and Media> tab to Multimedia and choose an Application to open your Audio CD with by clicking on the folder to the right of Command:  You will find a list of Applications, my favorite is Exaile.  There you can see the contents of your CD and it will open to that each time a CD is placed in the drive.

---

### Post by hhh on 2010-07-18
Thanks for the reply. That's what I've been doing (via Decibel Audio Player), but I was curious why thunar-volman will recognize DVDs but not CDs. I've checked it with 3 Xfce-based distros via a Live USB and they all ignore CDs but give me a nice desktop icon for DVDs and USB drives. No problem with Gnome distros (I haven't checked KDE).

---

### Post by hhh on 2010-07-19
Be-bump.

---

### Post by hhh on 2010-07-22
Bump.

---

### Post by bobcollard on 2010-07-22
Have you tried to use a different File Manager?  It would need to be the default to get it to open a CD on insertion.  Sorry, been away from the computer a few days.

---

### Post by hhh on 2010-07-22
PCManFM shows the CD in it's side pane, but clicking on it gives the error message "Location is not mountable". Nautilus does the same. I haven't tried installing gnome-volume-manager.

---

### Post by bobcollard on 2010-07-23
> **hhh said:**
> PCManFM shows the CD in it's side pane, but clicking on it gives the error message "Location is not mountable". Nautilus does the same. I haven't tried installing gnome-volume-manager.
In Xfce  4 Settings Manager>Desktop Tab Icons check the box for Removable Devices and insert a CD, then see if you can open it from the desktop.

---

### Post by hhh on 2010-07-23
It's checked, USB drives and DVDs show a desktop icon, CDs never do. I've tried some other Xfce distros via Live USB and it's the same thing there, maybe it's hardware specific for me. Gnome is not a problem.

Are you running Xfce and can you mount CDs?

---

### Post by bobcollard on 2010-07-23
> **hhh said:**
> It's checked, USB drives and DVDs show a desktop icon, CDs never do. I've tried some other Xfce distros via Live USB and it's the same thing there, maybe it's hardware specific for me. Gnome is not a problem.

Are you running Xfce and can you mount CDs?
Running Xubuntu Xfce 10.04 amd_64.  My CDs open in Exaile on the desktop, not in Thunar.  See screenshot attached.

---

### Post by hhh on 2010-07-23
So you have the exact same situation as me...
> **hhh said:**
> I can play an audio CD in gxine or mplayer or Decibel, but I can't browse the contents with Thunar.

You can play the CD, but you don't get an icon on your desktop, you can't see the drive in Thunar, you can see the drive but can't browse it in PCManFM or Nautilus, but if you insert a DVD or a USB drive you get both a desktop icon and a Thunar icon that you can examine the drive's contents with.

---

### Post by bobcollard on 2010-07-23
> **hhh said:**
> So you have the exact same situation as me...


You can play the CD, but you don't get an icon on your desktop, you can't see the drive in Thunar, you can see the drive but can't browse it in PCManFM or Nautilus, but if you insert a DVD or a USB drive you get both a desktop icon and a Thunar icon that you can examine the drive's contents with.
Not exactly, I am not trying to find another way to see it, LOL.

---

### Post by hhh on 2010-07-23
Yeah, it's certainly not a deal breaker, I love my Xfce setup. I'm just curious why other DEs will "see" the CD while Xfce will not.

---

### Post by bobcollard on 2010-07-23
> **hhh said:**
> Yeah, it's certainly not a deal breaker, I love my Xfce setup. I'm just curious why other DEs will "see" the CD while Xfce will not.
For me it's like this.  KDE is "Pretty" but, flawed, I have too many problems making things work in it.  Gnome is bloated and slow, it works, that's the only thing I can say for it.  I have tried most of the other distros with all three desktops and stayed with Ubuntu for ease of use.  I also use PC/OS which I am waiting for a new version (11) to come out.  To each his own and whatever works on your computer.  I try to make a difference helping out where I can.  Sorry if this did not help you, maybe next time?

---

### Post by hhh on 2010-07-23
Cheers!

---

### Post by fredbird67 on 2010-07-24
Bob, it's neat to see a fellow PC/OS user on here! :-)  I'm just a couple hours away to your south in St. Louis.  But yeah, I've noticed that too whenever I want to play a CD -- I have to open Exaile or VLC or whatever and click play to get it started.  No big deal, but still, it would be a lot nicer if Xfce would automatically play the thing, ya know?

---

### Post by bobcollard on 2010-07-24
> **fredbird67 said:**
> Bob, it's neat to see a fellow PC/OS user on here! :-)  I'm just a couple hours away to your south in St. Louis.  But yeah, I've noticed that too whenever I want to play a CD -- I have to open Exaile or VLC or whatever and click play to get it started.  No big deal, but still, it would be a lot nicer if Xfce would automatically play the thing, ya know?
The OP wanted a File Manager like Thunar to "Open" the CD so he could see the contents.
On the PC/OS front Roberto has his team working to get out the first Test of PC/OS 11, still waiting on that.  I'm an Insider waiting on the three versions to test.  Can't say much more than that.

---

### Post by jerrykenny on 2010-07-25
Go on . . . . . install konqueror !

you know you want to . . . ;)

---

