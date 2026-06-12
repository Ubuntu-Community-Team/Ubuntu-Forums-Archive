---
title: "Americas Army"
date: 2005-08-30
forum: Gaming &amp; Leisure
---

### Post by mrt on 2005-08-30
I've installed it and can open it and can navigate the menus, but when I load a map, it locks up my pc and I have to reboot it.  Even the keyboard doesn't respond (numlock,capslock buttons etc don't light up).

Does anyone know what I should check?  All of the graphics are on the Ultra Low setting and on the lowest resolution.  glxgears reports 3700 fps, which leads me to believe that the game should run fine.

2.4Ghz P4, 512 ram, Nvidia 128MB Geforce4 TI 4200 agp8x, 1.0-7174 drivers

I appreciate any pointers or tips
this is frustrating as hell, quake won't run, ut wont run, trying cube next...

---

### Post by bobmaster on 2005-08-31
The linux version is up to date yet that may be your problem. Just a guess.

---

### Post by rmrf on 2005-08-31
it seems like you have bigger problems then just playing america's army, especially since none of your other games work. have you done anything to your system recently that would warrant odd behavior? maybe a little more information on what setup you are running, your sources.list, etc, would lead someone closer to the fix.

good luck.

---

### Post by mrt on 2005-08-31
haha....cube runs for 15 seconds then locks up hard - ctrl alt bkspc gets me out of it though.  Imagine how I felt for the first 15 seconds, and then the seconds following...

I have not done much to the system, other than I think I installed the nvidia drivers from the nvidia website rather than apt.  you think if I use the version in apt I might have better luck?  I'd be willing to try that.

Is there an easy way I can remove my current nvidia drivers and install the version in apt?  As a last resort, I could reinstall the os if you guys think it would be worth my time.

---

### Post by KingBahamut on 2005-08-31
id think youd have to give the apt drivers a try. 

Nvidia prop drivers can do some crappy stuff I think.

---

### Post by rafakl on 2005-09-04
well, nvidia propietary drivers boosted my computer performance!!!

the default drivers that come with ubuntu (nv i guess), where very slow and crappy.

---

### Post by dducko3 on 2005-09-05
I installed the drivers that are found in apt.. nvidia-glx  and started haveing serious problems.. games would crash... flash animation killing me..   I got the Nvidia drivers and followed the HowTo found on these forums and now it all works good, better even then it ever did on my WinXP install.

---

### Post by rafakl on 2005-09-06
YEHA!!!!

Its good that every day i can boot linux and start my favorite game and see the excellent graphical performance!!!

---

### Post by mrt on 2005-09-15
I just did a fresh reinstall of Hoary.  glxgears (with the drivers from apt) still reports ~3700 fps, but AA still will not run; even at the lowest quality settings.

The menu and initial sounds all load fine, but when I start the Marksmanship training, it all goes to hell.  I can see the guy I'm supposed to walk up to and I can hear the crickets chirping.  If I move my mouse left slightly and wait about 10 seconds, the screen will update.  after about 30 seconds it locks up hard  -the only way to kill AA is to ssh in from another box.

is there anything else I can look at?

---

### Post by AdmiralSenn on 2005-09-15
Not like it matters. AA 2.4 for Linux isn't out yet unless I missed something in the last three days or so, and all the talk in the Linux section of the AA forums is about how there are no 2.3 servers left. Apparently your options are: Use Wine, run it in Windows, run it as 2.3 single player or don't play it.

---

### Post by Alacrity on 2005-09-15
Admiral,

At the fps you are running, it sounds like your Nvidia drivers.  Same here.  I had to go to the nice and comprehensive Ubuntu 5.04 Starter Guide @ ([http://ubuntuguide.org/](http://ubuntuguide.org/).  Follow exactly the Nvidia driver installation instructions.

For me, once Nvidia was running in Ubuntu, then for each Linux game sound was hit or miss.  Had to fiddle in each case.  For AA, I never got around to fixing the sound with 2.3, ran out of time, and went to XP AA 2.4 for a beautiful running game.

But, if you already have sound, I believe with an Nvidia install as per the Ubuntu instructions, you are home free.

Don't forget to add the repositories:

 How to install Graphics Driver (NVIDIA)?

Read General Notes 
Read How to add extra repositories? 
sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable
sudo gedit /usr/share/applications/NVIDIA-Settings.desktopInsert the following lines into the new file 
[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;Save the edited file (sample) 
Read How to restart GNOME without rebooting computer? 
Applications -> System Tools -> NVIDIA Settings 


If done correctly, you should see the single screen graphical NVIDIA screen during bootup.

Good luck.

---

### Post by Seth on 2005-10-29
2.5 is out today, so you should try again :)

---

