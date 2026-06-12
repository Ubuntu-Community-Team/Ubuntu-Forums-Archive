---
title: "Can't change resolution with 915resolution"
date: 2007-05-21
forum: Desktop Environments
---

### Post by tnic on 2007-05-21
I use the 915resolution package to set the right screen resolution on my FS Amilo Pro V3205 laptop with intel 945GM graphic controller.

I want to change my screen resolution to 1280x1024 because I'm using an external monitor.

I type:

```

pingvin@tomas-laptop:~$ sudo 915resolution 49 1280 1024
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 945GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Patch mode 49 to resolution 1280x1024 complete

```

and then I restart X, but nothing happens. In fact the screen resolution remain at 1280x800 whatever which changes I do with 915resolution and xorg.conf. 

But I have found an interesting piece of text in Xorg.0.log : 

```

...
(II) I810(0): Generic Monitor: Using hsync range of 45.71-50.53 kHz
(II) I810(0): Generic Monitor: Using vrefresh value of 60.00 Hz
(II) I810(0): Not using mode "1280x1024" (no mode of this name)
(II) I810(0): Not using mode "1600x1200" (no mode of this name)
(II) I810(0): Increasing the scanline pitch to allow tiling mode (1280 -> 2048).
(--) I810(0): Virtual size is 1280x800 (pitch 2048)
(**) I810(0): *Built-in mode "1280x800"
(**) I810(0):  Built-in mode "1024x768"
...

```

It seems like X don't find the mode I set with 915resolution. Does anyone know what I am doing wrong ?

Thanks in advance!

---

### Post by Kobalt on 2007-05-21
Try to remove in your xorg.conf all the resolutions you don't want. Save and close and finally restart X with Ctrl+Alt+Backspace.

---

### Post by tnic on 2007-05-21
OK, I did that 

xorg.conf :

```

...
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection
...

```

I restarted X and nothing special happened. Still I can choose between 1280x800 and 1280x768.

Here is some of my Xorg.0.log:

```

...
(II) I810(0): Generic Monitor: Using hsync range of 45.71-50.53 kHz
(II) I810(0): Generic Monitor: Using vrefresh value of 60.00 Hz
(II) I810(0): Not using mode "1280x1024" (no mode of this name)
(II) I810(0): Increasing the scanline pitch to allow tiling mode (1280 -> 2048).
(--) I810(0): Virtual size is 1280x800 (pitch 2048)
(**) I810(0):  Built-in mode "1280x800"
(**) I810(0):  Built-in mode "1024x768"
(==) I810(0): DPI set to (75, 75)
...

```

(II) I810(0): Not using mode "1280x1024" (no mode of this name) ?
Is there anyone who knows what this log really means? 

It still seems that xorg don't recognize the mode change I do with 915resolution. This is really bothering me.

---

### Post by veloce on 2007-05-21
Have a look at the output of:

 915resolution -l

Does this list the desired mode?  I suspect that it (mode 49) has the wrong "name" i.e. it's not the text "1280x1024"


Why are you using 915resolution manually? Did it not work automatically? I have had more success using its  config file:

/etc/default/915resolution

set the xres and yres lines in that and reboot.

---

### Post by tnic on 2007-05-22
Here is the output from 915resolution -l

```

Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 945GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1280x800, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1280x800, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1280x800, 32 bits/pixel

```

I have also tried editing the /etc/default/915resolution manually without any effect.

I think my problem is in xorg.conf. Is there some way to specify which mode I want to use?

---

### Post by veloce on 2007-05-22
> **tnic said:**
> Here is the output from 915resolution -l
I think my problem is in xorg.conf. Is there some way to specify which mode I want to use?

Yes, that 915resolution output shows your resolutions fine so it must be in your xorg.conf.

Now, you have two monitors connected, right?  I was just trolling through the log file you posted earlier and there is a line in there saying that clone mode is on. And there is the line in xorg.conf with the option command! 

This may be the problem - it will only let you have resolutions that work on both monitors.  In your serverlayout section, can you try adding the line:

option "clone" "off"

If this doesn't work, I suggest you set up two device, monitor and screen sections specific to your hardware and specify which to use in the server layout section.

---

### Post by tnic on 2007-05-22
> **veloce said:**
> 
Now, you have two monitors connected, right? 

I have one external monitor connected to my laptop

> **veloce said:**
> 
In your serverlayout section, can you try adding the line:
option "clone" "off"


I did that, but nothing happened.

> **veloce said:**
> 
If this doesn't work, I suggest you set up two device, monitor and screen sections specific to your hardware and specify which to use in the server layout section.
This seems reasonably but I'm new to linux and I don't know how to configure my xorg.conf. Can you specify more precise what to type?

---

### Post by capdog on 2007-05-22
Hi guys,

Any luck? I'm battling with the same problem!

---

### Post by tlayton_at_work on 2007-05-22
Not sure if this will exactly fix your issue, but you may want to try upgrading your video driver.  Intel just released a new version that supports modesetting and doesn't require 915resolution.  You would need to add the package 'xserver-xorg-video-intel' and remove 'xserver-xorg-video-i810'.  Then, change the driver in xorg.conf from 'i810' to 'intel'.

I'm currently using this new driver (I have the 945GM on a Dell), and there seems to be some performance improvements as well.  Improvements could also be the updated 'xserver-xorg-core' from 1.2 to 1.3.

---

### Post by tnic on 2007-05-22
I have tried the xserver-xorg-video-intel driver. It gives me some more resolution to choose between, but all of them are less than 1280x1024. And my Fn+F3 button to switch to external monitor does not respond on this driver so I changed back to xserver-xorg-video-i810.

I really hope that it will be easier using an external monitor on later ubuntu versions.

---

### Post by capdog on 2007-05-22
I finally fixed it, and posted my full details here:

[http://ubuntuforums.org/showthread.php?p=2702458](http://ubuntuforums.org/showthread.php?p=2702458)

I think there's a solution in there for you! Try it! :popcorn:

---

### Post by veloce on 2007-05-22
> **tlayton_at_work said:**
> Not sure if this will exactly fix your issue, but you may want to try upgrading your video driver.  Intel just released a new version that supports modesetting and doesn't require 915resolution.  You would need to add the package 'xserver-xorg-video-intel' and remove 'xserver-xorg-video-i810'.  Then, change the driver in xorg.conf from 'i810' to 'intel'.

I'm currently using this new driver (I have the 945GM on a Dell), and there seems to be some performance improvements as well.  Improvements could also be the updated 'xserver-xorg-core' from 1.2 to 1.3.

Are you using dual monitors?  I switched to the intel driver and it eliminated the need for 915resolution, but wouldn't let me use two monitors. (gdm fails to start).  It appears to have something to do with memory requirements but I've switched back to i810.

---

