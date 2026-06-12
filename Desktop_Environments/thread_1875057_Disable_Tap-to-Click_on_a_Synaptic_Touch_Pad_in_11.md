---
title: "? Disable Tap-to-Click on a Synaptic Touch Pad in 11.10"
date: 2011-11-04
forum: Desktop Environments
---

### Post by blanik on 2011-11-04
I have recently moved from Ubuntu 11.04 to Xubuntu 11.10.  Under Xubuntu the Synaptics TouchPad in my Dell XPSL501X notebook ([http://friendly.ubuntu.com/11.10/Dell%20Inc./XPS%20L501X/I:6395p:EZO:I8g:BQz:I8g/devices/](http://friendly.ubuntu.com/11.10/Dell%20Inc./XPS%20L501X/I:6395p:EZO:I8g:BQz:I8g/devices/)) has the "tap-to-touch" feature turned on all the time, which is a real pain as the Dell touch pad is extremely sensitive to touch, and just the slightest touch will cause the cursor to relocate when typing.

Under standard Ubuntu 11.04 and prior versions, tap-to-click and related touch-pad settings can be changed easily in the settings GUI.

Can someone please advise how I turn off tap-to-click in an Xubuntu 11.10 environment ?

Thanks,

Roy

---

### Post by typhoon_tip on 2011-11-04
System Settings -> Mouse and Touchpad -> Touchpad -> Untick "Enable mouse clicks with touchpad"

:)

---

### Post by Toz on 2011-11-04
Open a terminal and type in:
```
synclient MaxTapTime=0
```
If this successfully disables the tap to click, then add a new startup entry (Settings->Settings Manager->Session and Startup->Application Autostart) where the command is:
```
bash -c "synclient MaxTapTime=0"
```

---

### Post by jveezy on 2011-11-11
> **typhoon_tip said:**
> System Settings -> Mouse and Touchpad -> Touchpad -> Untick "Enable mouse clicks with touchpad"

:)

The problem is that option isn't available in Xubuntu. At least not for me.

> **Toz said:**
> Open a terminal and type in:
```
synclient MaxTapTime=0
```
If this successfully disables the tap to click, then add a new startup entry (Settings->Settings Manager->Session and Startup->Application Autostart) where the command is:
```
bash -c "synclient MaxTapTime=0"
```

This fixed it. Thanks.

---

### Post by sffvba[e0rt on 2011-11-11
> **Toz said:**
> Open a terminal and type in:
```
synclient MaxTapTime=0
```
If this successfully disables the tap to click, then add a new startup entry (Settings->Settings Manager->Session and Startup->Application Autostart) where the command is:
```
bash -c "synclient MaxTapTime=0"
```

Very handy to know as I needed it a few days ago (and will be needing it again in a few hours when I re-install Xubuntu :)


404

---

### Post by dkolars on 2012-03-11
I know this is an old thread, but I just found a solution to turn off the touchpad in my HP G60-445DX...  FINALLY!!

gpointing-device-settings :

> sudo apt-get install gpointing-device-settings

Has a "Disable touchpad" checkbox...  worked like a champ!!

I'm using XUbuntu 11.10 on the laptop...

---

### Post by tom king on 2012-03-14
[SIZE=3]Great free tool in Software Center > dconf Editor < that allows you to fix/change anything (almost) in 11.10. Using the check boxes I turned my touch pad off when only typing or you can disable it completely.  Great tool.[/SIZE]):P

---

### Post by poumtatalia on 2012-03-26
Doesn't work here, I get a "Couldn't find synaptics properties. No synaptics driver loaded?" while "Synaptics TouchPad driver for X.Org server"  actually is loaded and up-to-date )-;

---

### Post by Toz on 2012-03-26
> **poumtatalia said:**
> Doesn't work here, I get a "Couldn't find synaptics properties. No synaptics driver loaded?" while "Synaptics TouchPad driver for X.Org server"  actually is loaded and up-to-date )-;

Have a look at this thread: ([http://ubuntuforums.org/showthread.php?t=1757679&page=2]("http://ubuntuforums.org/showthread.php?t=1757679&page=2")) starting from post #12 with possible fix at post #14. It might be related.

---

