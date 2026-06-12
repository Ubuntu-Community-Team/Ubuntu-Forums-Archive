---
title: "Help needed please"
date: 2008-12-03
forum: Desktop Environments
---

### Post by brucey1st on 2008-12-03
Hi guys, ive been playing around with ubuntu for the last month (I must say its been a learning curve)

Im on the verge of giving up xp all together, but 1 thing blights my life ....

Screen rez+refresh rate ;/

I install the latest nvidia drivers without problem, ive googled google untill it says i give up lol, but all im trying to do is get my monitors native resolution which is 1440x900@75

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"

# Removed Option "metamodes" "1152x864 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1152x864_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


Can anyone help me out here please?

Cheers

Brucey

---

### Post by Mr Pestle on 2008-12-03
[QUOTE=brucey1st;6302786]Hi guys, ive been playing around with ubuntu for the last month (I must say its been a learning curve)

Im on the verge of giving up xp all together, but 1 thing blights my life ....

Screen rez+refresh rate ;/

I install the latest nvidia drivers without problem, ive googled google untill it says i give up lol, but all im trying to do is get my monitors native resolution which is 1440x900@75



When I installed the drivers I got the menu item System > Administration > NVidia X Server Settings

Which lets me configure all sorts of Graphics settings including native resolution
Have you found this option?

Good Luck

---

### Post by brucey1st on 2008-12-03
Thanx for the prompt reply , yes ive found this, but it doesnt give me my native resolution i require .....

Brucey

---

### Post by benerivo on 2008-12-03
Do you have a widescreen (1440x900) CRT monitor?

Also at this point i'd like to say that some sections of your xorg.conf file are 'duplicated'. For example you have two "Section Monitor" and two "Section Device".

---

### Post by brucey1st on 2008-12-03
Adding to the above my resolution atm is 1152x864@60

Brucey

---

### Post by brucey1st on 2008-12-03
> **benerivo said:**
> Do you have a widescreen (1440x900) CRT monitor?

Also at this point i'd like to say that some sections of your xorg.conf file are 'duplicated'. For example you have two "Section Monitor" and two "Section Device".

Thanx for the reply m8, i have a lcd 19" widescreen monitor

Brucey

---

### Post by Mr Pestle on 2008-12-03
Has the system correctly identified your LCD from "Detect Displays"?
X Server Display Configuration 
My settings =   Model DELL E248WFP (DFP-0 on GPU-0) GPU = GeForce 8600 GT
My Resolution is set to Auto but the drop-down has 1440 x 900
Is it the refresh rate that's your issue? mine's running at 60Hz and I can't see where to change it.

---

### Post by brucey1st on 2008-12-03
> **Mr Pestle said:**
> Has the system correctly identified your LCD from "Detect Displays"?
X Server Display Configuration 
My settings =   Model DELL E248WFP (DFP-0 on GPU-0) GPU = GeForce 8600 GT
My Resolution is set to Auto but the drop-down has 1440 x 900
Is it the refresh rate that's your issue? mine's running at 60Hz and I can't see where to change it.

both

brucey

---

### Post by blackened on 2008-12-03
> **brucey1st said:**
> Thanx for the reply m8, i have a lcd 19" widescreen monitor

Brucey

Ok, but comparing this to your xorg.conf I'm assuming you also have a CRT set up as a secondary display? If not, then you need to totally reconfigure (read, wipe out) xorg to remove the duplicate listings.

I would suggest first:

```
sudo dpkg-reconfigure xserver-xorg
```

This will put xorg.conf back to it's original near-empty state. From there you should add your hsync and vrefresh ranges to the single monitor entry. Don't add anything other than that just yet. Restart X and let's see what crops up from there.

```
sudo /etc/init.d/gdm restart
```
or ctrl+alt+backspace to restart X.

---

### Post by benerivo on 2008-12-03
Your xorg.conf contains a reference to a CRT monitor as well as a line mentioning 1152x864 (along with the duplications i mentioned above). Most lcd monitors need no resolution setting as they are given their defaults automatically. If you are comfortable backing up this file and replacing it then you could back it up and run```
sudo-dpkg reconfigure -phigh xserver-xorg
```for a default xorg file, or just use mine which is a default file plus a line to tell it to use the nvidia driver, plus several lines of nvidia driver Options. If you are not comfortable diong this then i would just change your existing file, so that the 1152x864 lines reads 1440x900. Then reboot. If it fails then do```
sudo nano /etc/X11/xorg.conf
```and change it back and reboot - and post back here.

EDIT - Do you have an secondary display? If so ignore the above instructions.

---

### Post by brucey1st on 2008-12-03
> **benerivo said:**
> Your xorg.conf contains a reference to a CRT monitor as well as a line mentioning 1152x864 (along with the duplications i mentioned above). Most lcd monitors need no resolution setting as they are given their defaults automatically. If you are comfortable backing up this file and replacing it then you could back it up and run```
sudo-dpkg reconfigure -phigh xserver-xorg
```for a default xorg file, or just use mine which is a default file plus a line to tell it to use the nvidia driver, plus several lines of nvidia driver Options. If you are not comfortable diong this then i would just change your existing file, so that the 1152x864 lines reads 1440x900. Then reboot. If it fails then do```
sudo nano /etc/X11/xorg.conf
```and change it back and reboot - and post back here.

EDIT - Do you have an secondary display? If so ignore the above instructions.

Hi i did what you said, and it removed it lol

Section "Screen"

# Removed Option "metamodes" "1152x864 +0+0"
# Removed Option "metamodes" "1440x900_75 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1152x864 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Brucey

---

### Post by brucey1st on 2008-12-03
Soz guys i forgot to mention, i run two pc's through one monitor, through a digital switcher ....

I hope thats not causing the problem?

Brucey

---

### Post by benerivo on 2008-12-03
> **brucey1st said:**
> Soz guys i forgot to mention, i run two pc's through one monitor, through a digital switcher ....

I hope thats not causing the problem?

Brucey

No it shouldn't be. From here i think you should reset your xorg.conf file to the default by opening a terminal and typing```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```this makes a copy of your current xorg. Then do```
sudo dpkg-reconfigure -phigh xserver-xorg
```which will set xorg to the default. Then do```
nano /etc/X11/xorg.conf
```and in 'Section Device' change it to read```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
```

Then press Ctrl+x to save this file. Then preass Ctrl+Alt+Backspace to restart the xserver.

---

### Post by brucey1st on 2008-12-03
Did what you said, and the screen went blank ...

When i restarted i was told nvidia x is not in use etc ...


Brucey

---

### Post by benerivo on 2008-12-03
> **brucey1st said:**
> Did what you said, and the screen went blank ...

When i restarted i was told nvidia x is not in use etc ...


Brucey

OK. Then replace xorg from the command line with```
 sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
``` then restart.

---

### Post by brucey1st on 2008-12-03
Done m8, everythings back to normal ...

Brucey

---

### Post by benerivo on 2008-12-03
Do ```
sudo apt-get install nvidia-xconfig
```then ```
sudo nvidia-xconfig --composite --add-argb-glx-visuals
```then restart.

---

### Post by brucey1st on 2008-12-03
ubuntu is now running in low graphics mode ...


Brucey

---

### Post by benerivo on 2008-12-03
> **brucey1st said:**
> ubuntu is now running in low graphics mode ...


BruceyHmmm. Bugger. Sorry Bruce but i can't help very much further. Just copy the xorg.conf back again with```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```then i would follow the instructions left by Alberto Milone [here]("http://www.albertomilone.com/nvidia_scripts1.html")

---

### Post by brucey1st on 2008-12-03
k m8 nps, (Thanx very much for your help)i have to say its these wee things that stop pc users moving accross imo ...

The only linux distro that reconises my pc is linux puppy, just shows yahs, ah well never mind

Brucey out

---

### Post by shazbut on 2008-12-03
> **brucey1st said:**
> Soz guys i forgot to mention, i run two pc's through one monitor, through a digital switcher ....

I hope thats not causing the problem?

Brucey

I know my my cheap kvm causes an issue like this for me, seems to prevent the monitor reporting its capabilities properly.  I had to use displayconfig-gtk command to force the correct monitor type to get it to work, which I think just puts the relevent info into xorg.conf.

---

### Post by brucey1st on 2008-12-03
> **shazbut said:**
> I know my my cheap kvm causes an issue like this for me, seems to prevent the monitor reporting its capabilities properly.  I had to use displayconfig-gtk command to force the correct monitor type to get it to work, which I think just puts the relevent info into xorg.conf.

Thanx for the reply, i will try that tommorrow when im sober ;)

brucey

---

### Post by brucey1st on 2008-12-03
> **shazbut said:**
> I know my my cheap kvm causes an issue like this for me, seems to prevent the monitor reporting its capabilities properly.  I had to use displayconfig-gtk command to force the correct monitor type to get it to work, which I think just puts the relevent info into xorg.conf.

Just tried it there, command not found ;/

Brucey

---

### Post by shazbut on 2008-12-03
Are you on 8.04?  If so you might need to
```
sudo apt-get install displayconfig-gtk
```

If you're on 8.10 displayconfig might not be an option any more, you might need to read up on the xrandr command. I'd start at this page:
[https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

---

### Post by brucey1st on 2008-12-04
Hi i tried to install "displayconfig-gtk" and it said ....


Package displayconfig-gtk is not available, but is referred to by another package.

btw im using ubuntu 8.10

Is there anything else i can do guys?

Cheers Brucey

---

### Post by blackened on 2008-12-04
Probably 75% of the display problems I've run into have been due to incorrect monitor auto-detection. The easiest way to solve this is by adding the hsync and vrefresh ranges of your particular monitor to xorg.conf. So google the specs for your monitor, or look at its documentation and find the hsync and vrefresh ranges so first

```
gksudo gedit /etc/X11/xorg.conf
```

then plug them in like so:

```
Section "Monitor"
	Identifier	"Configured Monitor"
**	HorizSync          30-82**
**	VertRefresh        56-76**
EndSection
```

Change the bold values to those of your monitor specification (you may have to add the lines themselves, but don't change the identifier line), then restart X with

```
sudo /etc/init.d/gdm restart
```
or ctrl+alt+backspace.

---

### Post by brucey1st on 2008-12-04
Well guys ive sorted the problem :D

I disconnected my dual monitor switcher, then installed wubi on my duel core athlon (Along with xp for now)

I installed nvidia drivers etc ...

Checked my nvidia x server settings, and there it was 1440x900@75 ;)

So the moral of the story is dont use a monitor switcher ...

I have 1 more question in my preferences/screen resolution its reporting my refresh rate different from nvidia x server settings? altho if im right nvidia x overrides that?

So atm im having a complete ball lol, ive just installed compiz fusion, and wine, and im away to try call of duty 2/3 :D

Cheers Again

Brucey

---

