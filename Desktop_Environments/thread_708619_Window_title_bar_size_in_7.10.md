---
title: "Window title bar size in 7.10"
date: 2008-02-26
forum: Desktop Environments
---

### Post by RickyOswaldIOW on 2008-02-26
Greetings,  I am sorry if this is a common issue but I have done a forum and google search without any results but here is my problem:  I am new to Ubuntu 7.10, installation was like a dream but at the login screen, the text is roughly 5x larger than the text box so as I type in my username and password, I cannot really read back what I have typed.  This problem carries over to the desktop where the text in the title bar of each window is also redicuously large.  This problem did not occur when using the Live CD, I can remedy the issue by going to System > Preferences > Appearance > Visual Effects and selecting 'None'.  I can also go back to Normal after this and everything remains the correct size until I reboot!

---

### Post by Sam Lars on 2008-02-26
This sounds really familiar... I remember seeing a bug report about it, but I can't find it now...
What is your DPI setting for fonts in the Appearances window?  If you change that, does it help?

---

### Post by RickyOswaldIOW on 2008-02-26
I'm not sure what the DPI font settings are but if I go into System > Preferences > Appearance > Fonts, WIndow Title Font is set to Sans Bold | 10 (the default) and all the others are Sans | 10.  As I say, this is a fresh install of the OS and I've not fiddled with anything.

---

### Post by Sam Lars on 2008-02-26
Sorry, it's in Details from that window.

---

### Post by RickyOswaldIOW on 2008-02-26
The resolutions right now is 96 dpi, I'll reset and see if it changes.

---

### Post by RickyOswaldIOW on 2008-02-26
The dpi is unchanged...

---

### Post by erginemr on 2008-02-26
Hmm, Live CD works OK, but installed system does not. It seems this is a graphics card driver issue. What video card are your using? And wehat is the outcome of the following command from a terminal?
```
lspci | grep -i VGA
```

Can you please post your /etc/X11/xorg.conf file here?

Please refer to this post of mine, which may (or may not) help:
[http://ubuntuforums.org/showpost.php?p=4222227&postcount=10](http://ubuntuforums.org/showpost.php?p=4222227&postcount=10)

And the thread where it belongs to:
[http://ubuntuforums.org/showthread.php?t=679257](http://ubuntuforums.org/showthread.php?t=679257)

---

### Post by sstusick on 2008-02-27
The bug for this has been fixed. Run the system updates.

---

### Post by erginemr on 2008-02-27
Alternatively, you mentioned that the problem is gone when you disable the visual effects. This might be a bug related to Compiz Fusion (but not the gdm screen). Please follow this post to update Compiz to the latest version:

[http://ubuntuforums.org/showpost.php?p=4364190&postcount=16](http://ubuntuforums.org/showpost.php?p=4364190&postcount=16)

---

### Post by RickyOswaldIOW on 2008-02-27
> The bug for this has been fixed. Run the system updates. I have all of the most recent updates but the problem persists.

For some reason, if the first application I load is Mozilla Firefox and I click on "Restore Session", the titles are all normal sized!  If I load a different application before this or if I do not have the option to restore a session I get the described problem.


I am using a Radeon 9250 AGP card and the output is
```

01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)

```
I have run CSS using WINE quite well so I don't think it's a driver issue here.  Also, my display size is pretty low and I was getting the issue at 640x480 if I recall correctly.
On top of this, it appears that I cannot get to the standard 4:3 aspect ratios beyond 800x600, I'd expect to se 1024x768 and such but instead I am running at 1152x768 as 800x600 is too big for my liking...

---

### Post by RickyOswaldIOW on 2008-02-27
Following these instructions to reduce the dpi of the font at the login screen has also had the side effect of reducing the size of the font in the title bars of the windows but it is still about twice as large as the standard size.
> 
If you also want small fonts on the GDM login window, you can do this:
1. Open System->Administration->Login Window
2. Select the 'Security' tab
3. Click the 'Configure X-Server' button
4. Append '-dpi 96' (without quotes) to the text in the 'Command' field"


---

### Post by erginemr on 2008-02-27
* OK. Please follow my previous thread and enable backports to see if it helps.

* Also does this problem disappear (both at gdm login screen and on the desktop) when you disable Compiz Fusion and restart your computer?

* What brand is your monitor? Is it standard size (4:3 as you mentioned) or wide-screen (16:9)? What is its natural resolution?

* Finally, please post your xorg.conf file by using:
```
gedit /etc/X11/xorg.conf
```

---

### Post by erginemr on 2008-02-27
> **RickyOswaldIOW said:**
> Following these instructions to reduce the dpi of the font at the login screen has also had the side effect of reducing the size of the font in the title bars of the windows but it is still about twice as large as the standard size.

Does your gdm login screen have normal font sizes now? 

Also, try making all fonts 1 px from Appearance -> Fonts and reboot to bring them back to 10 px. I know that it sounds like a stupid idea, but this might reset font settings in Gnome.

---

### Post by /usr/bin/hacked? on 2008-02-27
I had that same problem! When I would try to install from the cd it would do that, but then I installed the 7.04 version, and then upgraded it to 7.10, and it worked fine. I don't know if this is feasible for you or not, but there is my input.

---

### Post by RickyOswaldIOW on 2008-02-27
> Does your gdm login screen have normal font sizes now?   Yep, simply adding the -dpi 96 to the command line fixed that.  I did not try disabling Compiz Fusion as enabling the repositries and installing the updates seems to have fixed the problem!  Thanks very much for the help on that issue :)

Regarding the monitor aspect ration, I am using an old 17" CRT monitor (it's a flavour of Logix) and it's most definately a 4:3 ratio monitor.  The screen resolutions that I am presented in System > Preferences > Screen Resolution are:
640 x 480
800 x 600
1152 x 768
1280 x 800
1280 x 960

It is also stuck on 55Hz whereas windows detected it to be 60Hz if I remember correctly.

Also, thanks to /usr/bin/hacked? for the suggestion :)  (P.S. love your name).

---

### Post by erginemr on 2008-02-27
Great News! I am glad that you have solved your problem. :)

But I still would like to see your xorg.conf file by copying what is inside "gedit /etc/X11/xorg.conf" and pasting it here. Maybe we can also solve your resolution problem.

Don't heed what the "Screens & Resolutions" tool reports. It is buggy and does not report your refresh rate (55 Hz) correctly. And I wouldn't suggest using it to manage your screen resolution either.

---

### Post by RickyOswaldIOW on 2008-02-27
Well, can't say you didn't ask for it...
```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

```

Enjoy :)

I've also just noticed an error in one of my posts:
> 
Regarding the monitor aspect ration

ofc **ration** should be **ratio**

---

### Post by erginemr on 2008-02-27
Let me concentrate...

Hmm... Let me see:

ITEM I:
---------
```
Option		"XkbLayout"	"gb"
```
You are from Great Britain. (Genius I am ;))

ITEM II:
----------
```
Driver		"ati"
```
You are using the open source driver. I am not sure if your card is supported, but when this problem of yours is over, you may consider refering to:
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)
to install the binaty ATI driver, which will also enable Compiz Fusion (desktop effects).

ITEM III:
-----------
```
SubSection "Display"
	Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480" "640x350"
EndSubSection
```
You may consider dropping "1280x1024" from this list, leaving you with "1024x768" as the desktop resolution.

You may also consider adding a line for "MetaModes" to your "Device" section, whose duty is to force-select a specific resolution from the above given res. list.
```
Section "Device"
    ...........
    Option       "MetaModes" "1024x768"
EndSection
```

ITEM IV:
----------
```
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
```

You will receive a great deal of money very soon. You will meet someone and go on a journey with her. :^o

---

### Post by RickyOswaldIOW on 2008-02-28
Item I:  Quite an assumption, maybe I have a UK keyboard or I have it set up incorrectly :P

Item II:  This seems like a good course of action as indeed, I am reported to have a 9200 which in fact I have a 9250.

Item III:  Using the sudo command I have edited the file to drop the "1280x1024" from Modes and also included the MetaMode into the correct area.  I cannot say that I can see any difference but if the ScreenResolution tool can report incorrectly then maybe I am already on 1024x768 and it is simply displaying the wrong numbers!

Item IV:  Don't tell my wife!



  Also, my title bars are still about twice they size they should be and I have to go into the Apperance and change it as I described earlier although it is a lot more manageable now and does not really bother me.

---

