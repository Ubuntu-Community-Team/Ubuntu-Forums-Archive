---
title: "Kayboard layour switch settings forgotten"
date: 2008-12-10
forum: General Help
---

### Post by amos.shapira on 2008-12-10
Hello,

I'm using 32-bit Ubuntu 8.04 on a 1 year old Dell desktop. System is kept up to date.

I have USA and Israel keyboard layouts on it.

I configured the Alt-SHIFT combination to switch between layouts (copied from Windows) using System->Preferences->Keyboard->"Layout Options" and the "Layout" tab.

The configuration is remembered until the next reboot.

After reboot - I see that the combination is still marked in the Preferences above but I have to untick and re-tick it in order to make it effective again.

I also tried to set any of the keyboard LED's to indicate that the alternative layout is in effect but none of them works.

What should I do in order to make it work without having to reset it after every reboot?

Thanks.

--Amos

---

### Post by eternalnewbee on 2008-12-10
Go to: **Main Menu > System > Preferences > Sessions > Options** tab, and click **Save Currently Running Application**.

---

### Post by prshah on 2008-12-10
> **amos.shapira said:**
> 
What should I do in order to make it work without having to reset it after every reboot?

See any of these links: 

[[SOLVED] keyboard layout disappears on boot]("http://ubuntuforums.org/showthread.php?t=850040&highlight=setxkbmap")
[[SOLVED] Keyboard Layout Settings won't stick after reboot]("http://ubuntuforums.org/showthread.php?t=813567&highlight=setxkbmap")
[[SOLVED] Keyboar layout keeps resetting to US]("http://ubuntuforums.org/showthread.php?t=898384&highlight=setxkbmap")
[Keyboard preferences lost on automatic login]("http://ubuntuforums.org/showthread.php?p=5860154&highlight=setxkbmap#post5860154")

Summary: Add "setxkbmap" to your startup sessions.

---

### Post by amos.shapira on 2008-12-10
> **prshah said:**
> See any of these links: 

[[SOLVED] keyboard layout disappears on boot]("http://ubuntuforums.org/showthread.php?t=850040&highlight=setxkbmap")
[[SOLVED] Keyboard Layout Settings won't stick after reboot]("http://ubuntuforums.org/showthread.php?t=813567&highlight=setxkbmap")
[[SOLVED] Keyboar layout keeps resetting to US]("http://ubuntuforums.org/showthread.php?t=898384&highlight=setxkbmap")
[Keyboard preferences lost on automatic login]("http://ubuntuforums.org/showthread.php?p=5860154&highlight=setxkbmap#post5860154")

Summary: Add "setxkbmap" to your startup sessions.
Thanks. I actually liked the suggestion to just add the second layout to xorg.conf, as described in the first reply to [http://ubuntuforums.org/showthread.php?t=898384&highlight=setxkbmap](http://ubuntuforums.org/showthread.php?t=898384&highlight=setxkbmap)
I edited the file but can't logout right away to test this. Will post here when I can.

Thanks very much for researching this for me - it's done so well that at first I suspected it was done automatically by the forum system :)

---

### Post by amos.shapira on 2008-12-12
I just got around to test the fix - it works.

I tested by logging out then hitting Ctrl-Backspace, which kills the X server. I think this is close enough without having to reboot.

I still don't see any change in the LED indicators. I might put that in the xorg.conf file too.

Thanks.

---

### Post by amos.shapira on 2008-12-16
1. After another reboot the problem returned - had to unset and re-set the layout switching checkbox to make layout switching work.

2. I found the following bug reported in Lunchpad, which confirms that this is an issue with auto-login (which I use):

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/228196/](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/228196/)

Posting here to help others find this.

Thanks.

---

### Post by prshah on 2008-12-16
> **amos.shapira said:**
> 1. After another reboot the problem returned - had to unset and re-set the layout switching checkbox to make layout switching work.

Did you try adding setxkbmap to your startup sessions? From Intrepid onwards, settings in xorg.conf are commented out since HAL handles input devices.

---

### Post by amos.shapira on 2008-12-16
> **prshah said:**
> Did you try adding setxkbmap to your startup sessions? From Intrepid onwards, settings in xorg.conf are commented out since HAL handles input devices.
Nope. How should I do this? Just "save current session"?

What I DID try and worked is running the following command from a terminal window:
setxkbmap -print | xkbcomp - $DISPLAY

I created a ~/.xsession as follows:
```

#!/bin/sh
setxkbmap -print | xkbcomp - $DISPLAY > /dev/null 2>&1
```And made it executable. I'll wait till next reboot to test this.

Also for now I intend to stick with 8.04 - it's LTS, I'm happy with it (I'll eventually find a way to fix this annoyance), and I heard bad things about Intrepid.

Thanks very much!

---

### Post by prshah on 2008-12-17
> **amos.shapira said:**
> Nope. How should I do this?

See the linked threads in my earlier post for the details; I don't understand what you've done with the .xsession thing, that may be correct, but there is a easier and sure way with what is linked in the earlier post.

---

