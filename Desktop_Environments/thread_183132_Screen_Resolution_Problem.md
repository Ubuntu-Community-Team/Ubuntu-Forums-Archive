---
title: "Screen Resolution Problem"
date: 2006-05-27
forum: Desktop Environments
---

### Post by the_witch_king on 2006-05-27
Er..Hi...This is my first post. I am a linux newbie. I have been having problems with my screen resolution. It keeps changing randomly. Sometimes it is 800x600 and is the only option available, i was also having problems with my keyboard multimedia keys and was going through a thread which asked me to press the keys in a "real console"( i have no ieea what that is) , so i press Ctrl+Alt+F1 and i get a text screen. i have no idea how to revert back to the Graphical mode , so i restart my computer and i find that the resolution is 1280x1024 with four other options, though there is only one option available for the refresh rate. Can i have a permanent solution to this problem. My monitor is Samsung Syncmaster 793DF and my motherboard is Intel915GVA if it is going to help in anyway.

---

### Post by Denis on 2006-05-27
To get back to the Graphical mode: press Ctrl-Alt-F7. Numbers 1-6 are virtual terminals. 

About your resolution problem: you can set up the resolutions manually. 

Open up a terminal and type: 
sudo gedit /etc/X11/xorg.conf

Enter the password and gedit will open xorg.conf, a config file. 

Look for Section "Screen". It wil contain some lines like these: 
```

	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection

```
You probably want to add some of the "Modes" (resolutions) I mention here. Add them for each "Depth", so they are available for all color depths. 

Save the file and do a reboot to make sure it works. 

If your problem with refresh rates isn't solved, you can add these lines in the "Monitor" section of the same file: 
```

HorizSync	28-92
VertRefresh	43-60

```
But you will have to look up those values for your monitor!!

I hope this helps.

---

### Post by mad_willsy on 2006-05-29
Horray, this works for me, excellent.

---

### Post by treskjegg on 2006-05-29
Hi

I'm having the same problem right now...  can't get the resolution any higher than 1024x768.
Tried to add "1920x1200" on all depths, but still no go.

I took a clean install of ubuntu today, and now the resolution is stuck at 1024.  Worked with 1920x1200 before, and I followed the same instructions.

Any ideas? (and I am a complete newbie, thanks)


edit: got a Dell Inspiron 9400, WUXGA (1920 x 1200)

---

### Post by turbojugend_gr on 2006-05-29
Well while you are in ubuntu do the following:

Press CTRL + ALT + BACKSPACE. This should restart the X -server and get you to Log in screen.

Following you should press CTRL + ALT + F1. This should get you in a Terminal (while the Gnome and the X-server.org are closed as we need them to).

Then type:```
sudo dpkg-reconfigure xserver-xorg
```this should get you to reconfigure the Xorg (by the way this is the window manager). 

Nothing tricky in this procedure just do your thing it is really simple, just remember to PRESS THE SPACEBAR for those resolutions you wish to be able to use. Many users don't do so!!!! Press the SPACEBAR to get them looking like the 640x480 or 1024x768 options. You should be ok after this.

Don't diheartened by the leangth of my help note.1st I tend to say much. 2nd I prefer you to know why you do each step so you can help others when asked... "Don't feed one with your fish, teach him how to catch one!"

---

### Post by spira_mirabilis on 2006-05-29
I am also still having this problem with the Inspiron 9400, despite trying many suggestions, including 915 resolution and xorg.conf editing...also did the dpkg reconfigure, and selected 1900x1200, this resolution shows in the xorg.conf, but still I cannot use this resolution...

Here is the section of the xorg.conf:
```

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1440" "1920x1200" "1440x900"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1440" "1920x1200" "1440x900"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1440" "1920x1200" "1440x900"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1440" "1920x1200" "1440x900"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1440" "1920x1200" "1440x900"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1920x1200" "1440x900"
	EndSubSection
EndSection
```

---

### Post by turbojugend_gr on 2006-05-30
[QUOTE=spira_mirabilis]I am also still having this problem with the Inspiron 9400, despite trying many suggestions, including 915 resolution and xorg.conf editing...also did the dpkg reconfigure, and selected 1900x1200, this resolution shows in the xorg.conf, but still I cannot use this resolution...

Here is the section of the xorg.conf:
```

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1440" "1920x1200" "1440x900"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1440" "1920x1200" "1440x900"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1440" "1920x1200" "1440x900"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1440" "1920x1200" "1440x900"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1440" "1920x1200" "1440x900"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1920x1200" "1440x900"
	EndSubSection
EndSection
```[/QUOTE]


Have you installed the drivers for your VGA??? VESA drivers or are not enough to give such resolutions. Such as in windows, you got to install the drivers to get your card's potential. Search this forums to find a way to get your intel card working perfectly...

---

### Post by spira_mirabilis on 2006-05-30
I am using the i810 driver, the chipset is the intel 950. Do I need to install a custom driver? From what I understand,there isn't a specific driver for the 950 yet.

---

### Post by fossatig on 2006-05-31
Hi Spira,
I have just come across a similar issue with a friend laptop (DELL Inspiron E1405).
Xorg does not seem to like something, and it is possible that it boils down to
the 950 GMA not being supported.  On the other hand the Intel webpage for
the chipset (and GM) [http://www.intel.com/products/chipsets/945g/](http://www.intel.com/products/chipsets/945g/) points to a 
download that is just a tarball of xorg 6.8.11... we have not tried a compilation yet.
Have you made any progress?
Thanks
-GF

---

### Post by spira_mirabilis on 2006-05-31
Yeah I saw the Intel page for the drivers and there didn't seem to be any 950 specific information. I still am having no luck. At least I did manage a 1024x768 (which is bearable), at first I only had 800x600!

If I discover a solution, I'll post it here.

PS- Xorg seems to want to set the resolution to 1440x900 by default when running dpkg, even though I can't get that resolution...

---

### Post by curly on 2006-06-01
Hi, 
I did what you explain (sudo dpkg reconfigure etc... ) and press space bar but it didn't change anything, 
my problem is a bit special because I'm using ubuntu with parallels workstation on a Macintel (imac 20" core duo) so I would really appréciate to have full screen. 
I know it is possible to, but I can't get drivers for my video card because it's a virtual machine.
can you help me? what is the solution to configure xorg up to 1680x1050?
thanks

---

### Post by treskjegg on 2006-06-01
Thanks for the help turbojugend_gr!
I got it working eventually :)

Downloading 6.06 now. Hope that works out as well.

---

### Post by danielwsmithee on 2006-06-04
One thing that I found usefull while trying to get better resolution for my iMac core Duo (under Paralles Desktop) is to look at the xorg log file in "/var/log".  It has an entry for every resolution it attempts to setup.  It will normaly state why it will not go to a desired resolution.  In my case the hsync for a specifeid resolution was higher then the possible values set in the monitor section.

---

