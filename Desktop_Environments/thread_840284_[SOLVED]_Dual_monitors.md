---
title: "[SOLVED] Dual monitors"
date: 2008-06-25
forum: Desktop Environments
---

### Post by Motorhead Kaze on 2008-06-25
Hello.  I just bought a second monitor and got an ATI, Radeon dual-head video card. Ubuntu was cool to suggest an ATI driver, and I installed it.  Both monitors are working, one on a digital cable and the other on an analog cable. The second screen of course is still just a clone of the first. Is there a menu I need to tick off a box to split the monitors, or download a program? Is the program named Catalyst? 

I read several other posts but saw some help for Nvidia users, a guy saying that he thought ATI users were out of luck, and a very lengthy tutorial about dual-monitor setup from 2006.

Is there a relatively easy way to make the second monitor an extension of the first? I.e. one large desktop?

---

### Post by Motorhead Kaze on 2008-06-26
Hmmm. Nobody?

For anyone in-the-know, I have tried someone's tutorial for editing my xorg.conf with zero results.  Here is what I did in xorg.conf:

```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
	Option "monitor-VGA" "lcddisp"
	Option "monitor-DVI" "Configured Monitor"
EndSection

Section "Monitor"
	Identifier	"lcddisp"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
Option "LeftOf" "lcddisp"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes	"1280x1024"
	Virtual 2560 1024
	EndSubSection
	Defaultdepth	24
EndSection


```After restarting X I put this in a terminal
```

 xrandr --output VGA --pos 1280x0

```

But alas, I still have two of the same screen going on here. So what is not working?

Help would really be appreciated.

PS Are the names "lcddisp" and "Configured Monitor" not ok? "lcddisp" I copied from the text above. If this monitor actually has a proper name, how do I find it? Should I not be using the name "Configured Monitor" anymore?

---

### Post by shr2004 on 2008-06-26
Instead of starting a new thread, I also place my queries here as they are same.
I installed Ubuntu Hardy on my laptop, it has Intel driver, screen 1280x800. I have external monitor, 1280x1024. To configure dual monitor I tried most tutorials, here are the summary that I tried.
1. Ubuntu's System> Preferenes> ScreenResolution
2. displayconfig-gtk
3. modifying Xorg and use xrand commands
4. URandr tool (gui for above)
From all of them I got same result. Here is what I got and what I want
(i). I got cloned output in both monitors, resolution 1280x1024, so in laptop screen I cannot see lower part of the screen.
(ii). creating a big virtual screen changing xorg, I tried to use left-of, right-of, above, below. Above and below do not work at all. right and left works but resolution problem as (i). 
Now I use either laptop display or external, but not together or extended. xrandr should work fine and its very easy to use it. Any help from any side. Here is part of my xorg.conf which is pretty much nothing
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection
```

Thanks

---

### Post by Motorhead Kaze on 2008-06-27
Wow, what a bunch of crap that was!  Somehow, messing with all of this xorg.conf stuff woke up Compiz?! How in the heck THAT can happen, I have no idea. I do remember a large compiz update coming up yesterday, but I have all visual effects turned off...at all times. Compiz somehow got switched on and gave me a blank white screen...which took my friend and I an hour to fix before I could get back to this dual monitor situation.

(BTW, to fix that, I went through Gnome failsafe mode, ran ```
sudo apt-get remove compiz
``` then restarted Gnome, and if you can believe this, had to go into SYNAPTIC to kill off about 6 or so Compiz related programs that somehow got turned on!  &#12467;&#12531;&#12500;&#12474;&#12398;&#12496;&#12459;&#12516;&#12525;&#12540;&#65281;)

On the dual monitor problem, I tried a couple different dual monitor tutorials (with all sorts of unnecessary added code in them) and though none of them worked for me, a friend found the following: first, ```
gksudo gedit /etc/X11/xorg.conf
```and add the red text.
```

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        DefaultDepth    24
       [COLOR="Red"][B] SubSection "Display"
            Depth           24
            Virtual         2560 1024
        EndSubSection[/B][/COLOR]
EndSection
``` then I restarted X, went into system/preferences/screen resolution and unchecked the clone screens, pulled the monitor (white square) marked "Electronics" off to the left, selected the resolution, 1280x1024 at a refresh rate of 60hz and on the monitor to the right (another white square) marked "BenQ 19in" I selected the same resolution and refresh rate.  Apply, close.

Now I have dual monitors on Ubuntu Hardy.

The dumbass thing is, I restarted X and my right monitor was dead again, and I had to go back into system/preferences/screen resolution and redo my changes.  Apparently, this is another issue, and a friend has this to add, *"It sounds like the unchecked box getting rechecked is a bug that involves a file in your home directory called ~/.gnome2/monitors.xml,  which sometimes doesn't get overwitten properly. That's one reason deleting all the .g stuff worked. If the problem comes back, try deleting that file, resetting the stuff in that dialog, and restarting"*. So, with that in mind, I am off to enjoy my dual monitors.

Note: If you are just trying to get the dual monitors going, my white screen/compiz b.s. can just be ignored.  

Note 2: Anyone who has trouble with finding what the Virtual numbers should be &#8594; add the widths of your 2 monitors (for me, 1280+1280=2560) to get the first number, and the 2nd number is the greater height of the 2 monitors (for me, both are the same, so the number remains 1024) hence my virtual number was 2560 1024

---

### Post by BluePlum on 2008-06-27
[http://ubuntuforums.org/showthread.php?t=842094](http://ubuntuforums.org/showthread.php?t=842094) Can u help me do it?

---

### Post by Motorhead Kaze on 2008-07-01
Hi.  I am back. Due to some ugliness with Gnome freezing on me, and spending hours trying to get it to work, I decided to install Hardy fresh.

Why do I mention that?  Well, the edit I did of my xorg.conf stopped working after the reinstall. sudo xrandr -q showed that I had only one monitor...both were on though, and working as clones.

After 10 hours -- really -- of searching the forums, trying many more dual monitor tutorials, I found the answer was that **THIS TIME I had installed propriety drivers for my graphics card** (ATI), and somehow that was keeping Ubuntu from "Seeing" my second monitor. Once I turned the driver OFF, that simple fix I did above, restarting Gnome, then arranging my monitors in the Screen Resolution prefs menu, brought my dual monitor, extended desktop back to me.

Everything is cool again.

Peace

Oh, helpful links were:

[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)
[https://help.ubuntu.com/community/XORGHardy](https://help.ubuntu.com/community/XORGHardy)
And about the propriety drivers, etc. [http://ubuntuforums.org/showthread.php?t=766846&highlight=hardware+detection&page=2](http://ubuntuforums.org/showthread.php?t=766846&highlight=hardware+detection&page=2)

---

