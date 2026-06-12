---
title: "Display settings suddenly deconfigured."
date: 2009-09-09
forum: Desktop Environments
---

### Post by AvalonSpirit on 2009-09-09
Hi, i didnt really know here to post this
 
My display settings got deconfigured out of the blue. The system used to recognize the brand and model of my monitor and suported its native resolution (1920x1200) and now it doesn't (it says monitor: Unknown) the best it allows me is 1360x768.

I searched the forums for related problems: I've tried editing the Xorg file without succes, and updating my drivers.

I am using ubuntu 9.04 and my monitor is a Gateway® FPD2485W.

thanks.

---

### Post by hal10000 on 2009-09-09
Which graphic card are you using?
Can you post the countent of /etc/X11/xorg.conf?

---

### Post by AvalonSpirit on 2009-09-09
Here's the xorg.conf file:
> 
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection	"Display"
		Modes		"1920x1200"
	EndSubSection
	EndSection
I added the subsection under screen to see if that did anything (which it didn't)

and i'm using the onboard video which is the Intel® 3100

what do you think?

---

### Post by hal10000 on 2009-09-09
Can you change resolution with **System-->Settings-->Display** (i have a german language environment, so i can only guess how the correct menu entries are called)

---

### Post by hal10000 on 2009-09-09
Or you may reconfigure your xserver with [COLOR="Red"]sudo dpkg-reconfigure xserver-xorg[/COLOR]

---

### Post by hal10000 on 2009-09-09
> My display settings got deconfigured out of the blue
This lets me think that your /etc/X11/xorg.conf file was altered or rewritten, maybe after a recent (automatic) upgrade. If this happened, then usually the upgrading process crates a backup file of your existing xorg.conf file.

As an example, here you can see the content of my own /etc/X11 directory:
```

$ ls -l /etc/X11/xorg.conf*
-rw-r--r-- 1 root root 1219 2009-09-09 11:15 /etc/X11/xorg.conf
-rw-r--r-- 1 root root 1137 2009-04-05 21:04 /etc/X11/xorg.conf~
**[B]-rw-r--r-- 1 root root 1159 2009-08-27 15:47 /etc/X11/xorg.conf.20090827154734**[/B]
-rw-r--r-- 1 root root 2246 2009-03-30 12:27 /etc/X11/xorg.conf.dist-upgrade-200903301227
-rw-r--r-- 1 root root 1159 2009-06-15 18:55 /etc/X11/xorg.conf.dist-upgrade-200906151855
-rw-r--r-- 1 root root  894 2009-07-10 12:05 /etc/X11/xorg.conf.failsafe

```

As you can see, there are different backup-files of xorg.conf.

If after a recent upgrade my xserver was crashed, i would have searched for the file with the latest working configuration, which in this example is **-rw-r--r-- 1 root root 1159 2009-08-27 15:47 /etc/X11/xorg.conf.20090827154734** and rename it to xorg.conf:
[COLOR="Red"]sudo cp /etc/X11/xorg.conf.20090827154734 /etc/X11/xorg.conf[/COLOR]
and hopefully the x-server works correct after restarting it.

Maybe this can help you to restore your old xorg.conf

---

### Post by AvalonSpirit on 2009-09-09
> Can you change resolution with System-->Settings-->Display (i have a german language environment, so i can only guess how the correct menu entries are called)

I can change it, however the 1920x1200 option is not available, only lower resolutions.

> Or you may reconfigure your xserver with sudo dpkg-reconfigure xserver-xorg
I have already tried this with no effect

> This lets me think that your /etc/X11/xorg.conf file was altered or rewritten, maybe after a recent (automatic) upgrade.

I recently upgraded to 9.04, however, it had been running fine for a few weeks.

I'll try to restore a previous file, and see if that works.

Thanks a lot for your help

---

### Post by bobince on 2009-09-09
> **AvalonSpirit said:**
> The system used to recognize the brand and model of my monitor and suported its native resolution (1920x1200) and now it doesn't (it says monitor: Unknown) the best it allows me is 1360x768.

Yeah, same happened to me on a 1280x1024 panel connected by VGA. The mechanism used to read the monitor name and available resolutions&#8201;&#8212;&#8201;&#8216;EDID&#8217;&#8201;&#8212;&#8201;seems to break sometimes (it did once for me in Jaunty, and all the time in Karmic), and the default monitor settings it uses when no EDID is available are so conservative that you don't get anything above that 1360x768.

If it's the same VGA thing you may be able to use the fixes to xorg.conf I did, increasing the HorizSync speed to let xrandr know that changing to a higher resolution will be OK and won't blow up the monitor. See: [http://ubuntuforums.org/showthread.php?p=7910567](http://ubuntuforums.org/showthread.php?p=7910567)

I hope the kernel issue can be fixed, the results are quite bad and not easy to rescue for most users.

---

### Post by AvalonSpirit on 2009-09-10
I have managed to fix the problem! 

I tried to find previous Xorg files but all were from after the deconfiguration.

I was a bit frustrated so i shutdown the computer, unplugged all the cables, plugged tham back in again and turned the computer on.
Problem fixed!!

I now think it was a conection problem although everything appeared to be ok. I might need a new VGA cable but right now everything is working fine.

I really appreciate the answers on this thread. 
Thx hal10000 and bobince.

Ill switch the status to solved now... 
although i'm not sure the problem was identified (im not complaining though :]  )

---

### Post by bobince on 2009-09-11
> **AvalonSpirit said:**
> Problem fixed!!

Yeah, same happened to me in Jaunty: it just fixed itself randomly after a while. It wasn't a connection problem in my case as I tried a number of VGA cables.

---

### Post by abelbrito on 2009-10-08
i have a similar problem on my presario F700 notebook. my resolution's fine and everything, even the nVidia drivers are properly installed and i get the desktop effects too. yet in the display settings my monitor is shown as Unknown. any help on this would be awesome :)

---

### Post by AvalonSpirit on 2009-10-08
It might be that the monitor you have is not "known" to ubuntu, however if your resolution is fine I wouldn't worry too much about it. Although there is probably a way to name your monitor in a config file.
does anyone have any ideas?

---

### Post by hal10000 on 2009-10-09
If you just want to fill in your monitor's name, you can edit the file
[COLOR="Red"]/etc/X11/xorg.conf[/COLOR] manually, e.g with 
[COLOR="Red"]gksudo gedit /etc/X11/xorg.conf[/COLOR].
You have to find the sections "Monitor" and "Screen" and fill in the monitor name in the Identifier place.

---

### Post by abelbrito on 2009-10-09
> **hal10000 said:**
> If you just want to fill in your monitor's name, you can edit the file
[COLOR="Red"]/etc/X11/xorg.conf[/COLOR] manually, e.g with 
[COLOR="Red"]gksudo gedit /etc/X11/xorg.conf[/COLOR].
You have to find the sections "Monitor" and "Screen" and fill in the monitor name in the Identifier place.
thanks :)

---

