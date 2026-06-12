---
title: "Can not run Compiz with GeForce 8600GT"
date: 2009-01-09
forum: General Help
---

### Post by nicnocquee on 2009-01-09
Hello guys, need help here.

I tried to enable Visual Effects in Ubuntu 8.10 Ibex through System -> Preferences -> Appearance, but failed, Desktop Effect cannot be enabled.
Then I tried installing the restricted driver first (tried both the 173 and 177), but after I restarted, I got a black monitor with "Out of Timing Error". I restore the xorg.conf file (I backed it up before installing the driver), restart the gdm, then tried Envyng. But still same result.

I tried adjusting the HorizSync and VertRefresh in by adding lines in xorg.conf,
```
Section "Monitor"
        Identifier   "Generic Monitor"
        HorizSync   24-82
        VertRefresh 56-86
EndSection
```
The number is coming from executing ddcprobe:
```

...
ctiming: 1024x768@66
monitorname: LL-T1610W
monitorrange: 24-82, 56-86
...

```
But still not working.

This is the output of lscpi |grep -i vga
```
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
```

This is the output of running compiz in terminal
```
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
```

I also tried running Nvidia X Server Setting, through System -> Administration -> Nvidia X Server Settings. But it said 
```
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
```
I followed the instruction, but still after restarting got "out of timing" black screen.

Any suggestion?I really want to run compiz :(

FYI: I did fresh install of Ibex, but using the old /home partition.

---

### Post by loomsen on 2009-01-09
Do you have the nvidia driver installed?

If not do this:
```

sudo apt-get install envyng-core envyng-gtk
```
Then run the program to install the right driver.

If you already did this just run
```

sudo nvidia-xconfig
```

and then hit ctrl+alt+backspace to restart your xserver.

---

### Post by nicnocquee on 2009-01-10
hi loomsen,

as i have said, i installed the nvidia driver, both through system-> administration -> hardware drivers and through envyng, but both gave the same result when i restarted the system, the "out of timing" error with black screen.
any other idea?:confused:

---

### Post by Vadi on 2009-01-10
This "out of timing" seems to be a problem with the nvidia driver and your monitor. I haven't seen the issue before, and it seems that the driver installs fine.

I'd recommend posting here: [http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by nicnocquee on 2009-01-11
ok vadi, thanks 4 the info
i'll try that

---

