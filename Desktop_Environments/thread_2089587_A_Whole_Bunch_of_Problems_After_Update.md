---
title: "A Whole Bunch of Problems After Update"
date: 2012-11-29
forum: Desktop Environments
---

### Post by mdmcaf on 2012-11-29
Hey y'all~

Ever since the last round of updates (which included an x.org server update) my system has been acting screwy. My specs are:

Asus P8P67 Motherboard
Intel Core i7 2600 @ 3.4GHz
16GB RAM
XFX AMD Radeon HD 6870 1GB
OCZ Agility 3 120GB SSD (with the OS on it)
Western Digital Caviar Black 1TB HDD (split into 2 partitions, one Windows 7 Ultimate partition and another 500GB partition for data on the Linux machine)
External USB 3.0 3TB HDD (I think that it's Western Digital but I don't remember off the top of my head).

Anyways. My problems are as follows:

1. I have 2 monitors on this setup, a 20" Dell Ultrasharp running at 1680x1050 and a 24" Dell Professional running at 1920x1080. Every time I boot into the system (and it doesn't matter if I log out and log back on or do a reboot/cold start) the resolution of the 24" monitor is 1680x1050. I have to go into AMD Catalyst Control Center and change the resolution of the monitor manually. It didn't do this before the last round of updates last week.

2. A couple of unwanted programs open when I log back into the machine. These programs are: KDirStat and an extra instance of xclock (for a total of 2 instances of xclock). I've tried clearing out my sessions cache and saving a new session via the GUI but that doesn't change anything.

3. Alt-F2 doesn't work anymore. I'll press those keys to get the application launcher and nothing happens. The only work around I've found is to go to the Application Finder and search for the command that I want to enter (but not all of them are listed).

4. I can't change the Window Manager Theme or the Style (under Appearance). I've tried rebooting after selecting them and it doesn't change, I've also tried clearing the session cache and saving a new session and the changes aren't present.

5. I can't change the system icons. They're stuck at some really ugly ones and it's very annoying. Again, I've tried clearing the session cache and saving a new session, but the changes aren't showing up. One interesting thing to note is that when I first log in to the machine the external drives (which haven't been mounted yet) show the correct icon theme, but when I move the mouse over them they change to the ugly icons that I don't want.

6. The eyes-plugin that I've installed doesn't remember the last configuration that I had it set to. It defaults to "Tango" instead of "Default" which is what I prefer.

I've been able to determine (in my opinion, at least) that it's an update which has broken my install. I've tried re-installing Xubuntu to no avail, it'll work at first...but as soon as I install updates to it the installation will break. I've also tried restoring to an image that I made about a month ago. When I restore the image the system is working like it should but as soon as updates get installed the system is broken again. There are hundreds of updates so it's not really possible to try them one by one until I notice the one that breaks it.

Any help would be greatly appreciated on any of the issues that I've noticed. I've been a Linux user for a number of years so I'm fairly proficient at the command line and what not, but these problems are new to me so it'd be useful to get specific commands to try as I'm not the most advanced user out there.

Thanks!

---

### Post by amethyst igor on 2012-11-30
> **mdmcaf said:**
> Hey y'all~

Ever since the last round of updates (which included an x.org server update) my system has been acting screwy. My specs are:

Asus P8P67 Motherboard
Intel Core i7 2600 @ 3.4GHz
16GB RAM
XFX AMD Radeon HD 6870 1GB
OCZ Agility 3 120GB SSD (with the OS on it)
Western Digital Caviar Black 1TB HDD (split into 2 partitions, one Windows 7 Ultimate partition and another 500GB partition for data on the Linux machine)
External USB 3.0 3TB HDD (I think that it's Western Digital but I don't remember off the top of my head).

Anyways. My problems are as follows:

1. I have 2 monitors on this setup, a 20" Dell Ultrasharp running at 1680x1050 and a 24" Dell Professional running at 1920x1080. Every time I boot into the system (and it doesn't matter if I log out and log back on or do a reboot/cold start) the resolution of the 24" monitor is 1680x1050. I have to go into AMD Catalyst Control Center and change the resolution of the monitor manually. It didn't do this before the last round of updates last week.


I had a similar issue in Linux Mint Mate. 

Here is what I noticed: when the monitor is turned off during system boot, the resolution gets screwed up. If the monitor is turned on during boot, somehow the system reads info from the monitor itself and the correct resolution is achieved. So I learned to always turn the monitor on first, then the computer.

But you are running two monitors, which complicates matters. Since the problems arose after the update, I am willing to wager the update hosed an important config file. Have you checked out the contents of /etc/X11/xorg.conf recently, by any chance? Also check the guide over at [https://wiki.archlinux.org/index.php/AMD_Catalyst#Configuring_X](https://wiki.archlinux.org/index.php/AMD_Catalyst#Configuring_X) because it is totally awesome and destroys all other Catalyst guides in the Universe.

---

### Post by mdmcaf on 2012-12-01
Thanks for the lead. I haven't looked at the X.org configuration site yet (though I certainly intend to), but I did take a glance at my xorg.conf file and discovered that there's an extra monitor listed in it which shouldn't be there.

I tried to delete the section of the config file with the extra monitor but when I log out and log back in to my machine I still have the same problem. I tried 3 times and got the same result each time, and I made sure that I saved it correctly. I tried editing it from vi as well as from gedit and got the same result.

I was also messing around with the Catalyst Control Center settings and noticed that when I changed the multiple display mode to "Single display Desktop (multi-desktop" a few of the problems went away - the icons returned to their usual theme, I was able to change themes and styles, and the resolution wasn't messed up at log in. I don't want to run in this mode as I'd like to be able to move windows from one monitor to the other...but perhaps a reinstallation of the drivers is needed?

---

### Post by mdmcaf on 2012-12-01
So I believe that I figured out at least some of the problems:

I restored to my backup image from ~1 month ago and started doing the usual cleaning that needed to be done since with that image I was running low on disk space on the root partition. While I was deleting old kernels I noticed a message that said something along the lines of "this kernel is still active" and then I noticed that a message flashed by about fglrx. I don't know exactly what it said as it went by too quickly for me to read. But I rebooted to see if my deleting the old kernels had anything to do with it; sure enough, when I logged back on again everything was screwed up. I hadn't installed any updates at that point so I'm certain that the updates didn't have anything to do with it.

I'm doing a large file transfer with the computer right now, but I intend to install the updates that need to be installed to see if it breaks, I'm confident that it won't since it appears as though I've discovered the root (heh) of the problem.

The problems that remain are:

1. when logging in there are still a couple of unwanted apps that start up (kdirstat and a random number of extra instances of xclock).

2. the windows aren't where I last left them...they're scattered all over the place.

3. the eyes-plugin for one of the panels defaults to the wrong set of eyes - it's tango instead of default, and I want it at default...the preference is just never saved and when I log back into the system it's gone back to tango again.

That's it though, yay progress!

---

### Post by mdmcaf on 2012-12-01
Nevermind. It's still broken. I restarted and it's back to broken. I also tried doing a restore to the backup and then configuring the monitors (but nothing else) and when I rebooted it was broken.


Any thoughts, anyone?

---

### Post by amethyst igor on 2012-12-02
> **mdmcaf said:**
> Nevermind. It's still broken. I restarted and it's back to broken. I also tried doing a restore to the backup and then configuring the monitors (but nothing else) and when I rebooted it was broken.


Any thoughts, anyone?

I do not know about using multiple monitors. That is something I saw people in the corporate world doing, but it's not my bag. My smallest monitor is 24" and I haven't felt a need for a second monitor. But to each his own. What I do know is that installing the ATI proprietary driver is no trivial matter. It is easy to screw up. Installation is far from simple, and absolutely requires command-line interface, as per the Arch Linux guidelines. If you install via Ubuntu's software center or Linux Mint (Debian) Synaptic, here's what will happen. You will see Catalyst Control Center. You will see fglrx. You will not get any gpu acceleration. It is like you installed nothing. You have to run the commands specified on the Arch Linux wiki. You also have to configure the X11 config file as per the Arch Linux wiki. I learned this the hard way. Am I going to buy another AMD chip? No. Another ATI card? No. From now on, Intel / Nvidia all the way, all the time.

Whether fglrx / X11 has something to do with your specific issue, I don't know quite honestly, again because my knowledge of multiple monitors is zilch, but I'm just sharing what I do know. Read the Arch Linux wiki link, it is 100% required reading for anyone that uses ATI graphics under Linux. And no, I don't use Arch Linux, but they just happen to have an excellent documentation writer somewhere in their userbase...I don't know who it is...somebody with good brains. Too bad all the distros can't come together and merge and share the talent but at least a lot of the knowledge is transferable.

---

### Post by mdmcaf on 2012-12-02
> **amethyst igor said:**
> I do not know about using multiple monitors. That is something I saw people in the corporate world doing, but it's not my bag. My smallest monitor is 24" and I haven't felt a need for a second monitor. But to each his own. What I do know is that installing the ATI proprietary driver is no trivial matter. It is easy to screw up. Installation is far from simple, and absolutely requires command-line interface, as per the Arch Linux guidelines. If you install via Ubuntu's software center or Linux Mint (Debian) Synaptic, here's what will happen. You will see Catalyst Control Center. You will see fglrx. You will not get any gpu acceleration. It is like you installed nothing. You have to run the commands specified on the Arch Linux wiki. You also have to configure the X11 config file as per the Arch Linux wiki. I learned this the hard way. Am I going to buy another AMD chip? No. Another ATI card? No. From now on, Intel / Nvidia all the way, all the time.

Whether fglrx / X11 has something to do with your specific issue, I don't know quite honestly, again because my knowledge of multiple monitors is zilch, but I'm just sharing what I do know. Read the Arch Linux wiki link, it is 100% required reading for anyone that uses ATI graphics under Linux. And no, I don't use Arch Linux, but they just happen to have an excellent documentation writer somewhere in their userbase...I don't know who it is...somebody with good brains. Too bad all the distros can't come together and merge and share the talent but at least a lot of the knowledge is transferable.


That's interesting. I've been using AMD video cards for years without any issues like this; I've always used the Catalyst Control Center and the only issue that I've come across is that I have to access it through the terminal instead of just clicking the icon from the applications menu. But perhaps it's changed recently (well...it obviously has changed recently) and it's time for me to do some real Linux configuration.

I think that you're right about fglrx having something to do with it.

I'll check out the wiki on configuring the monitors/video card and get back to you. I've just been lazy and trying to come up with a quick fix to my problem...which has just ended up wasting more time than I have to waste.

Do you think that if I sort out of the problem with fglrx/x11 that it'll improve the situation with extra applications opening and the eyes-plugin defaulting to the wrong settings, or is that unrelated?

Thanks for your help!

---

### Post by mdmcaf on 2012-12-03
So I followed the directions on the wiki and it hasn't improved anything. I'm attaching my xorg.conf file in case there's something that I did wrong.

```

Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "0-DFP11"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1680x1050"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1920 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-DFP10"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1080"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
	Option	    "OverlayOnCRTC2" "1"
	Option	    "Monitor-DFP11" "0-DFP11"
	Option	    "Monitor-DFP10" "0-DFP10"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   3600 1920
		Depth     24
	EndSubSection
EndSection

```

---

### Post by amethyst igor on 2012-12-03
I got some new (and I think better) information for your problem over [here]("http://forums.linuxmint.com/viewtopic.php?f=29&t=115308"). Check it out.

---

