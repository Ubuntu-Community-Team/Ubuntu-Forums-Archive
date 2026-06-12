---
title: "Dell E6400 Docking station issues"
date: 2009-07-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ampm24 on 2009-07-08
First off, let me say that I've had great success with 9.04 on my Dell E6400.  Everything worked out of the box.  Even my ATT and Verizon broadband cards worked right off the bat.  Only one small issue is with my docking station at work.  I have a dual monitor setup, one VGA and one DVI.  When I power up docked, I get the boot screen, but as soon as the login screen should come up, the screen goes into power save.  If I open the lid to the laptop, I can login in.  If I use the Nvidia control panel, I can change the display settings to eventually get the displays up.  I enable them both, disable the laptop screen and adjust the resolutions, I can get them up, but it's very unstable.  Locks up 2 out of 3 times, and other times, I can't get the right monitor to be primary.  Other issue, is I can't save the config.  It gives me an error when I try to save to the existing config file.  Any ideas?  This is my first run with Ubuntu in a year so I'm a little rusty.  My only other linux knowledge is with VMware at work.
 
Pete

---

### Post by Diamond.Dave on 2009-07-12
Wow!  I have this same issue - I have an older Dell Latitude D820 with 9.04 - same thing.  works fine in laptop mode.  Put it in the docking station and turn on, I watch the boot all the way up to the password screen and then it goes to power save...

---

### Post by DrBubba on 2009-07-31
Have the same problem on a Latitude E6500.  Everything else works fine.  Running the nVidia X configuration utility shows that it detects the display just fine.  It's wierd because the other virtual terminals are there - I can get VT1 - VT6 just fine and VT 8 shows the system messages also just fine but the monitor doesn't display VT7 which is where gdm is showing the login prompt.  So I've got a nice big monitor for a command line, but no X.

---

### Post by jimic79 on 2009-08-12
I have the exact same problem on my Dell XPS M1710.  I put it in the dock, closed and off, hit the power button on the dock, the DVI monitor powers up, shows the bios, grub, boot process, then as soon as I land on the password screen, the monitor goes into power save mode.

Anyone have any ideas or fixes for this?  There's gotta be a way for ubuntu to use the external video if the lid is closed.

---

### Post by pizza-is-good on 2009-08-12
> **ampm24 said:**
> First off, let me say that I've had great success with 9.04 on my Dell E6400. Everything worked out of the box. Even my ATT and Verizon broadband cards worked right off the bat. Only one small issue is with my docking station at work. I have a dual monitor setup, one VGA and one DVI. When I power up docked, I get the boot screen, but as soon as the login screen should come up, the screen goes into power save. If I open the lid to the laptop, I can login in. If I use the Nvidia control panel, I can change the display settings to eventually get the displays up. I enable them both, disable the laptop screen and adjust the resolutions, I can get them up, but it's very unstable. Locks up 2 out of 3 times, and other times, I can't get the right monitor to be primary. Other issue, is I can't save the config. It gives me an error when I try to save to the existing config file. Any ideas? This is my first run with Ubuntu in a year so I'm a little rusty. My only other linux knowledge is with VMware at work.
 
Pete
 
Is this problem happening in Ubuntu or Windows?
 
Also, do you have the extended docking staion or the small one? I have the small one, and if you do as well, I think I know what the problem might be, but let me know.
 
Also, you are invited to join the E-Laptop group. Follow the link in my signature.

---

### Post by HotShotDJ on 2009-08-13
On my Dell E1505 (which I believe is exactly the same thing as the E6400) I had to go to the Power Manager preferences (left-click the battery icon in the system tray), go to the "On AC Power" tab and then under "When laptop lid is closed" select "Do nothing." I believe the default is "blank screen" which is why your external monitor goes right to powersave mode when GDM (the login prompt)comes up

If you don't have the Power Manager in your system tray (sometimes it is set to only come up when on battery power), you can start it from System -> Preferences -> Power Manager)

With that setting, I have had no trouble keeping the laptop lid closed when using an external monitor with Ubuntu. I have System -> Preferences -> Display set to turn off the laptop display when an external monitor is present (you must have the external dispay(s) plugged-in to configure that part, otherwise it just shows you the laptop display with the "on/off" radio buttons grayed out).  I don't know how the built-in display settings app interacts with an NVidia graphics card, so that part might have to be done through the NVidia Control Panel on your system.  I've also used "xrandr" through a terminal to control displays, although I haven't had to resort to that since Ubuntu 7.10.

---

### Post by grigglestone on 2010-03-01
> **HotShotDJ said:**
> "When laptop lid is closed" select "Do nothing."

Hmmm .. using 9.10 on a Dell E6500/NVIDIA I don't see this option.

Any thoughts .. has this option been taken away in 9.10?

thanks for any input

---

### Post by moosekaka on 2010-03-24
> **grigglestone said:**
> Hmmm .. using 9.10 on a Dell E6500/NVIDIA I don't see this option.

Any thoughts .. has this option been taken away in 9.10?

thanks for any input

this is nuts...three weeks and no resolution yet...indeed the option for "do nothing" has been regressed in 9.1....i ended up installing 8.04 as that one allowed me to dock my inspiron 6400 with a LG 23" LCD with 1680x1050 res...

im new to ubuntu...but it seems to me that ubuntu makes you jump through hoops to get simple things like monitors to work rather than let you concentrate on running the really cool stuff in linux!

---

### Post by jher on 2010-04-06
I've had similar problems with my E6400 but I solved them by disabling the "Seiko" display in the Nvidia X Server Settings.  

I'm running 9.10 with dual 24" dell screens via VGA and DisplayLink.

My xorg.conf is as follows:

> 
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Mon Nov  3 08:46:46 UTC 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 2407WFP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 160M"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-2: 1920x1200_60 +0+0, DFP-4: 1920x1200_60 +1920+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


---

### Post by mtiday on 2010-04-08
[SIZE=4]I had a similar issue with my Precision M2300. Connect to Dock, turn laptop on, screen blanked out at login. I followed instructions on post [http://ubuntuforums.org/showthread.php?t=1319921](http://ubuntuforums.org/showthread.php?t=1319921) to "Do Nothing" when lid was closed. That worked , but same issue at login screen. I removed the proprietary Nvidia driver. Works like a champ now! The generic video drivers worked without any config setup. If Nvidia can't fix the bugs they need to open source their driver![/SIZE]

---

