---
title: "Desktop (NOT laptop) LCD brightness control??"
date: 2007-07-12
forum: Desktop Environments
---

### Post by amohanty on 2007-07-12
Hi All,

I was wondering if there was any way to set or control the brightness of my LCD hooked up to my desktop, similar to the laptop brightness control applet. I have an ati radeon with fglrx.  

Thanks.
AM

---

### Post by tgm4883 on 2007-07-12
Isn't there a button on your monitor for this?

---

### Post by amohanty on 2007-07-12
Yes, however, I would prefer not having to:

1. press menu
2. press up * 2
3. press select
4. press down/up * x (to control brightness)
5. press menu again to turn the thing off

I guess I am just being lazy :)

AM

---

### Post by afeasfaerw23231233 on 2007-10-25
i decide to bump this thread as i have the same question. my lcd screen control panel has some problem. the left arrow key doesn't work. so it is a big trouble whenever i need to adjust brightness or contrast. when i was using xp, i can adjust the brightness using the intel graphic driver utility (i forget the exactly name. it is an applet called something like ''intel graphic media accelerator'' in the task bar === i am using i845G intergrated chipset) my another old box also has this similarfunction when running xp (PIII, SiS630 intergrated chipset). there's an graphic card applet in the task bar which provide ''contrast, brightness, rotation, gamma ray.....'' for me to adjust. however i cannnot do this in ubuntu

---

### Post by afeasfaerw23231233 on 2007-10-29
BuMp

---

### Post by afeasfaerw23231233 on 2007-11-01
bump... i find that i can do brightness control on xubuntu 7.10 by right-click on the desktop and choose ..(i do not remember the name) how to do this on ubuntu?

---

### Post by dmig on 2007-11-21
in ubuntu you need to install gddccontrol package for that.
but i found out, that my sony sdm-s74 monitor can't be controlled when connected via dvi cable :(

---

### Post by afeasfaerw23231233 on 2007-11-21
thanks for reply anyway, i may try it later

---

### Post by deepaknr on 2008-01-10
I have a Acer Aspire 5710G, which came up with ATI Radeon HD2300 graphics card. Initially the brightness control worked fine, but after few reboots it stopped working. The brightness was full at 100%, later I loaded default BIOS settings, this made the brightness to go full LOW.

I used this command echo -n 50 > /proc/acpi/video/VGA/LCD/brightness as root, the brightness came to 50%. After this, the functional brightness key started to work properly.

I am just waiting how long can the function key work properly.

Kindly let me know if there is a permanent solution to this.

Thanks

---

### Post by rosegarden78 on 2008-01-19
Try typing this command in a terminal
 
 xgamma -gamma 0.75
 
 I have posted my own solution here:
 
 [http://ubuntuforums.org/showthread.php?p=4168042#post4168042](http://ubuntuforums.org/showthread.php?p=4168042#post4168042)

---

### Post by rosegarden78 on 2008-01-19
My black screen was too bright and had horizontal stripes of the darkest gray.  Although my keyboard has brightness controls *painted* on top,  Fn+Up or Fn+Dn key combinations are not detected by keyboard shortcuts in GNOME, KDE or XFCE on my Dell Inspiron 1200 laptop.  But Ctrl+Up/Dn *is* detected and just the same as a Fn key.  You may consider adding *other* keyboard shortcuts that may be missing.  Keep in mind the "xgamma -gamma 1.0 1.0 1.0" numbers refer to RGB channels.  Once set at gamma 0.75 your black screen should once again be solid black.

Advanced Solution
------------------------------
Obtain a Macro program to record the mouse movements and keys you used to activate your device.  Assign a keyboard shortcut to call the macro quickly.

Kubuntu + Ubuntu Solution
--------------------------------------------
Same principle as Xubuntu but you need to find out how to add custom groups and commands to your Keyboard Shortcut Menu.  It should be located under System Setting or Preferences or Control Panel.  Second to need something to call like a shell script or an activation program.  In this case it's a command-line program, xgamma, so we need to make a shell script with headers, make it executable and call it with bash.  If the program is a one-click deal you can add it to Session Manager - Startup Programs.

Xubuntu Solution
----------------------------
## Always use the latest distro - Gutsy or Hardy 7.10+.
## Before you begin, press Alt-F2 then type "**xgamma -gamma 0.75**"
## If that fails you need to install xgamma from Synapic or Add/Remove Programs or aptitude or etc.

Phase 2 - Assign Keyboard Shortcuts to Shell Scripts
----------------------------------------------------------------------------------
# Note you must use full path /home/Startup/...
1) Right click Desktop and select Settings - Keyboard Shortcuts or use XFCE Menu from Program Launcher
2) Add a new group called Custom
3) Add a new item
4) Where it says command type "bash /home/Startup/GammaC-up"
5) When it says choose key press Ctrl-Up
6) Add a new item
7) Where it says command type "bash /home/Startup/GammaC-dn"
8) When it says choose key press Ctrl-Dn
Now you finished configuring the keyboard shortcuts you need to write a shell script:

Phase 1 - Write Shell Scripts
---------------------------------------------
1) Navigate to your /home or ~/ folder
2) Create a folder called "Startup"
3) Navigate to the Startup folder
4) Launch a text editor, or create new file
5)  In the text editor, or file, type the lines below:

#!/bin/sh
# Shell Script I. - GammaC-up
# ---------------------------------------------
xgamma -gamma 1.0 1.0 1.0

6) Save this file as **GammaC-up**, or rename it
7) Create a new document or file
8) In the text editor, or file, type the lines below:

#!/bin/sh
# Shell Script II. - GammaC-dn
# ----------------------------------------------
xgamma -gamma 0.75 0.75 0.75

9) Save this file as **GammaC-dn**, or rename it

You have finished writing your shell scripts now you need to do one thing:

Phase III. - Make Scripts Executable
-------------------------------------------------------
1) Right click file Properties - Permissions and make executable for both scripts
2) If that doesn't work for some reason you can also Press Alt-F2 then type "**chmod +x /home/Startup/GammaC-up**" and then "**chmod +x /home/Startup/GammaC-dn**"

You have completed Phase One.  Your keyboard shortcuts are calling bash, the shell interpretor, which uses the script that uses xgamma.  My previous post mentioned changing xorg.conf but this ultimately failed to correct the gamma.

Phase IV. - Automatic Gamma Correction on Login
---------------------------------------------------------------------------------
If you want Gamma Correction after you login you need to use Preferences - Sessions Manager - Startup.  Just remember when you add the command line it has to be a shell script with the proper header like before.

Startup Program
---------------------------
bash /home/Startup/GammaC-dn

Although you cannot increment brightness this way, I find that my LCD panel contains 86 pixels per inch as stated (I measured it with kruler myself) & responds best (pure black screen) at -gamma 0.75.  One number is sufficient if you are adjusting all channels.  You may experiment further but on standard LCD panels 86 ppi at gamma 0.75 works best.

P.S.  The fastest system is XFCE - you may also try adding it from Synaptic. Then select Session Type when you log in. Once Xubuntu has started try pressing Alt-F2 then type "nautilus". This will give you many features familiar in GNOME. I'm experimenting with this because the XFCE desktop seems to be the cleanest and fastest of them all. And I like the features of Nautilus.  Just remember to add "XFCE Menu" to your launcher because Nautilus replaces the right click menu with document creation tools. Keep GNOME and KDE to satisfy the dependencies.

---

### Post by Grinning Fool on 2008-01-27
deepaknr -- thanks for htat, I've been looking all over to find that little tidbit of info you posted. Of course, it would be better to have the Fn keys working, but at least what you gave lets me change the brightness; better than I could do before :) 

> **rosegarden78 said:**
> Try typing this command in a terminal
 
 xgamma -gamma 0.75
 
 I have posted my own solution here:
 
 [http://ubuntuforums.org/showthread.php?p=4168042#post4168042](http://ubuntuforums.org/showthread.php?p=4168042#post4168042)

That's not really the same thing.  That's just increasing the color saturation; and not actually brightening the LCD's backlight, resulting in a significant difference in appearance.

---

