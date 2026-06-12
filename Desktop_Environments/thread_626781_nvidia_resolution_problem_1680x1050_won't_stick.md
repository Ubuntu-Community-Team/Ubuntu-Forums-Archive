---
title: "nvidia resolution problem 1680x1050 won't stick"
date: 2007-11-29
forum: Desktop Environments
---

### Post by shawnyar217 on 2007-11-29
Hi,

How can I force Xorg to ALWAYS use the 1680x1050@60 resolution that I know is correct for my system?

The nvidia-settings app correctly detects my graphics hardware: a GeForce 7800 GS and an Acer X221W 1680x1050 60hz widescreen LCD monitor.

By playing around with various settings and xorg.conf I can sometimes get it to switch into the correct resolution and it looks great.  But eventually it falls back to 1280x1024 either after a reboot or after I use my monitor switch to switch to another computer and then come back.

Also, even when 1680x1050 is working, I can't get the new desktop effects to work.  This is a modern nvidia card with strong 3D features, though it is an AGP card.  I do get the nvidia splash screen when I boot up or when I switch users.

I've also had troubles with the login screen resolution being 1280x1024 even though the logged-in desktop resolution is the correct 1680x1050.  How can I make Ubuntu ALWAYS use 1680x1050?

Restricted drivers manager says "NVIDIA accelerated graphics driver (latest cards)" and Enabled and In Use are checked.

Advanced, Screens and Graphics Preferences says "nvidia" driver under "Graphcs Card" and "Acer X221W (widescreen) 1680x1050 50hz" under "Screen".  Strangely, there are options for 50hz, 51hz, and 52hz, but not for the 60hz that I need.

Preferences, Screen Resolution says "1680x1050" and "50 hz".  It also shows the 51hz and 52hz options.

This is all while my monitor itself reports that it is actually displaying 1280x1024@60hz.

Thanks,

Shawn Yarbrough

---

### Post by shawnyar217 on 2007-11-29
Forgot to mention: this is on Ubuntu 7.10.

---

### Post by dabl on 2007-11-29
> **shawnyar217 said:**
> Hi,

How can I force Xorg to ALWAYS use the 1680x1050@60 resolution that I know is correct for my system?



Open a console window, and enter ```
sudo nvidia-settings
``` to run the Nvidia settings utility in Super User mode.

Click the "X Server Configuration" tab, then click the "detect displays" button, then set your resolution to whatever you want for the default.  I recommend you leave the refresh set to "Auto".  When you have it the way you want it, click the "Save to X Configuration File" button in the lower right, put an "x" in "Merge", and then "Save" and then quit.

Restart the X server with Ctrl-Alt-Backspace and you should be able to log in to your chosen default display.

:guitar:

---

### Post by shawnyar217 on 2007-11-29
I've done that before without much luck, but I followed your instructions exactly just to be sure.

The ctrl-alt-backspace showed the nvidia splash screen and let me log in again.  All my previously open windows were gone.  My monitor's OSD still says 1280x1024.

---

### Post by shawnyar217 on 2007-11-29
As I mentioned in the original post, nvidia-settings correctly identifies my hardware, ideal resolution and refresh rate.

Then the Ubuntu configuration tools get the refresh rate wrong, suggesting rates of 50hz, 51hz, and 52hz when the LCD screen schould be running at 60hz.  Then the monitor itself reports that the signal resolution is only 1280x1024.  What the heck is going on?

How I can I force Ubuntu to run at the res and refresh that I know is correct?  Even when I've temporarily convienced Ubuntu to run in 1680x1050, the login screen was usually at 1280x1024 until I logged in.  This suggests to me that there is a config file other than xorg.conf somewhere that I am missing.

---

### Post by Tex Arcana on 2007-11-29
subscribing... I just registered to find out the fix for mine (FX5950 Ultra with a Westinghouse 22" 1680x1050 LCD), except mine won't get out of 1024x780.  :(

---

### Post by shawnyar217 on 2007-11-29
[found some more info online but not sure what to do with it yet]

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg534464.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg534464.html)

Both displayconfig-gtk and gnome-display-properties show incorrect
refresh rate options.

They show 50 and 51 instead of sane options such as 60 and 75... my LCD
panel says it's using 75 but displayconfig-gtk and gnome-display-
properties show it as 50 (i don't think there is a 50 for this monitor)

I have tried many xorg.conf changes, but it appears displayconfig-gtk
and gnome-display-properties do not use xorg.conf to lookup the refresh
rate options...

Basically I would like to know where displayconfig-gtk and gnome-
display-properties store their settings so I can manually define the
correct options.

---

### Post by 81wtbvi02 on 2007-11-29
I had a similar problem, though I have a different video card.  My login screen was at the desired resolution, as was the desktop if I logged in as root, but my user login was at a lower resolution.  I would have to switch it every time I logged in.

I was poking around and found "Applications>System Tools>Configuration Editor", then went to "desktop>gnome>screen>default>0" and entered "60" in the rate key and "1680x1050" in the resolution key.  So far, this seems to have fixed the problem.

Interestingly, when running Windows XP (I have a dual-boot setup) my ancient video card can't output 1680x1050, but it can in Ubuntu 7.10.  If I can get my sound recording to work consistently, I may be able to dump XP entirely!

---

### Post by shawnyar217 on 2007-11-29
OK apparently there are multiple problems at work here, but I found a solution to one of the problems for nvidia cards:

In short, to fix the weird 50hz, 51hz, etc., refresh rates in your various Ubuntu/GTK system preferences, edit your /etc/X11/xorg.conf file, find the Device section for your video card, and add the following line into there:

    Option         "DynamicTwinView" "False"

This is apparently an nvidia-only issue.  The line above fixes the issue, but at the cost of disabling the "X Server Display Configuration" page in the nvidia-settings program.  If you have to, use nvidia-settings once to generate your xorg.conf file, then add the line above to that file and nvidia-settings won't be able to generate xorg.conf files anymore.  But your refresh rates will be fixed.

See also:
[http://www.nvnews.net/vbulletin/showthread.php?t=96182&highlight=refresh+rate](http://www.nvnews.net/vbulletin/showthread.php?t=96182&highlight=refresh+rate)
[http://ubuntuforums.org/showthread.php?p=1557092](http://ubuntuforums.org/showthread.php?p=1557092)

---

### Post by shawnyar217 on 2007-11-29
Now get this: I'm using the Switch User option from Ubuntu's Shutdown menu to restart X over and over and over.  And each time X restarts, the resolution is unpredictably either 1280x1024 or 1680x1050.

I'm not touching any configuration settings or files in between restarts.  Some of the time X arbitrarily decides to give me the wrong resolution.  Sometimes the login screen is correct but my logged-in desktop is wrong.  Sometimes the reverse.  Sometimes both are correct.

---

### Post by shawnyar217 on 2007-11-30
> **81wtbvi02 said:**
> I was poking around and found "Applications>System Tools>Configuration Editor",

Where do you get the Configuration Editor from?  My "Applications>System Tools" menu doesn't have that on it.

---

### Post by 81wtbvi02 on 2007-11-30
It must be enabled in "System>Preferences>Main Menu>Applications>System Tools".  Check the box in the "Show" column.

---

