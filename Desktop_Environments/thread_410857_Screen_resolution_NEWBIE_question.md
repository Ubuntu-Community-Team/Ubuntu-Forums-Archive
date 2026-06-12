---
title: "Screen resolution NEWBIE question"
date: 2007-04-16
forum: Desktop Environments
---

### Post by Buz_Light on 2007-04-16
Hi all, and thanks for looking at this.

First, let me state that I'm a perfect newbie on Ubuntu, trying Linux for the really first time. I installed 7.04 and everything seems to work great on my laptop (Acer Aspire 1684WLMi) except for my screen resolution which cannot be set to 1280x800 as I do in XP (Hence I see 2 black bars on each side of my screen).  
Video card : Intel 82852/82855 GM/GME
I've seen on this forum many people reporting this problem but I am completely lost in the available information. Where do I start to fix this???

Thanks for your time,
Carl

---

### Post by lotacus on 2007-04-16
**sudo gedit /etc/X11/xorg.conf**

Section "Screen"
	Identifier	"Default Screen"
	Device		"Ati Radeon x1650"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1280x854" **"1280x800"** "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection

there is the example.

oh, i see what you mean, my resolutions in gnome don't reflect xorg.conf... so you may have a problem. To think, this issue is still present in fiesty. Gollly Gee.

---

### Post by Buz_Light on 2007-04-16
If it can help you try to figure out what my prob is, here is the output to 
[B]
sudo gedit /etc/X11/xorg.conf[/B]

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

---

### Post by notatoad on 2007-04-17
try removing any "display" subsections that you do not need from xorg.conf. 

so it looks something like this:
```
Section "Device"
Identifier "Intel Corporation 82852/855GM Integrated Graphics Device"
Driver "i810"
BusID "PCI:0:2:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-64
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82852/855GM Integrated Graphics Device"
Monitor "Generic Monitor"
DefaultDepth 24

SubSection "Display"
Depth 24
Modes "1280x800"
EndSubSection

EndSection

```

and don't forget to backup xorg.conf.  (i learned this one the hard way)

---

### Post by elchato on 2007-04-17
yeah, I have the same problem with my toshiba laptop... no 1280x800

cant I just add it into the xorg.conf?

---

### Post by Buz_Light on 2007-04-17
> **notatoad said:**
> try removing any "display" subsections that you do not need from xorg.conf. 

so it looks something like this:

...
 
and don't forget to backup xorg.conf.  (i learned this one the hard way)


OK I tried that but I was unable to save my changes. when I look at xorg.conf properties, it says the owner is "root" and others have read-only access... 
I'm sure it is a stupid detail, told you I am a newbie... Any hints?

---

### Post by finer recliner on 2007-04-17
if the file is owned by root and using sudo doesnt work, then you'll have to actually log in as the user root to edit the file.

```

$ sudo -i
//enter your normal user password
//now you are root, notice the # in the prompt
# gedit /etc/X11/xorg.conf
//edit file and save changes

```

restart the comp to see changes, or just restart X with ctrl+alt+backspace

---

### Post by Buz_Light on 2007-04-17
> **finer recliner said:**
> if the file is owned by root and using sudo doesnt work, then you'll have to actually log in as the user root to edit the file.

```

$ sudo -i
//enter your normal user password
//now you are root, notice the # in the prompt
# gedit /etc/X11/xorg.conf
//edit file and save changes

```

restart the comp to see changes, or just restart X with ctrl+alt+backspace

Thanks for the input.
However, it did not worked... after restarting X, my desktop turned black (with a nautilus problem window popping out,  and after restarting feisty, it came back to normal... When i go to syst/pref/screen resolution, the only ones available are 1024x768, 800x600, 640x480. 

Here is xorg.conf now:
```

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24

	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

```

Another idea??

---

### Post by Pikestaff on 2007-04-17
This is what worked for me:

```
sudo dpkg-reconfigure xserver-xorg
```

Choose mostly defaults until you get to the part where it asks what screen resolutions you'd like.  Press spacebar to select the ones you want, and then continue with the reconfiguration.  After you're done, reboot.  You should then be able to change your screen resolution to what you want in system settings.  Good luck!

---

### Post by Buz_Light on 2007-04-17
> **Pikestaff said:**
> This is what worked for me:

```
sudo dpkg-reconfigure xserver-xorg
```

Choose mostly defaults until you get to the part where it asks what screen resolutions you'd like.  Press spacebar to select the ones you want, and then continue with the reconfiguration.  After you're done, reboot.  You should then be able to change your screen resolution to what you want in system settings.  Good luck!

Did not work... And I really turned off all the resolution options but 1280x800. After the reboot, I still have 1024x768, 800x600, 640x480 and not the one I want...

I'm desperate, and completely rely on your ideas.

now xorg.conf looks like :
```

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

```

---

### Post by Naatan on 2007-04-17
have you tried

dpkg-reconfigure xserver-xorg

---

### Post by Buz_Light on 2007-04-17
> **Naatan said:**
> have you tried

dpkg-reconfigure xserver-xorg

Yep, that's what I explained on my last post, but still doesn't work.

Here is what I found on acer.ca, if it can help :

Video Subsystem : Intel 855GME integrated with 64MB shared RAM
LCD Properties : 15.4" WXGA TFT, 1280 x 800 x 16.7 million colors

---

### Post by Mach1US on 2007-04-17
First of all always save  backup copy of your original xorg file , trust me you will need it , then run :
```
 gtf 1280 800 60
``` 
This will print the mod line.
Cut  starting at 
 ```
Modeline"1280.....-HSync +Vsync
```
and paste into xorg file after
```
 Identifier    "Generic Monitor"
```
Make sure your range in
```
 HorizonSync 28-64
```
is as high as modline value , generally up to 64

---

### Post by Buz_Light on 2007-04-18
> **Mach1US said:**
> First of all always save  backup copy of your original xorg file , trust me you will need it , then run :
```
 gtf 1280 800 60
``` 
This will print the mod line.
Cut  starting at 
 ```
Modeline"1280.....-HSync +Vsync
```
and paste into xorg file after
```
 Identifier    "Generic Monitor"
```
Make sure your range in
```
 HorizonSync 28-64
```
is as high as modline value , generally up to 64

Ok, I tried that too, made my xorg.conf look like this 
```
Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Modeline "1280x800_60.00"  83.46  1280 1344 1480 1680  800 801 804 828  -HSync +Vsync
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection
```
because the output of  **gtf 1280 800 60** was
```
1280x800 @ 60.00 Hz (GTF) hsync: 49.68 kHz; pclk: 83.46 MHz
  Modeline "1280x800_60.00"  83.46  1280 1344 1480 1680  800 801 804 828  -HSync +Vsync
```
restarted X and rebooted computurer and did not worked... Still only see 1024x768,800x600 and 640x480 although these are not in xorg.conf
pfffffff....     thanks for helping

---

### Post by Mach1US on 2007-04-20
In my old Toshiba the modeline did the trick.
first try add other depths
[HTML] 	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection
 [/HTML]

if it won't work try
[HTML]Section "Monitor"
Identifier "LCD Monitor"
HorizSync 30-64
VertRefresh 60
Option "DPMS"
EndSection[/HTML]

If it also fails try aditionally 
[HTML]Section "Device"
Identifier "Intel Corporation 82852/855GM Integrated Graphics Device"
Driver "i810"
BusID "PCI:0:2:0"
Option "ShadowFB" "true"
EndSection[/HTML]

If it still will not work try to get more info about the driver it looks that you using same driver as i despite having little different card .
I Have intel too but mine is 915GM and my diver is i810 also.
My dell displays perfect 1280x800 with this exact driver but i'm not sure if it would be the same one for your card.

---

### Post by kkimes on 2007-04-20
I have a similar problem with my HP computer with a Nvideo Gforce4 MX video built in.  I can run 1200 in windows no problem, but cannot run that high in Ubuntu.  I was thinking it was a driver issue, but I wonder if it is just because it doesn't know that my monitor is capable of running there.

The system calls my monitor a generic monitor instead of a HP pavilion f1703.  I still think it is a driver issue, but maybe it is a monitor driver problem instead of a video driver.

Any suggestions?

---

### Post by Mach1US on 2007-04-20
> **kkimes said:**
> I have a similar problem with my HP computer with a Nvideo Gforce4 MX video built in.  I can run 1200 in windows no problem, but cannot run that high in Ubuntu.  I was thinking it was a driver issue, but I wonder if it is just because it doesn't know that my monitor is capable of running there.

The system calls my monitor a generic monitor instead of a HP pavilion f1703.  I still think it is a driver issue, but maybe it is a monitor driver problem instead of a video driver.

Any suggestions?

My monitor section shows "Generic Monitor" but displays perfect res. and  in all my laptops and desktops have full res with generic in  xorg and actually sporadically after  real heavy tweaking i get the actual screen recognition in xorg but it never performs rite.
this card has dual screen capabilities , did you try it with external screen?

---

### Post by kkimes on 2007-04-22
I am not running a laptop.  I'm running an HP desktop with a builtin (on the MB) Nvidia chip set.  If I try to change the resolution via the System > Preferences interface, it does not show a resolution higher than 1028.  I'm used to running it in 1200 mode (when in WindowsXP), so it does bug me a little bit since I know the hardware and monitor is capable of running that high.

A somewhat related problem is how foxfire displays on my Ubuntu setup.  It is so bad that some pages are unreadable.  I had to install Opera (which doesn't run flash very well), but at least does a good job of displaying most pages I want to look at.

---

### Post by Mikkel Nielsen on 2007-04-22
I share this same problem and looking in other threads it seems there are quite a lot of people suffering from not being able to run as high a resolution in feisty as they used to do in either windows or older ubuntu versions.

Me being a complete ubuntu-n00b it would be great with a dummy-guide on how to solve this problem, I don't even know where to write the codes people are suggesting as solutions.

Bare with a ubuntu-n00b :)

Is it possible that there will come some update that solves the problem?

---

### Post by Mach1US on 2007-04-23
Adjustments available in gnome GUI are just graphical representation of actual results of system interpretation of a config files so if you can't see certain res in drop down menu it doesn't mean it isn't capable of it , it's just means you haven't properly configured it yet .
Look into those :
 [http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)
(read where it says "Getting the Right Mode for an LCD monitor"
[https://wiki.caosity.org/tiki-index....0Configuration](https://wiki.caosity.org/tiki-index....0Configuration)
Trust me if your machine has the guns to run the res linux can display it , it's just a matter of you ingenuity .
If you'll  grind out of initial bumps and potholes you will be more than glad to have Ubuntu .

---

### Post by Buz_Light on 2007-04-23
GREAT!

I finally fixed my resolution with the help of this [**[COLOR="Blue"]howto[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=24923")

Give it a try, it worked like a charm for me and the guide is really simple to follow.

THANKS to everyone who helped on this thread.

Carl

---

