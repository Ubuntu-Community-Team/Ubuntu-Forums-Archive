---
title: "Ubuntu v6.06 on Dell not seeing ViewSonic video drivers"
date: 2007-07-04
forum: Dell  Ubuntu Support
---

### Post by walktheline on 2007-07-04
Okay, I'm a newbie and I admit I should know immediately what to do.  However, I have searched the forums and cannot find a concise "way" to do this correctly.  I recently tried out Ubuntu 6.06, and just bought a ViewSonic 19" Q19wb monitor. The reccomended setting (1440x900) is not a choice to be selected when trying to change the Screen Resolution from the system preferences.

I have gone to the terminal and tried adding the code "1440x900" underneath the SubSection "Display" area.  But this does not resolve anything, and I have done the adequate cntrl+alt+backspace to log out, and have logged out.  Still nothing.  

I am using a Dell PC, with Intel Corp. 945G Integrated Graphics Controller and a Q19wb monitor.  Can someone dumb it down for me, what steps I need to take in order for this monitor to be used to it's fullest optimization?  Thank you in advance-

---

### Post by whizbaby on 2007-07-04
BEFORE doing any change to your /etc/X11/xorg.conf make a backup of it so you can fall back to your old config:
 
sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.saveme

First try (in terminal):
gtf 1440 900 60

this will give you an output like

 # 1400x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 104.23 MHz
  Modeline "1400x900_60.00"  104.23  1400 1480 1632 1864  900 901 904 932  -HSync +Vsync

copy-paste this to the end of your  "Monitor"  section

Then find and modify at the bottom of your "Screen" section

 SubSection "Display"
                Depth           24
                Modes           "1440x900_60.00" "1280x1024" "1024x768" "800x600" "640x480"
 EndSubSection

to have your mode in front of the others, like above. Now restart the xserver.

IF this doesnt seem to help at all, install 915resolution

sudo apt-get install 915resolution

and learn how to use it

man 915resolution

if its too complicated just ask again

---

