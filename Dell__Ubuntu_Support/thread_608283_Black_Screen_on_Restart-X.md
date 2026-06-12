---
title: "Black Screen on Restart-X"
date: 2007-11-09
forum: Dell  Ubuntu Support
---

### Post by KillerSiafu on 2007-11-09
I did a clean install of gutsy on a Dell 1420 N. Everything appears to be working fine for the most part. However, when for whatever reason I need to restart X (ctrl-alt-backspace), I run into a problem.

It appears to restart X fine. It brings up the ubuntu login screen and I'm able to login in no problem, I even get the sounds associated with logging in. However, the desktop never loads. It sits at this black screen with an X for a cursor.

I've tried restarting X again at this point but it appears to be unresponsive. Attempting to restart my computer with ctrl-alt-delete also doesn't work. The only way I've been able to get out of it is to hold down the power button for a hard reboot. The only other thing I can try is to do alt f1, but I'm not sure if that will work or not. 

Any help is appreciated. I attached my xorg.conf

---

### Post by insineratehymn on 2007-11-10
What kind of video card does your Dell have?

I'm asking to see if your xorg.conf file reflects the proper drivers.

---

### Post by KillerSiafu on 2007-11-10
It's an Intel Mobile GM965/GL960 Integrated Graphics Controller (unfortunately).

---

### Post by insineratehymn on 2007-11-10
Have you tried reconfiguring your xorg server?

> sudo dpkg-reconfigure xserver-xorg

Its gonna go through a series of choices with you in the terminal (old school DOS style). Its kind of like DragonQuest... make the right choices and hope it flies.

But seriously, before you do anything that sounds like xorg, xserver, or anything that has an x in it, its a good idea to **backup** your xorg.conf file, that way if it breaks you can just replace it.

To back it up:
> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup

To replace it:
> sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf

---

### Post by KillerSiafu on 2007-11-10
Well I tried that and ran through the different options. I don't think i really changed anything but I tried restarting x and it made it past the black screen and onto the desktop so I guess that worked. Unfortunately, my mouse is now moving extremely slow (despite its sensitivity / acceleration being turned way up in the settings). I've fixed this problem before but I can't remember how.

---

### Post by insineratehymn on 2007-11-10
Try using syndaemon...
> syndaemon -l

Or something like that, I've never gotten my Synaptic TouchPad to work, so...

Glad to hear you got colours on your screen now!

---

### Post by KillerSiafu on 2007-11-10
I remembered how I fixed the touchpad problem.

When i did that configuration utility you mentioned it overwrote my xorg.conf (obviously). So i took a look at my backup copy and remembered I had added the following lines to the 'Section InputDevice for the Synpatic Touchpad'. 

        Option "MinSpeed" "0.60"
        Option "MaxSpeed" "1.10"
        Option "AccelFactor" "0.030"
        Option "EdgeMotionMinSpeed" "200"
        Option "EdgeMotionMaxSpeed" "200"
        Option "UpDownScrolling" "1"

Thought I'd post that for anyone else experiencing the same problem. Thanks for the help, I've restarted X twice now with no problems and my touchpad is working again!

---

