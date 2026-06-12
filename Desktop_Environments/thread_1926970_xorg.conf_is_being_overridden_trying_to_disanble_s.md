---
title: "xorg.conf is being overridden trying to disanble synaptic tap-to-touch"
date: 2012-02-17
forum: Desktop Environments
---

### Post by Tystick86 on 2012-02-17
Does any one know the proper conf file to add Synaptic properties to like MaxTapTime 0 to.  I tried /etc/xorg.conf but I think they get overridden because the output of xinput --list-prop 10 (10 being Synaptic) has nothing to do with what I specified.  I am new to KDE and would appreciate any help

---

### Post by Copper Bezel on 2012-02-17
Yes, it's /usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf. Changes you make there should apply to any DE you're using. You'll want to add a section like this:
```
Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Option "SHMConfig" "on"
        Option "MaxTapTime" "0"
        Option "SingleTapTimeout" "0"
EndSection
```

---

### Post by Tystick86 on 2012-02-17
Thank you for the response Copper Bezel I didn't have the directory /usr/share/X11/xorg.conf.d I tried making it and the config file you recommend but they had no effect I am using BackTrack I don't know if its a little different

---

### Post by Copper Bezel on 2012-02-17
Oh. Yeah, I can't help with that - the above works for Ubuntu and probably Debian-based distros, but BackTrack isn't Debian-based.

You'll be doing a similar thing to a similar file, but I don't know what to tell you in terms of how to find and identify it.

---

### Post by Tystick86 on 2012-02-18
Hugh interesting it has apt-get with Ubuntu Repositories I thought it was Debian based. Oh well thank you for the help.

---

### Post by Copper Bezel on 2012-02-18
Oh, dear, I didn't read to the end of the Wikipedia article. = P Yes, it switched to Ubuntu-based in 2010.

I just found it, though. The location in BackTrack is /usr/**lib**/X11/xorg.conf.d/10-synaptics.conf, not usr/share. Do you see that folder? (I don't have any way of testing this, as I'm not using Backtrack, but it's mentioned in [_this_]("http://www.backtrack-linux.org/forums/showthread.php?t=42520") thread from the BackTrack forums.)

---

### Post by Tystick86 on 2012-02-21
Yes that's the one thank you

---

### Post by Copper Bezel on 2012-02-21
Good! Just mark the thread as Solved if it works (Thread Tools in the upper right) or let me know if it doesn't.

---

