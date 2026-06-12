---
title: "Installation.....HELP ME PLEASE!"
date: 2006-01-10
forum: Desktop Environments
---

### Post by gle041 on 2006-01-10
Hello.

I have tried installing Ubuntu on my desktop system a few times. I just had it format the drive and then install it.

After it is installed, it will not boot and says:

"Failed to start the X server (your graphical interface).  It is likely the it is not set up correctly.  WOuld you like to view the X server output to diagnose the problem?"

Please help me....

---

### Post by eqisow on 2006-01-10
boot in in recovery mode (from the GRUB menu) and try "sudo dpkg-reconfigure xserver-xorg" at the command line. Follow the on screen instructions to configure your monitor and video card with X. If that fails try "install nvidia-glx" first (if you have an nvidia card, I don't know about other ones) the reconfigure X again.

---

### Post by probe45 on 2006-01-10
Also an option is to look @ the given output and try to see whats wrong or paste it here.

#cat /var/log/Xorg.0.log |grep EE

Best thing when you cant figure it out is also tell what videocard you are useing :)

Good luck

---

### Post by gle041 on 2006-01-10
It is a NVIDIA video card, I tried to reconfigure it, but I still get the error message.

In my BIOS, the prmary video adapter is the PCI which is where it is.

Any other ideas?

---

### Post by probe45 on 2006-01-11
Since xorg also can fail on other stuff, like wrong keybord/mouse settings, monitor settings etc it would be better to pass te file output from the command I gave you in my earlier post.

---

### Post by gle041 on 2006-01-11
anyone have any ideas...I tried everything suggested.

I feel like giving up on Linux....

---

### Post by probe45 on 2006-01-11
[QUOTE=gle041]anyone have any ideas...I tried everything suggested.

I feel like giving up on Linux....[/QUOTE]

Erm??

I still dont see the output of  "#cat /var/log/Xorg.0.log |grep EE" (without the quotes) anywhere. You ask for help I want to provide you with help but without that output its almost impossible to help since I dont know what the failure is.

Like I said before the error you give in the topicstart does not tell a thing only that there is a fault in the config with the output of "#cat /var/log/Xorg.0.log |grep EE" it will be much clearer what the problem is.

So please provide us with the output of #cat /var/log/Xorg.0.log |grep EE

thx

---

### Post by gle041 on 2006-01-11
I just tried it...it dosn't do anything

---

### Post by probe45 on 2006-01-11
what did you type?

I hope:

cat /var/log/Xorg.0.log |grep EE

if so it should give an output else you also can do

cat /var/log/Xorg.0.log

only that way the list will be longer

---

### Post by gle041 on 2006-01-11
Okay,

It says:

(II) Loading extension MIT-SCREEN-SAVER
(EE) No devices detected.

---

### Post by probe45 on 2006-01-11
[QUOTE=gle041]Okay,

It says:

(II) Loading extension MIT-SCREEN-SAVER
(EE) No devices detected.[/QUOTE]

mhh not much either :(

What devices? mouse? keyboard? screen? videocard? 

2 options..

sudo dpkg-reconfigure xserver-xorg

Will rebuild your xorg.conf but I doubt it will help

or paste your /etc/X11/xorg.conf here with following info:

- What monitor (brand + size 14" 15" 17" or bigger)
- What Mouse (usb ps2 or serial)
- What keyboard (qwerty, azerty, qwertz etc)
- What videocard (brand and type pci or agp)

---

### Post by jerrykenny on 2006-01-11
Probe, without the info that equisow  is asking for, its impossible to say whether the problem is with your mouse, or graphics card . . . . 

If you want to try manually editing a file, you could try . . . typing

sudo   nano /etc/X11/xorg.conf

then going down to Graphics card, make sure driver is set to "nv" and not "nvidia",

It may be the mouse, so if that wont work try changing your mouse to "Driver"  "/dev/psaux"

Change one thing at a time . . . 

Press Control and X, to save the file, you'll be prompted to save type y

then type   sudo startx

---

### Post by probe45 on 2006-01-11
[QUOTE=jerrykenny]Probe, without the info that equisow  is asking for, its impossible to say whether the problem is with your mouse, or graphics card . . . . 

If you want to try manually editing a file, you could try . . . typing

sudo   nano /etc/X11/xorg.conf

then going down to Graphics card, make sure driver is set to "nv" and not "nvidia",

It may be the mouse, so if that wont work try changing your mouse to "Driver"  "/dev/psaux"

Change one thing at a time . . . 

Press Control and X, to save the file, you'll be prompted to save type y

then type   sudo startx[/QUOTE]

Why are you replying to me?
What info is equisow asking for as far I see I ask info here :confused: 

Guess you misplaced the names ;)

---

### Post by gle041 on 2006-01-11
Ok, I edited what you said, and then typed "sudo startx".

it says "FATAL SERVER ERROR: no screens found"

---

### Post by probe45 on 2006-01-11
I reply myself

[QUOTE=probe45] 

2 options..

sudo dpkg-reconfigure xserver-xorg

Will rebuild your xorg.conf but I doubt it will help

or paste your /etc/X11/xorg.conf here with following info:

- What monitor (brand + size 14" 15" 17" or bigger)
- What Mouse (usb ps2 or serial)
- What keyboard (qwerty, azerty, qwertz etc)
- What videocard (brand and type pci or agp)[/QUOTE]

---

### Post by gle041 on 2006-01-11
I can't type the entire thing, it's quite long. 

Any other ideas?  Or other free operating system suggestions? I really don't want to go back to Windows...

---

### Post by jerrykenny on 2006-01-11
Sorry gle, probe, I'm tired now  

"Why are you replying to me?"

and confused . . . . Bed beckons

---

### Post by probe45 on 2006-01-11
[QUOTE=gle041]I can't type the entire thing, it's quite long. 
[/QUOTE]

cant you upload the file to your webspace? (most if not all isp´s provide there costumers with webspace for a homepage)

---

### Post by gle041 on 2006-01-11
how do I upload the file....i have ftp space

---

### Post by lx638 on 2006-01-11
mind if i bump in?i have the same problem as ^^^

here's the what it says: 

**no screens found**

and i also found these

[B](WW) the directory /usr/share/X11/fonts/cyrillic does not exist
(WW) the directory /usr/share/X11/fonts/CID does not exist
(WW) fonts.dir invalid
(WW) open APM failed (dev.apm_bios) (no such file of directory)[/B]

---

### Post by gle041 on 2006-01-11
what kind of video card do you have?

---

### Post by lx638 on 2006-01-11
shared video from the motherboard only, S3 Pro Savage DDR

---

### Post by gle041 on 2006-01-11
I have a GeForce FX 5200 version 4.34.20.42.D1

---

