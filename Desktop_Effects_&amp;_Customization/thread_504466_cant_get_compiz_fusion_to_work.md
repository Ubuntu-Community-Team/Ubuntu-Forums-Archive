---
title: "cant get compiz fusion to work"
date: 2007-07-19
forum: Desktop Effects &amp; Customization
---

### Post by unseenbeing on 2007-07-19
so basically i have spent 2 hours trying to get this to work with no luck

it installed but doesnt do anything
none of the hot keys do anything, no plugins work

what am i doing wrong

---

### Post by sad_iq on 2007-07-19
When you type in a terminal ```
compiz --replace
``` do you get any error messages???

---

### Post by unseenbeing on 2007-07-19
yes
holy crap
```
daniel@:~$ compiz --replace
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
/home/daniel/.themes/FC-Fino-Dark/gtk-2.0/menubar-custom.rc:40: Unable to locate image file in pixmap_path: "Menu-Menubar/menubar-inactive.png"
/home/daniel/.themes/FC-Fino-Dark/gtk-2.0/menubar-custom.rc:43: Background image options specified without filename
/home/daniel/.themes/FC-Fino-Dark/gtk-2.0/panel_black-plastic.rc:15: error: invalid string constant "panelbuttons-black", expected valid string constant
/home/daniel/.themes/FC-Fino-Dark/gtk-2.0/toolbar-custom.rc:19: error: invalid string constant "toolbar", expected valid string constant
/home/daniel/.themes/FC-Fino-Dark/gtk-2.0/gtkrc:246: Unable to locate image file in pixmap_path: "Toolbar/toolbar.png"
/home/daniel/.themes/FC-Fino-Dark/gtk-2.0/gtkrc:249: Background image options specified without filename

```

---

### Post by sad_iq on 2007-07-19
Do you have the correct driver for your video card installed???
```
glxinfo |grep direct
``` 
And to see what video card you have:
```
lspci |grep vga
```
Paste the output here!

---

### Post by unseenbeing on 2007-07-19
when i do
```
glxinfo |grep direct
```
it says 
direct rendering: no
OpenGL renderer string: Mesa GLX Indirect


nothing happens when i put 
```
lspci |grep vga
```

---

### Post by sad_iq on 2007-07-19
Ok...like I susoected...you don't have your video driver correctly installed...the thing that worries me is that nothing shows up when you type **lspci |grep vga** (It's the first time someone says that line doesn't print anything)...so let's try ```
lspci
``` and paste the result here!

---

### Post by unseenbeing on 2007-07-19
```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:0a.0 CardBus bridge: Texas Instruments PCI1420
00:0a.1 CardBus bridge: Texas Instruments PCI1420
00:0b.0 Ethernet controller: 3Com Corporation 3c556 Hurricane CardBus [Cyclone] (rev 10)
00:0b.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 10)
00:0d.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

```

---

### Post by sad_iq on 2007-07-19
Ok...I think I made a mistake...my command uses lowerspace characters...should have been uppercase ones.
 To install your video driver try **envy**:[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) it should work(most of the times)!

---

### Post by unseenbeing on 2007-07-19
now my xserver just crashed

---

### Post by unseenbeing on 2007-07-19
i need a driver now casue i cant boot

this pisses me off

to late now im sick of this crap not working

im reinstalling 6.10 and not upgrading to feisty

---

### Post by AlexenderReez on 2007-07-19
i think there are few howto in tutorial and tips section about install driver ...mostly in beryl howto...before it guide how to install beryl,it will guide how to install driver...have a lokk at it...i think manually installation is better than envy .....it is difficult either...

---

### Post by unseenbeing on 2007-07-19
i got it back up

i removed some progam and now im back

---

### Post by russo.mic on 2007-07-29
The first thing you should do is go into /etc/X11 try to restore the original xorg.conf.  I've got to believe that the envy install script makes a backup of xorg.conf, although i've never installed it myself.  

you need to install the ATI driver, as you have an ATI video card, hence the last line of the lspic | grep vga

sudo apt-get update

sudo apt-get install xorg-driver-fglrx

sudo aticonfig --initial

sudo aticonfig --overlay-type=Xv

do that from in the terminal, or if you can't logon to X, from the command line and hit startx after all that.
for future reference, the first thing you should do when installing composite managers is possibly 

fglrxinfo

to see if the ati driver is install properly.  if it's not, then that's your first step.  

Russo

---

### Post by sdowney717 on 2007-07-29
ATI is poor choice, Nvidia works for all these extra effects.

Dont you have to use the open source ATI driver for beryl and compiz?
And then you have no 3d acceleration.

I have an ATI 9600 and went thru all this before and the problem is no compositiing available with fglrx?

---

### Post by russo.mic on 2007-07-29
I'm not trying to invalidate the last post, but saying ATI is a poor choice after he's got it installed into his machine isn't very encourging.

Besides, Compiz and Beryl run perfectly fine on my Macbook Pro's ATI X1400 using XGL.  

Don't be discourged!  <in a Rob Schneider voice> You can do it!
!
Russo

---

### Post by unseenbeing on 2007-07-31
new issue
i now own an ibook g3
and i want to run compiz on this. it runs beryl just fine but im wondering if it runs compiz fusion 
i tryed the tutorial that is pinned and it doesnt work

---

### Post by JohnGH on 2007-10-30
> **unseenbeing said:**
> 
nothing happens when i put 
```
lspci |grep vga
```

I think that should be:

```
lspci | grep VGA
```

Because I think the line should be something like:

00:0f.0 VGA compatible controller: (adapter name here) PCI Display Adapter

---

