---
title: "DELL XPS M1730 dual NVIDIA SLI"
date: 2008-01-26
forum: Dell  Ubuntu Support
---

### Post by Petengy on 2008-01-26
Hi to all

I'm trying to install Ubuntu 64 bit on my XPS but really nothing to do... live cd doesn't start.
I suppose there are problems with nvidia drivers (SLI configurations).

If someone was able to install it please write here HOW... I'm very sad :(

really TnX

Pet

---

### Post by macabro22 on 2008-01-27
bump!

---

### Post by rogi on 2008-01-27
I had to use the Alternate CD on my M1330.  The normal x86 desktop CD wouldn't recognize the HDD, and gave me some graphics problems.  After the install it all ran great.  HTH

---

### Post by Petengy on 2008-01-27
dear ROGI

TnX for your answer, I'll try using the alternate CD.

I'll post all results :)

Tnx

Pet

---

### Post by Petengy on 2008-01-30
Dear Rogi

I used the Alternated CD but I wasn't able to choose the right way to create a partition because I want keep Vista on my HD, so I don't want erase eveything.
I'm trying to install Ubuntu in dualboot with vista, if it's possible, I have to find the way

at the moment ...no way.....

---

### Post by Petengy on 2008-01-30
if someone was able to "put" ubuntu and vista togheter on xps m1730 please write here how :)

---

### Post by macabro22 on 2008-01-30
> **Petengy said:**
> if someone was able to "put" ubuntu and vista togheter on xps m1730 please write here how :)

Alright!

I've done it last night!

I got my Dell XPS m1730 to dual boot with Ubuntu 64 bits and Windows Vista.

I am glad to say almost everything worked out of the box after struggling with the video card drivers. (wi-fi, audio playback and the video camera!)

I also got Compiz-fusion working with all the extra plugins.

Later on, when I get home from work I can post you guys my xorg.conf so you get everything going.

Here's what you have to do: from another computer download the ENVY deb file: [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

When the boot sequence locks up, change to another terminal instance (i.e. CTRL + ALT+ F#).

Then unpack the deb file by adding this to the path where you have your file (i.e. cd /media/disk if you have a regular pendrive):

```
sudo dpkg --intall envy_0.9.10-0ubuntu2_all.deb
```

Then edit your /etc/X11/xorg.conf file and save it with the crap I will post here later.

```
 

#

Section "Device"
    Identifier  "nVidia0"
    Driver      "nvidia"
    VendorName  "nVidia Corporation"
    BoardName   "GeForce 8700M GT"
#    BusID	"PCI:3:0:0"
    Option	"NvAGP"		"0"
    Option	"SLI"		"auto" 
    Option	"NoLogo"	"false"
    Option	"BackingStore"	"true"
    Option "UseCompositeWrapper" "true"
    Option "AddARGBGLXVisuals"	"true"
    Option      "DamageEvents"	"false"
EndSection

Section "Device"
    Identifier  "nVidia1"
    Driver      "nvidia"
    VendorName  "nVidia Corporation"
    BoardName   "GeForce 8700M GT"
#    BusID	"PCI:4:0:0"
    Option	"NvAGP"		"0"
    Option	"SLI"		"auto" 
    Option	"NoLogo"	"false"
    Option	"BackingStore"	"true"
    Option "UseCompositeWrapper" "true"
    Option	"DamageEvents"	"false"
EndSection

Section "Module"
    Load	"dbe"
    Load	"glx"
    Load	"extmod"
    Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"

#

Section "Device"
    Identifier  "nVidia0"
    Driver      "nvidia"
    VendorName  "nVidia Corporation"
    BoardName   "GeForce 8700M GT"
#    BusID	"PCI:3:0:0"
    Option	"NvAGP"		"0"
    Option	"SLI"		"auto" 
    Option	"NoLogo"	"false"
    Option	"BackingStore"	"true"
    Option "UseCompositeWrapper" "true"
    Option "AddARGBGLXVisuals"	"true"
    Option      "DamageEvents"	"false"
EndSection

Section "Device"
    Identifier  "nVidia1"
    Driver      "nvidia"
    VendorName  "nVidia Corporation"
    BoardName   "GeForce 8700M GT"
#    BusID	"PCI:4:0:0"
    Option	"NvAGP"		"0"
    Option	"SLI"		"auto" 
    Option	"NoLogo"	"false"
    Option	"BackingStore"	"true"
    Option "UseCompositeWrapper" "true"
    Option	"DamageEvents"	"false"
EndSection

Section "Module"
    Load	"dbe"
    Load	"glx"
    Load	"extmod"
    Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia0"
	Monitor		"LCD"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1920x1200"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
        screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia0"
	Monitor		"LCD"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1920x1200"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
        screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection


```

Or else you can find out how to edit xorg.conf yourself at the nVidia forums or ask for help at #compiz at irc.freenode.net.

reboot and you're good to go!

P.S. If your kernel updates you will have to do this again to fix your video drivers. (This will probably happen right away, since you will want to update your system after getting it going for the first time.)

---

### Post by Petengy on 2008-01-30
dear dear DEAR MACABRO22  :KS

you don't know how you make me happy :) :) to know that is possible to install ubuntu on our machines .. really happy

Only I wasn't able to start the live CD .... during the booting (of the live CD) all stop (freeze) and I don't know how to go on.

I tryed using the alternate cd but vista doesn't make me able to create partitions, so I don't know where to put ubuntu.


Didn't you had any trouble to start the live cd ? How you was able to install Ubuntu ? :confused: :confused:


TnX a Lot for the answer 
Pet

---

### Post by macabro22 on 2008-01-31
> **Petengy said:**
> dear dear DEAR MACABRO22  :KS

you don't know how you make me happy :) :) to know that is possible to install ubuntu on our machines .. really happy

Only I wasn't able to start the live CD .... during the booting (of the live CD) all stop (freeze) and I don't know how to go on.

I tryed using the alternate cd but vista doesn't make me able to create partitions, so I don't know where to put ubuntu.


Didn't you had any trouble to start the live cd ? How you was able to install Ubuntu ? :confused: :confused:


TnX a Lot for the answer 
Pet

Yes! I did. Just be patient with the cd(it should take around 5-10 minutes for the message to appear) and wait for a message to popup on the black screen saying it couldn't detect your video resolution or something of the kind. 

Then choose start in low resolution mode and Install ubuntu.

After restarting you will get locked up at boot. Then do what I posted previously.

I am sorry if thats confusing. I should have posted that previously.

Cheers

---

### Post by Petengy on 2008-01-31
dear macabro22

My problem is that after choosing "start in low graphic mode" the boot process stops at "Running local boot scripts (/etc/rc.local)

and nothing happen  :confused:

---

### Post by macabro22 on 2008-01-31
> **Petengy said:**
> dear macabro22

My problem is that after choosing "start in low graphic mode" the boot process stops at "Running local boot scripts (/etc/rc.local)

and nothing happen  :confused:

Petengy,

Yeah, now I remember! What you do now is hit ctrl + alt + f3.
This will bring you to another command line session.

There you type "gdm" to start gnome. Install ubuntu, then do the stuff I posted before.

Hope that helps!

Tell me how it goes.

---

### Post by macabro22 on 2008-01-31
Doodes,

You will also notice there's no boot splash screen!

Here is a fix I found! [http://www.lodemenos.net/SOLVED-Boot-Usplash-Black-Screen.html]("http://www.lodemenos.net/SOLVED-Boot-Usplash-Black-Screen.html")

Now all that rests to fix is the microphone. I can't get any sound input at all. Wether from the internal or external mic.

---

### Post by Petengy on 2008-02-01
dear macabro

I'm at work now... but I really want to get home to try your solution ... :)

at the moment tnx again.... I'll tell you

Pet

---

### Post by Petengy on 2008-02-02
hi macabro

so, your suggestions were very useful, I was able to start the live CD, after CTR+ALT+F3 I was able to start the GUI by  startx command.

so really TnX

BUT.... the next step is to create a partition to put Ubuntu in it.

As You can see in the attcachment, Dell sell his laptop partioning the HD in 4 parts (logical partiotns) and using the utility  inside Vista is not possible to create others one...

Gparted doesn't see anything, no partitions on my HD.....

So next step is create a space for Ubuntu whit out erase existing partitions, that mean reinstall the configured OS...

I will do it ... I will 

TnX again
Pet

---

### Post by macabro22 on 2008-02-02
> **Petengy said:**
> hi macabro

so, your suggestions were very useful, I was able to start the live CD, after CTR+ALT+F3 I was able to start the GUI by  startx command.

so really TnX

BUT.... the next step is to create a partition to put Ubuntu in it.

As You can see in the attcachment, Dell sell his laptop partioning the HD in 4 parts (logical partiotns) and using the utility  inside Vista is not possible to create others one...

Gparted doesn't see anything, no partitions on my HD.....

So next step is create a space for Ubuntu whit out erase existing partitions, that mean reinstall the configured OS...

I will do it ... I will 

TnX again
Pet

There's an option to use a partition's free space. Thus, you may choose Vista's partion and resize it so Ubuntu takes a quota out of it. I choose half the size. You can do the same. That way there's enough disk space to install linux applications in the Ubuntu partition and games in the Vista one.

Look carefully not to erase anything.

---

### Post by bongey on 2008-02-02
I have most of everything working on the xps 1730 go to this forum for more [http://ubuntuforums.org/showthread.php?p=4257333](http://ubuntuforums.org/showthread.php?p=4257333) .

---

### Post by Petengy on 2008-02-03
hi bongey

your thread and the macabro instructions are like gold for me,I was able to get ubuntu properly working _using the live CD_.

Next step, now, is to create a partition on xps1730 HDs without erase the existing ones (the ones Dell make when they sell their machine), because now I want _install Ubuntu definitively on HD_ and make a dualboot with vista. 

Vista has a utility to shrink partitions and then, in theoretically way ,create a new one, but after I had shrinked the C: partition (data partition where there's the OS) vista doesn't permit to allocate it, because it seems not more then 4 partitions are allowed.

Not only but Gparted doesn't see anything on xps HDs, no partitons , nothing...

Now I'm trying to find a solution in another forum (in italian language) to see if it possible to allocate a new partition leaving untouched the already created by dell.

I had attached a example partitions created by dell on xps.

After that, if all will get right, I'll post a complete wiki in my forum that I have created for dell XPS M1730.

My "dream" is to make possible to me and the peoples that have a xps1730 to install ubuntu without  touch the dell's installation CDs to recreate or reinstall OS, drivers or Media direct suite.

---

### Post by bongey on 2008-02-03
Are you running a raid setup ?  I have a single drive .  

Here is one way to do it [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first) 

The only thing is the dell media direct partition might get messed up. 
Notice I don't run windows vista , and if you are putting windows on there for games, you will get better performance with xp.( I have it dual boot windows xp/linux and xp flies on it ) with this kind of boot [http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)  . Works fine you will have to slip stream the intel drivers , something like this [http://www.msfn.org/board/Unattended-install-SATA-drivers-Floppy-t13173.html](http://www.msfn.org/board/Unattended-install-SATA-drivers-Floppy-t13173.html).

---

### Post by bongey on 2008-02-03
Here is a link with media direct  and such [http://forum.notebookreview.com/archive/index.php/t-103281.html](http://forum.notebookreview.com/archive/index.php/t-103281.html)

---

### Post by Petengy on 2008-02-03
dear bongey

I'm reading now your messages, I'll tell you.

for now TnX a lot :) :)

PS
I have 2 raid HDs.

---

### Post by Petengy on 2008-02-15
Finally I solved my ubuntu problem installing it on a external usb HD.
I done a "how to" .......


Really TnX to all (Macabro and Bongey) for your answers...

---

### Post by macabro22 on 2008-02-15
> **Petengy said:**
> Finally I solved my ubuntu problem installing it on a external usb HD.
I done a "how to" .......


Really TnX to all (Macabro and Bongey) for your answers...

Petengy, 

Please let me know if your microphone works.

---

### Post by Petengy on 2008-02-18
Dear Macabro

You're right, mic doesn't work. I spent these 2/3 days to find a way to fix it, but nothing was done ... sorry.

If I found something I'll post you. :)

---

### Post by Petengy on 2008-02-23
not solutions found yet... and you ??

---

### Post by macabro22 on 2008-02-25
Nope.
I think it might be fixed in Feisty, since it will have the latest ALSA drivers.

---

