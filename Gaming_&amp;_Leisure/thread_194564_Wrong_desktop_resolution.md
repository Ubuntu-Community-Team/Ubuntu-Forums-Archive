---
title: "Wrong desktop resolution"
date: 2006-06-11
forum: Gaming &amp; Leisure
---

### Post by kivio on 2006-06-11
Hi, i'm running Ubuntu 6.06 with the graphic drivers from Nvidia.

Whenever i quit an OpenGL game (Quake1, Quake3, Quake4) the desktop changes its resolution to the resolution of the game i was running. 

For example: my desktop runs at 1280x1024 and i start Quake4 with 640x480. I quit Quake4 and my desktop resolution is 640x480. Of course i can change it back to 1280x1024 with xrandr or with ctrl+alt+plus/minus but thats not really a solution. 

The console prints the following message after the game has terminated:

 X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  134 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x1600002
  Serial number of failed request:  76
  Current serial number in output stream:  78

Thanks for your help :)

---

### Post by i8bugs on 2006-12-04
> **kivio said:**
> Hi, i'm running Ubuntu 6.06 with the graphic drivers from Nvidia.

Whenever i quit an OpenGL game (Quake1, Quake3, Quake4) the desktop changes its resolution to the resolution of the game i was running...

I'm having the same problem but no one replied to this post.  I know my son fixed this problem once, but he's in Alaska and can't assist.  
Anyone know how to program Quake3 to be the same resolution as my computer??
bugs.

---

### Post by i8bugs on 2006-12-04
FIXED!  If you have this problem, goto (In the quake opening menu) SETUP>SYSTEM>VIDEO MODE > Set to same resolution as you desktop.
You will not have that problem anymore.

---

