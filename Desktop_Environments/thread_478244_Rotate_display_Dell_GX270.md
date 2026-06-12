---
title: "Rotate display Dell GX270?"
date: 2007-06-19
forum: Desktop Environments
---

### Post by Nick Payne on 2007-06-19
I have 7.04 installed on a Dell GX270 which uses the nVidia chipset.. I would like to put the monitor in portrait mode, but even after changing from nv to the nvidia driver when I go to System / Preferences / Screen Resolution, rotation is greyed out, and if I go to nVidia settings under System Tools, I can't see any option there for rotating the display. Any suggestion on how I do this?

---

### Post by toobuntu on 2007-06-19
sudo aptitude install xrandr

xrandr -o left
xrandtr -o normal

---

### Post by Nick Payne on 2007-06-19
> **toobuntu said:**
> sudo aptitude install xrandr

xrandr -o left
xrandtr -o normal

Doesn't work:

nick@paw1599:~$ xrandr -o left
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  156 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12

---

### Post by john3333 on 2007-06-20
Here's what worked for me (I have a Dell Dimension 4100 with an NVIDIA GeForce2 MX video card). Basically, I added a line to xorg.conf.
Here's how:
1. Press Alt+F2
2. In the window that opens, type: gksudo nautilus (enter)
3. In the window that opens, double-click on 'File System' in the left pane
4. Double-click the 'etc' folder to open it.
5. Scroll down and double-click on the X11 folder to open it.
6. Once in the X11 folder, scroll down to XORG.CONF  file and double-click it to open.
7. In the xorg.conf file, scroll down to  Section "Device"
8. Add a line at the bottom of this Sectioin "Device" section which says:
Option  "RandRRotation"  "On" 
(with the quote marks only where I've just typed them. And don't leave out any 'R's in RandRRotation -- an easy mistake to make)
9. Save and exit.
10. Reboot, or just restart your desktop using Ctrl+ALT+BACKSPACE
Now you should have the option in your NVIDIA settings to rotate the screen any way you want.
**If this does not work, you can manually type in the rotation setting you want in the xorg.conf file. That would mean that for Step #8, type:
Option "CCW" (with the quotes around CCW. This will rotate your screen 90-degrees counter clockwise, which will give you the portrait mode. If you wanted to, you could also rotate it clockwise by typing in "CW" or invert it by typing "INVERT"
Good luck.

---

### Post by Nick Payne on 2007-06-21
Thanks. That worked, except that I have to manually rotate the desktop after each reboot. Adding Option "CCW" in xorg.conf doesn't seem to automate it. First I added 

Option "RandRRotation" "On" 

to the devices section of xorg.conf, which allowed screen rotation but the rotation didn't persist across a reboot. I then added 

Option "CCW" 

to the devices section, but the screen rotation still doesn't persist across a reboot. Any suggestion on how to achieve that?

---

### Post by Nick Payne on 2007-06-21
> **Nick Payne said:**
> 

Option "CCW" 


Found the entry in xorg.conf should be 

Option "Rotate" "CCW"

---

