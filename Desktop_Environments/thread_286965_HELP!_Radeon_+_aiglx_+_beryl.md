---
title: "HELP! Radeon + aiglx + beryl"
date: 2006-10-28
forum: Desktop Environments
---

### Post by japatoo on 2006-10-28
I have got an ibm thinpad t41, it has a Mobility Radeon 9000 in it.  I installed ubuntu 6.10 yesterday and want to run Beryl on it. Therefor i followed the instructions on [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)

But if i execute beryl or beryl-manager, the desktop and panels are messed up.  They're both missing a third or so.  The right part where studd is missing doesn't redraw.  And the desktop is white.  The windows are fine though.

The blurfx plugin doesn't work, though I thought my Radeon 9000 supports fragment shaders?  Or maybe it doesn't?  Or it's the opensource drivers?

Anyhoo, I'm hoping to get it to run at a usable level soon. 

my xorg.conf:

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option          "XAANoOffscreenPixmaps"
EndSection

i added the option "XAANoOffscreenPixmaps" by myself but it does not effect anything

hope someone can help me.

tom

---

### Post by happy-and-lost on 2006-10-28
Have you installed the ATi driver with any luck?

So far I've been unable to install it under Edgy, you may have to wait a few weeks for that to be fixed.

---

### Post by davec64 on 2006-10-28
Exactly the sane problem!

I've tried modding my xorg to include:

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R100 QD [Radeon 7200]"
	Driver		"radeon"
	Option 		"DRI" "true"
	Option 		"ColorTiling" "on"
	Option 		"EnablePageFlip" "true"
	Option 		"AccelMethod" "EXA"
	Option 		"XAANoOffscreenPixmaps"
	Option 		"RenderAccel" "true"
#	Option 	"AGPMode" "x" <- x may be 2 or 4 depending on your system
	Option 		"AGPFastWrite" "on" 
	BusID		"PCI:1:0:0"
EndSection

I'm just about to try:

section "Extensions"
Option "Composite" "false"
EndSection

I'll post back and tell you if that makes a difference!

---

### Post by happy-and-lost on 2006-10-28
If you really need it, go back to Dapper. I am. There are too many enormous bugs in Edgy which make life difficult. They should be sorted within a few weeks, but I need stability and useability now. :(

---

### Post by davec64 on 2006-10-28
I've tried the second mod to xorg:

> 
section "Extensions"
Option "Composite" "false"
EndSection


That just crashed X!!!!

Anybody else got any suggestions?
I'm enjoying the tinkering, but as far as I'm concerened it's not time for me to updrade to edgy on my main machine!

---

### Post by japatoo on 2006-10-29
> 
@ happy-and-lost: Have you installed the ATi driver with any luck?

i thought the ATi Proprietary Linux Driver did not support aiglx...
so i have not tried to install it yet

apart from the beryl thing i am highly pleased with edgy. i switched from suse linux 10.1 over to edgy and i am actually very surprised at the good hardware detection and software presettings compared with suse. i can not believe that i spent several hours on tinkering with suse to get the volume and brightness osd and the special keys run. ](*,)  edgy support that by default. 

thanks for your help so far. hope the ubuntu team get the mentioned aiglx/beryl bug fixed

---

### Post by rsm75 on 2006-11-10
to fix the desktop clipping problem with the radeon... 

I hunted for quite a while, until I finally found a user who had the same problem with desktop clipping that I did and found a way to fix it by using the drirc file.  It didn't work for me, but after a bit more of troubleshooting, it looks like dri uses two drivers (learned from dri.freedesktop.org), r200 and radeon.  You can find out which one your card is using by typing "xdriinfo" in a terminal.  After that, put this drirc file into your /etc/ directory, reboot, and presto, should work.  Substitute the driver attribute with whatever is appropriate.  for my Mobility 9000, it is r200.

<driconf>
        <device screen="0" driver="r200">
                <application name="all">
                        <option name="allow_large_textures" value="2" />
                </application>
        </device>
</driconf>

just fyi however, i did all this in FC6, I assume it'll work the same for Ubuntu, but you never know.

---

### Post by lognok on 2006-11-10
Hi rsm75, just tested your suggestion on my Ubuntu Edgy [IBM R51 ATI M9000] and now my problems are solved.
Created the file 'drirc' in /etc/ and pasted your code in:

<driconf>
<device screen="0" driver="r200">
<application name="all">
<option name="allow_large_textures" value="2" />
</application>
</device>
</driconf>

and started beryl-manager.

 No more 1/3 of the screen black and no white wallpaper.

It's just super duper now, thanx a lot.

---

