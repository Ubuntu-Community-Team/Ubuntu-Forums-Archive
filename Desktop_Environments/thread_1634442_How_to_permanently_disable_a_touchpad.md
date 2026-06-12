---
title: "How to permanently disable a touchpad?"
date: 2010-11-30
forum: Desktop Environments
---

### Post by akuda on 2010-11-30
Hi,

I am using Ubuntu 10.04 on Lenovo Thinkpad, and I have tree pointing devices:
- touchpad
- trackpoint
- mouse, that is connected only when I am home, so for around 50% of time.

I have downloaded a package "Pointing Devices" and tried to disable a touchpad, which annoys me. Sometimes new settings works, but each time I connect/disconnect mouse, the default settings (everything on) restores. It's even worse, because right now the touchpad works and annoys me, while it's written that it's disabled in "Pointing devices", so either the package is outdated, or it's a BUG.

How to permanently disable a touchpad?

Regards,
akuda

---

### Post by C1377 on 2010-11-30
DISABLE THE HARDWARE.

I am not familiar with LENOVO/IBM laptops, but most have a function  combo (exe. Fn + F6) that does this on the hardware level.

---

### Post by gogolink on 2010-11-30
Try running **gconf-editor** (just type gconf-editor in terminal, or run using alt + F2).

Under / > desktop > gnome > peripherals > touchpad, uncheck the box "touchpad enabled".

Works for me.

---

### Post by inobe on 2010-11-30
> **akuda said:**
> Hi,

I am using Ubuntu 10.04 on Lenovo Thinkpad, and I have tree pointing devices:
- touchpad
- trackpoint
- mouse, that is connected only when I am home, so for around 50% of time.

I have downloaded a package "Pointing Devices" and tried to disable a touchpad, which annoys me. Sometimes new settings works, but each time I connect/disconnect mouse, the default settings (everything on) restores. It's even worse, because right now the touchpad works and annoys me, while it's written that it's disabled in "Pointing devices", so either the package is outdated, or it's a BUG.

How to permanently disable a touchpad?

Regards,
akuda

seen your post and decided to search tutorials and tips part of the forums and found this [http://ubuntuforums.org/showthread.php?t=1629433&highlight=howto+disable+touchpad](http://ubuntuforums.org/showthread.php?t=1629433&highlight=howto+disable+touchpad)

---

### Post by TNT1 on 2010-12-01
Disable the hardware. Either via BIOS, or open the laptop with a screwdriver, and disconnect the tp. I have my lenovo touchpad disabled by disconnecting. (it was dipped in wine, so the touchpad is a bit iffy now...)

---

### Post by akuda on 2010-12-01
the fn-f8 does the trick, thanks

---

### Post by notebookshopper on 2010-12-03
[COLOR=#000000][FONT=Times New Roman][LEFT][FONT=Arial]There's a batch of registry entries for each user's touchpad settings, as well as a single subset of these as a default (fortunately tapping on/off is in this subset). By trial and error (changing the settings in Control Panel, then seeing what effect it had on the registry settings), I discovered that modifying a user's touchpad settings changes their INDIVIDUAL registry entries (so each user can have a different profile), but the default remains the same. However, each time the machine is booted, every user's individual settings are copied from the default, overwriting any recent changes they may have made. I doubt the defaults were meant to be used this way (surely they should be more of a "factory reset" function?), but that's how things happen on our Inspiron

Thanks 

[/FONT][/LEFT][/FONT][/COLOR]

---

### Post by lkilcher on 2010-12-20
I was having this same problem.  I would *disable* the touchpad in "gpointing device settings".  The touchpad would be disabled for a few seconds or so, then it would be start responding again (even though the check box said it was disabled)!  I figured out that this was because I had "disable touchpad while typing" *enabled* under "mouse preferences".  This check box causes a little program "syndaemon" to run, which detects when you're typing and disables the mouse.  Presumably then, it re-enables the mouse whenever it detects that you aren't typing.

!!!!  --  **SOLUTION**  --  !!!!
Therefore, the following solution fixed my problem:
1) uncheck "disable touchpad while typing" under "mouse preferences"
2) check "disable touchpad" under "gpointing device settings".

These steps will disable your mouse.  Hopefully, in the future, "mouse preferences" and "gpointing device settings" will be integrated into one dialogue.  Also, the "disable while any other devices are connected" option is great in theory, but I have a trackpoint that means this does the same thing as "disable touchpad".  Perhaps in the future one will be able to exclude devices that disable the touchpad?

In general though, I'm very happy with all of the features that are available for my touchpad.  Multitouch!  Mouse clicks!  Thanks to everyone who's worked on this.

---

### Post by helgesdk on 2012-12-04
**EDIT**
Ah, I found a much more thorough guide, also using xinput to control the enabled/disabled state:
[http://ubuntuforums.org/showthread.php?t=1629433](http://ubuntuforums.org/showthread.php?t=1629433)
**/EDIT**


Sorry to revive this old thread, but I found another solution in Ubuntu 12.04, which seems more robust and is easy to automate.
My problem was, the touchpad would sporadically re-enable upon resume from suspend.

The following commands should be run in a terminal.

First, find the device id that you want to disable:
```
xinput list
```
In my case, the SynPS/2 Synaptics TouchPad has id=18.

XInput devices have several properties, identified by a number (see xinput list-props <device>).
The "Device Enabled" property has the number 132.

Setting property 132 to 0 will disable the device in X:
```
xinput set-prop <device> 132 0
```
e.g. in this case I will use the command:
```
xinput set-prop 18 132 0
```

Add this command (with the proper device id) to your autostart applications, and you have permanently disabled the XInput device - it cannot even be switched on using the Fn-F8 key combo.

---

### Post by oldos2er on 2012-12-04
Old thread closed.

---

