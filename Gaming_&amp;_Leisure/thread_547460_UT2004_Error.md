---
title: "UT2004 Error"
date: 2007-09-10
forum: Gaming &amp; Leisure
---

### Post by derekr44 on 2007-09-10
I've installed UT2004 (the 6cd version) by running the linux-installer.sh file located on install CD1.  The install went without a problem and it successfully exported the map files on the first run.  However, after exporting the maps, the game crashes and the following error is displayed in terminal:

> WARNING: ALC_EXT_capture is subject to change!
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x186
  Serial number of failed request:  164
  Current serial number in output stream:  165


Help?

I'm running the latest nVidia binary drivers with Beryl/Gnome.  I've tried running this without Beryl but am receiving the same error.

---

### Post by Perfect Storm on 2007-09-10
Have you installed the latest patch? If not, first do that.

---

### Post by derekr44 on 2007-09-10
Same error:

> WARNING: ALC_EXT_capture is subject to change!
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x186
  Serial number of failed request:  163
  Current serial number in output stream:  164


---

### Post by Perfect Storm on 2007-09-10
ok

Next question is; Are you running the 64bit version of Ubuntu?

---

### Post by derekr44 on 2007-09-10
Nope.  This is vanilla Ubuntu, the i386 version.

---

### Post by Perfect Storm on 2007-09-10
*scratches his head*...

Lets see the xorg.conf


```
cat /etc/X11/xorg.conf
```

---

### Post by derekr44 on 2007-09-10
At work now, so I'll grab xorg when I get home.

Yeah, I know it's wierd...

---

### Post by Perfect Storm on 2007-09-10
Yeah, I've been reading up to see if anyone else had similiar problem, but havn't seen so far.

I run UT2004 with the latest nvidia driver with no problems.

My guess might be that perhaps a beryl option or another option in the xorg.conf might mess something up.

---

### Post by derekr44 on 2007-09-10
I searched the forum for "XF86VidModeSwitchToMode" and found only one thread (with no replies) about someone who couldn't play any games in full-screen.

I'm trying to think of what my xorg says...

Come to think of it... I think I removed all resolution settings (ie. 1024x768, 800x600) from it because I wanted to force 1440x900.  So is it possible that UT2004 is looking for 800x600, but can't find it as an option?  I did notice that 1440x900 was the only resolution option when I got it working through Crossover.

---

### Post by Perfect Storm on 2007-09-10
If that so, you need to edit the ut2004 ini file to set the resolution that you prefer. No wonder it wouldn't work ;)

You'll find it in: ~/.ut2004/System

---

### Post by derekr44 on 2007-09-10
Yup, that was it.

---

### Post by md_lasalle on 2007-09-10
hey, just dropping to say that i had this problem, and got around to fix it!

I recently messed around with my xorg.conf file, and had to reinstall ATI driver for my X1600. Since then, i wasnt able to play it.

Everywhere in the xorg.conf where you see resolution, it was only "1440x900"

Adding the other resolutions didnt fix it at first, but going in the ~/.ut2004/System/UT2004.ini file and changing the

FullscreenViewportX=1280
FullscreenViewportY=800

by

FullscreenViewportX=1024
FullscreenViewportY=768

in [SDLDrv.SDLClient] section fixed it!

Like if my new driver installation didn't support 1280x800 anymore. Because this is the last resolution i played in.

---

### Post by derekr44 on 2007-09-11
Yup.  I adjusted mine to 1024x768 for windowed and 1440x900 in fullscreen and it worked.

---

