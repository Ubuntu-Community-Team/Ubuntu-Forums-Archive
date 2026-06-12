---
title: "Changed resolution, and white screened!"
date: 2009-03-09
forum: Desktop Environments
---

### Post by BiynaYahu on 2009-03-09
Hello everyone,

  I am running 8.10 Intrepid Ibex on an Inspiron 1501 laptop.  I was running an open source shooter, (it has a weird name I can't think of right now) and when I quit out of it my virtual desktop was larger than my screen.  In an attempt to get Gnome to fix itself I thought to change the resolution, and then change it back.  I dropped the resolution to something ridiculous like 300x120.  Way down from the native 1200x800.  As soon as I hit apply it white screened.
  I restarted the computer into recovery mode, and ran Xfix.  This allowed my to boot to my desktop, and I thought I was home free.  I was not home free.  A buddy of mine was over and we decided to play World of Warcraft.  It wouldn't load.  So, naturally I checked to see if my proprietary video driver was loaded.  Nope.
  I loaded the driver, and rebooted.  WHITE SCREEN!  To say the least I was very disappointed.  I ran Xfix again, rebooted, and opened up my resolutions.  I changed the resolution from 1200x800 to 1024x786, and it white screened again.  Now nothing I do will allow me to get to my desktop.  It shows the GDM, but as soon as I log in it white screens.  Any help would be greatly appreciated.  :D:KS:D

---

### Post by BiynaYahu on 2009-03-09
*bump*

---

### Post by BiynaYahu on 2009-03-09
*bump*

---

### Post by BiynaYahu on 2009-03-10
I tried running xrandr -s 1200x800, but it replied cannot open display

---

### Post by Zorael on 2009-03-10
Please post the contents of your **/etc/X11/xorg.conf** file. There are probably GUI ways of troubleshooting this, but I don't know them. :3

Also, "proprietary driver"; Nvidia?

Lastly, xfix resets your X configuration file (xorg.conf), which naturally removes any references to drivers that should be explicitly loaded, along with every other custom options it may contain. Instead, upon X start it autodetects your hardware and loads what it deems proper. And it never loads proprietary drivers unless told to (in, again, xorg.conf).

---

### Post by BiynaYahu on 2009-03-10
```
Section "Device"
        Identifier                  "Configured Video Device"
EndSection

Section "Monitor"
        Identifier                  "Configured Monitor"
EndSection

Section "Screen"
        Identifier                  "Default Screen"
        Monitor                     "Configured Monitor"
        Device                      "Configured Video Device"
EndSection
```

No, it's an ATI 1101 or something integrated card.  11xx for sure.

Also, I'm off to work now.  So, I won't be able to reply for a couple hours (4 or 5).

---

### Post by warp99 on 2009-03-10
You need to add the fglrx driver to your xorg.conf. When you reset xserver the xorg.conf file was overwritten. You may have a backup copy of your xorg.conf file in the same directory. If that's the case restore the backup file instead. If no backup exists open your xorg.conf file as root and scroll down to this section, then add the item in bold:

```
Section "Device"
        Identifier                  "Configured Video Device"
        **Driver                      "fglrx"**
EndSection

```

---

### Post by BiynaYahu on 2009-03-10
I used a back up of my xorg.conf, but I'm still getting a white screen....

---

### Post by MGT Systems on 2009-03-11
The dreaded white screen is the bane of my life.  The last time I got it, this fixed it:

Download the latest proprietary FGLRX driver from the ATI website (if you haven't already got it).  Make sure you've installed the "fakeroot" package.  Uninstall current version of FGLRX.  Run the .run autoinstall script you just downloaded.

I can't remember if there are any other packages it needs or not, but I'm sure you'll find out...

---

### Post by BiynaYahu on 2009-03-24
Okay, I had a problem getting my internet working.  I've since solved the problem.  Unfortunately, I don't know how to ensure that the FGLRX driver is uninstalled properly using the command prompt.

---

### Post by BiynaYahu on 2009-03-24
Okay, I don't know what is going on, but now I have Gnome up, and running.  Now I have the problem of the resolution configuration utility thinking my monitor is 15". 


edit:  hmmm... it might be 15 inches....

---

### Post by BiynaYahu on 2009-03-24
it works, it doesn't work, it works, it doesn't work... I don't know.

---

### Post by irv on 2009-03-24
This has happen to me a few time. The way to get back to normal is to boot and when the grub comes up boot to the latest kernel in recovery and choose the fix video mode. After it run you will have a chance to boot normal.
This always worked for me.

---

### Post by BiynaYahu on 2009-03-24
So, ummm...  It's working again now.  Plus, now it's working without a hitch.  I absolutely give up on trying to figure out what just happened, and I'm gonna just blame it on the fact that this is a Dell, and a laptop...  Thank you everyone for all of your help!

edit: And down it goes.  I have no idea.  I've completely formatted and reinstalled my root, and boot partitions.  I have gotten a fully functional boot.  How can it just kick in and our like this.  I mean is this hardware damage?

---

### Post by BiynaYahu on 2009-03-25
*bump*

---

### Post by irv on 2009-03-25
> **BiynaYahu said:**
> So, ummm...  It's working again now.  Plus, now it's working without a hitch.  I absolutely give up on trying to figure out what just happened, and I'm gonna just blame it on the fact that this is a Dell, and a laptop...  Thank you everyone for all of your help!

edit: And down it goes.  I have no idea.  I've completely formatted and reinstalled my root, and boot partitions.  I have gotten a fully functional boot.  How can it just kick in and our like this.  I mean is this hardware damage?

It does sound like you are having a hardware issues. I have one Dell laptop (and a new one at that) model 1521 that just doesn't like Ubuntu Linux. I had so many issues with it I gave up trying to run it with Linux. All my other pc's love Ubuntu.

---

### Post by BiynaYahu on 2009-03-28
*bump*

---

### Post by BiynaYahu on 2009-04-02
Okay, so I think it's time to approach this problem from a different angle.  I think the first thing I should attempt is to use the provided utility to set the parameters of my video settings.  You know lock in the only settings I'm gonna use.  1280x800 resolution, 60Hz refresh rate (I think), and you know lock in those settings permanently. So, my real questions here are, how do you set those parameters (is it using xrandr?)?  Plus does anyone know all the specifics I should input for my monitor.  Remember I am using a Dell Inspiron 1501.  Also, when answering I cannot use any GUI programs to do this.  As soon as I log in I have to crtl+alt+backspace, and run a Failsafe Xterm.  Thank you all again.

---

