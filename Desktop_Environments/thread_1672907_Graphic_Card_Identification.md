---
title: "Graphic Card Identification"
date: 2011-01-21
forum: Desktop Environments
---

### Post by sembagdod on 2011-01-21
I have PC with Motherboard Intel® Desktop Board D945GCNL, and Ubuntu 10.10 installed on it. 

Graphic card was working fine, but recently i don't know what happen suddenly the visual effects stop working, and i believe the issue with the identification of the VGA. 
with error message"Desktop effects could not be enabled"


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=181669&stc=1&d=1295638925[/IMG]


i checked some forums related but wasn't able to solve it. 
when i type compiz. 
it stuck on the below: 

 [COLOR="Blue"]zhra@zhra-desktop:~$ compiz
 Xlib:  extension "GLX" missing on display ":0.0".
 compiz (core) - Fatal: Root visual is not a GL visual
 compiz (core) - Error: Failed to manage screen: 0
 compiz (core) - Fatal: No manageable screens found on display   
 :0.0

 Launching fallback window manager
[/COLOR]
and the PC hang after that. 

Please guide me in detail instruction as am new to Linux world

---

### Post by Krytarik on 2011-01-22
You probably have not the correct video driver installed or it runs with wrong settings.

What video card/chip is installed, what driver is running, did you install one?
To find out the video card/chip, if you don't know it, enter in a terminal:
```
lspci |grep VGA
```

You may also post the content of the file "/etc/X11/xorg.conf".

---

### Post by celldweller1591 on 2011-01-22
try this :- 
compiz --replace ccp & emerald --replace &
Also , see this link for help> [http://wiki.compiz.org/Troubleshooting](http://wiki.compiz.org/Troubleshooting)

---

### Post by sembagdod on 2011-01-23
Thanks Krytarik, i did run that code and below is what i got

[COLOR="Red"]zhra@zhra-desktop:~$ lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)[/COLOR]

And I didn't find the file "/etc/X11/xorg.conf", instead i found 
xsession.options
xwrapper.config
xreset
x
rgb.txt 

and some other folders as the below screenshot. 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=181788&stc=1&d=1295794618[/IMG]

Please advise

---

### Post by sembagdod on 2011-01-23
Thanks Krytarik, i did run that code and below is what i got

[COLOR="Red"]zhra@zhra-desktop:~$ lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)[/COLOR]

And I didn't find the file "/etc/X11/xorg.conf", instead i found 
xsession.options
xwrapper.config
xreset
x
rgb.txt 

and some other folders as the below screenshot. 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=181788&stc=1&d=1295794618[/IMG]

Please advise

---

### Post by matt_symes on 2011-01-23
Hi

What driver have you installed ?

```
lspci -v | grep -A10 VGA
```

Post the output back here.

This will also tell us what driver you have installed. I suspect you don't have the correct driver installed as you don't have an xorg.conf, but i am no expert with Intel.

Kind regards

---

### Post by sembagdod on 2011-01-23
here you go: 

[COLOR="Red"]
zhra@zhra-desktop:~$ lspci -v | grep -A10 VGA
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
	Subsystem: Intel Corporation Device d606
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 90200000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 30e0 [size=8]
	Memory at 80000000 (32-bit, prefetchable) [size=256M]
	Memory at 90280000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915
zhra@zhra-desktop:~$ [/COLOR]


Regards

---

### Post by Krytarik on 2011-01-23
I'm also not an expert for Intel graphic chips, but I believe the driver you are running is the only one available/appropriate.

Try re-installing those:
```
sudo apt-get install --reinstall xserver-xorg-video-intel
```If that doesn't fix the issue, which I somewhat expect, take a look into ~/.xsession-errors and /var/log/Xorg.0.log for error messages.

---

### Post by sembagdod on 2011-01-23
Reply @ Krytarik

Sorry man it didn't work 

Regards

---

### Post by sembagdod on 2011-01-23
Reply @ celldweller1591
please check the below output 

[COLOR="Red"]
zhra@zhra-desktop:~$ compiz --replace ccp & emerald --replace &
[1] 1966
[2] 1967
zhra@zhra-desktop:~$ Xlib:  extension "GLX" missing on display ":0.0".
compiz (core) - Fatal: Root visual is not a GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager
[/COLOR]

---

### Post by Krytarik on 2011-01-23
Then post the content of the file "/etc/X11/xorg.conf", if there is one (you may use the code-tags (#) this time).

Also check the log files I mentioned.

---

### Post by sembagdod on 2011-01-23
Sorry i didn't get that? should i type "code-tags (#)" on the terminal ?

---

### Post by Krytarik on 2011-01-23
> **sembagdod said:**
> Sorry i didn't get that? should i type "code-tags (#)" on the terminal ?
No, when you post output/content here, mark it and click at the # to get it into a separate frame, it's just better to distinguish then, and is monospaced.

---

