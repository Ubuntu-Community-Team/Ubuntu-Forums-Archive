---
title: "Display Resolution on AMD A10"
date: 2013-04-17
forum: Desktop Environments
---

### Post by Ciaraldi on 2013-04-17
I have been using Linux for 20 years and X-Windows for 30 years (no kididng!) and I still have trouble sometimes with setting display resolution.
I have a new machine with an AMD A10-5800K processor, which includes Radeon 7660 graphics. My monitor is an Acer X221W, with native
resolution of 1680x1050. OS is Xubuntu, which is Ubuntu 12.04 LTS with Xfce. The monitor is plugged into the VGA port through a KVM switch.

When I boot up with no xorg.conf file, it comes up with 1600x1200 resolution. Running xrandr gives this output:
------
Screen 0: minimum 320 x 200, current 1600 x 1200, maximum 1600 x 1600
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
DFP3 disconnected (normal left inverted right x axis y axis)
DFP4 disconnected (normal left inverted right x axis y axis)
DFP5 disconnected (normal left inverted right x axis y axis)
CRT1 connected 1600x1200+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1600x1200      60.0*+
   1600x1050      60.0  
   1400x1050      60.0  
   1600x900       60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1366x768       59.8  
   1360x768       60.0  
   1280x800       59.8  
   1152x864       60.0  
   1280x768       59.9  
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   720x480        60.0  
   640x480        59.9  
------
Incidentally, I was able to create the 1600x1050 resolution using "xrandr --newmode".

All the utilities that let me choose resolution, including gvidm and amdcccle, only allow the modes listed above.

Running "get-edid" says that it cannot get the EDID info from the monitor.

Some of the things I have tried so far:
1) Creating a default xorg.conf using "aticonfig --initial", then adding a modeline for 1680x1050 and setting this as the 
"Preferred Mode". No effect.
2) Trying to add a 1680x1050 mode with xrandr. Got an "invalid parameter" message. I suspect this is because the maximum screen size
is 16001600. I don"t know  how to change the maximum size. 

Any ideas on how I can fix this? Thanks in advance.

---

### Post by Ciaraldi on 2013-04-18
I forgot to mention that running "fglrxinfo" gives this:

display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7660D
OpenGL version string: 4.2.11627 Compatibility Profile Context

----------
I have also attached the result of running "fglrxinfo -v".
---------
Running "lsmod  | grep fgl" yield this:

fglrx                3264017  84

---

### Post by Ciaraldi on 2013-04-20
I see that 70 people have viewed this thread, but nobody has come up with an answer yet.
I am attaching some more informatin:
-- My current xorg.conf
-- /var/log/Xorg.0.log -- this has some messages which might help pinpoint the problem.
-- The output of "xrandr --verbose"

Thanks in advance!

---

### Post by Ciaraldi on 2013-04-21
Well, I got it working!

After doing lots of Googling I figured out that I could extract the EDID information by plugging the monitor into another Linux machine.
I did that with one running Fedora 18 and gave this command:

   sudo monitor-get-edid > x221w.edid

This retrieved the info from the monitor and saved it in binary form. IF I had been running Ubuntu on that other machine the command would have been "get-edid" instead of "monitor-get-edid".

Then I FTP'd the file back to the Xubuntu box and saved it as /etc/ati/crt1.EDID ; then I rebuilt the xorg.conf file with this command:

  sudo aticonfig --initial

I rebooted and everything is running fine now. I am attaching the EDID file in case anyone needs it, and will also besubmitting it to the EDID databse on quantumdata.com . Note that I had to gzip the file so I could upload it to this site

---

