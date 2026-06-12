---
title: "[SOLVED] acer x191w, feisty herd, &amp;amp; 1440x900"
date: 2007-10-02
forum: Desktop Effects &amp; Customization
---

### Post by uncleclinto on 2007-10-02
Hey peeps,

I just put 64 bit herd on my new acer.  The monitor (x191w) recommends 1440x900, but the best resolution available is 1280x1024, which is pretty crappy.  It's all squished and weird looking.  I tried many solutions including modifying the xorg.conf.  At one point, I ended up not being able to access ubuntu at all.  the monitor just flashed "input not supported".  In dapper, about a month ago, I had this same issue and typed something magical in the terminal that opened a gui xorg configuration utility of some kind.  I can't remember how to do that or find the tudorial that mentioned it for the life of me.  Can anyone suggest a solution??

Clint

---

### Post by oneporter on 2007-10-03
Hey Clint,

Getting the resolution right on this monitor is clutch.. it looks a lot better at 16:10..

I don't quite know what you're talking about with the gui, but maybe you reconfigured your xserver packages?

**(EDIT: This doesn't seem to work in Gutsy, but does in fiesty and transfers if you upgrade)**
What I did to get the higher resolution was to change the resolutions in the "Screen" Section.

Run (alt + f2) **gksu gedit /etc/X11/xorg.conf**  

There should be a few different resolutions for each depth setting but each line of resolutions will be the same.  Change the first entry to "1440x900" in each one.  So it looks something like this:

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
	Monitor		"X191W"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1440x900"	"1360x850"	"1280x1024"	"1280x960"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1440x900"	"1360x850"	"1280x1024"	"1280x960"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1440x900"	"1360x850"	"1280x1024"	"1280x960"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1440x900"	"1360x850"	"1280x1024"	"1280x960"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1440x900"	"1360x850"	"1280x1024"	"1280x960"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1440x900"	"1360x850"	"1280x1024"	"1280x960"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Note:  Your device name is probably different so don't change that...
ctrl + alt + backspace and log back in...

Hope that helps

---

### Post by uncleclinto on 2007-10-03
Hey,

here's what I have now:
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"X191W"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Even with a restart, I still get only 1280x1024 and down for resolution choices.

---

### Post by oneporter on 2007-10-03
You piqued my interest.  So, I've been tinkering with this on and off all day.  It looks like if you'll add a modeline in the monitor section of your xorg.conf it will work.

```
Section "Monitor"
	Identifier   "X191W"
	HorizSync	31-80
	VertRefresh	56-75
	Modeline 	"1440x900@75" 146.10 1440 1472 2024 2056 900 917 928 946
	Option	    "DPMS"
EndSection
```

---

### Post by Gremlinzzz on 2007-10-03
type 915 in synaptic package manager

---

### Post by uncleclinto on 2007-10-07
Okay... I ditched the 64 bit feisty because I was tired of forcing architecture all the durned time.  I went with Ubuntu Studio instead, but, alas, I still suffer from my resolution woes.

I tried 915 Resolution.  I tried downloading my intel driver.  Basically, I tried all of the suggestions in the following pages & posts:
[LIST]
[*][http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_Large_Widescreen_Support](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_Large_Widescreen_Support)
[*][http://www.ubuntugeek.com/fix-for-widescreen-resolutions-for-intel-display-cards-in-ubuntu-feisty.html](http://www.ubuntugeek.com/fix-for-widescreen-resolutions-for-intel-display-cards-in-ubuntu-feisty.html)
[*][http://ubuntuforums.org/archive/index.php/t-441878.html](http://ubuntuforums.org/archive/index.php/t-441878.html)
[*]And many more.
[/LIST]

None of these fixed my problem.  Some rendered my display useless, throwing me into a noob panic.  Luckily, I was able to configure xorg from the terminal and get things back up and running.  Now, I find this promising suggestion, noted in the following two posts:
[http://ubuntuforums.org/showthread.php?t=280683&page=3](http://ubuntuforums.org/showthread.php?t=280683&page=3)
[http://ubuntuforums.org/showthread.php?t=370204](http://ubuntuforums.org/showthread.php?t=370204) 

It's tempting to try this, but before I do, I would like some insight into what happens if I get the bouncing display message that reads "input not supported"?  How do I get in and fix the damage??  The last time 915 actually got me close to 1440x900, the options menu was gone from my grub screen.  If it hadn't been 915 (which doesn't permanently change my xorg.conf file), I'd be screwed.  

Anyway, I just need a backup plan because I finally had to break down and do some work on the old compy, and I don't want to loose all my data in an attempt to get my nasty squished resolution fixed.

Please help!  ](*,)

---

### Post by uncleclinto on 2007-10-09
Okay,

I used Woodyk's advice (summarized below).
```
Note: The bold sections should be replaced with the settings for your monitor.

1) Find the specifications for your monitors model number. In my case I did a little bit of googling to find out the detailed specs on my monitor. If you're lucky enough to have the manual then life will get a little bit easier. There are three sections in particular that you want.

    * Horizontal Scan Frequency (ex: 30 kHz to 81 kHz )
    * Vertical Scan Frequency (ex: 56 Hz to 76 Hz )
    * Optimal Resolution (ex: 1920 x 1200 @ 60 Hz)

The spec sheet may contain other useful information so make sure you keep a copy of the info.

2) We now know that the optimal setting is 1920 x 1200 @ 60 Hz. Simply run the following to obtain the "Modeline" for your xorg.conf.

    gtf 1920 1200 60

The output should resemble this:

    # 1920x1200 @ 60.00 Hz (GTF) hsync: 74.52 kHz; pclk: 193.16 MHz
    Modeline "1920x1200_60.00" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -HSync +Vsync

3) Now edit you're /etc/X11/xorg.conf. Under the "Monitor" section modify the "HorizSync" and "VertRefresh" to match the specs that you obtained on your monitor. Also add the "Modline" string you have from your gtf output. Ex:


    Section "Monitor"
    Identifier "Generic Monitor"
    Option "DPMS"
    HorizSync 30-81
    VertRefresh 56-76
    # 1920x1200 @ 60.00 Hz (GTF) hsync: 74.52 kHz; pclk: 193.16 MHz
    Modeline "1920x1200_60.00" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -HSync +Vsync
    EndSection

Under you're "Screen" section you will now need to add your specified "Modeline" res setting. Ex:


    Section "Screen"
    Identifier "Default Screen"
    Device "ATI Technologies, Inc. RV280 [Radeon 9200]"
    Monitor "Generic Monitor"
    DefaultDepth 24
    SubSection "Display"
    Depth 24
    Modes "1920x1200_60.00" "1280x1024"
    EndSubSection
    EndSection

I hope this helps... Its a shame to loose so much desktop real estate to a bad monitor config. 
```

I'm really running out of ideas.  I actually managed to solve this problem on my Dapper box, which shares the same monitor via Belkin, about a month ago. I'm kicking myself for not posting a step-by-step of the solution.  Someone, somewhere posted some CLi voodoo to open a GUI method for configuring xserver xorg.  It essentially asks all of the same questions as the text method, but for some reason didn't break my system like the text method.  Does anyone have any idea what I'm talking about or a clue what I can do to fix this?  I'm getting beyond frustrated with this situation.  I'm losing a load of desktop real estate, which is bad for a web designer.

Thanks,
Clint

---

### Post by oneporter on 2007-10-10
open terminal type sudo dpkg-reconfigure xserver-xorg

is that what you're talking about?

---

### Post by uncleclinto on 2007-10-10
> **oneporter said:**
> open terminal type sudo dpkg-reconfigure xserver-xorg

is that what you're talking about?

Close!  That's, in fact what broke my dapper system.  Someone then told me another command that opens a GUI version of that, which asks the same questions, but allowed me to skip questions (maintaining the current functional config settings), while still giving me the opportunity at the end to select additional screen resolutions.  I didn't have to install anything.  This was in dapper already.  I simply typed the command (which I was too STUPID to write down), and up popped the cool little GUI dialog.

Anyone know what that is??

---

### Post by uncleclinto on 2007-10-10
SOLVED!!!!!!!

Okay, so several poeple have pointed out this little trick throughout the forums: "sudo apt-get install xserver-xorg-video-intel".  It, therefore was the first thing I did, having an intel card and a wide screen.  Unfortunately, no one bothered to mention that one must also edit the xorg.conf file and replace "vesa" with "intel".  I did that... restarted x... and rock, I'm working in native res baby!
:guitar:

---

### Post by danst on 2007-11-01
Did you use the 915resolution hack ... or is it just the intel drivers that set the resolution to 1440x900 ...

---

