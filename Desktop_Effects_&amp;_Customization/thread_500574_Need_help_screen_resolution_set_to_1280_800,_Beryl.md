---
title: "Need help: screen resolution set to 1280 800, Beryl stopped working.  Related ?"
date: 2007-07-14
forum: Desktop Effects &amp; Customization
---

### Post by tomaasj on 2007-07-14
Need some help,

Beryl stopped working.  The icon is still there in the bar and reacts to the right-click mouse button.  I am not able to select Window manager from Metacity (default) to Beryl.  After a re-install of Beryl (using the terminal or Synaptic, tried both) I was able set the window manager to Beryl but then the screen flickers and nothing happens.

These problems occured after I solved the screen resolution issue which seems to be a topic with my Dell laptop.  Highest was 1024 768, but after installing a patch (see below) I am now able to run the laptop with a 1280 800 resolution.  Before finding the patch, I was tinkering with a file named xorg.conf in /etc/X11 (followed advice form a thread here in the forums).  I made a backup of the xorg.conf file in the directory etc/X11.  Following tinkering with xorg.conf file, the resolution was not solved, so I replaced the altered xorg.conf file with the backup I made.

Maybe the two issues are not related but think it prudent to mention what I was doing before I noticed that Beryl was not behaving as it should.

Is there somebody here to get Beryl running on my laptop again ?

Thanks in advance,

Tomaasj


My laptop:

Inspiron 6400 Dual Core Processor T2080 (1.73GHz,1MB L2 cache, 533MHz)
15.4" Wide Screen WXGA (1280 x 800) TFT Display
Intel Media Accelerator 950 Graphics Up to 256MB shared graphics memory

used this link to get my screen resolution fixed to 1280 800:
[http://www.cyberciti.biz/tips/howto-linux-dell-inspiron-1280x800-screen-resolution.html](http://www.cyberciti.biz/tips/howto-linux-dell-inspiron-1280x800-screen-resolution.html)

---

### Post by duydaniel on 2007-07-14
> **tomaasj said:**
> Need some help,

Beryl stopped working.  The icon is still there in the bar and reacts to the right-click mouse button.  I am not able to select Window manager from Metacity (default) to Beryl.  After a re-install of Beryl (using the terminal or Synaptic, tried both) I was able set the window manager to Beryl but then the screen flickers and nothing happens.

These problems occured after I solved the screen resolution issue which seems to be a topic with my Dell laptop.  Highest was 1024 768, but after installing a patch (see below) I am now able to run the laptop with a 1280 800 resolution.  Before finding the patch, I was tinkering with a file named xorg.conf in /etc/X11 (followed advice form a thread here in the forums).  I made a backup of the xorg.conf file in the directory etc/X11.  Following tinkering with xorg.conf file, the resolution was not solved, so I replaced the altered xorg.conf file with the backup I made.

Maybe the two issues are not related but think it prudent to mention what I was doing before I noticed that Beryl was not behaving as it should.

Is there somebody here to get Beryl running on my laptop again ?

Thanks in advance,

Tomaasj


My laptop:

Inspiron 6400 Dual Core Processor T2080 (1.73GHz,1MB L2 cache, 533MHz)
15.4" Wide Screen WXGA (1280 x 800) TFT Display
Intel Media Accelerator 950 Graphics Up to 256MB shared graphics memory

used this link to get my screen resolution fixed to 1280 800:
[http://www.cyberciti.biz/tips/howto-linux-dell-inspiron-1280x800-screen-resolution.html](http://www.cyberciti.biz/tips/howto-linux-dell-inspiron-1280x800-screen-resolution.html)


Hi Tomaasj.
First, I am noob... and I used to follow too many guide line ==> eventually, my system messed up. 

After I reinstall Ubuntu... tgm4883 gave me the following and it worked.

> sudo apt-get install 915resolution
then do ctrl-alt-backspace

Compiz fusion guide
[http://ubuntuforums.org/showthread.p...=compiz+fusion](http://ubuntuforums.org/showthread.p...=compiz+fusion)


Is there anyway that you could restore your driver card as it was after the fresh installation?
Then you just need to type in terminal:

sudo apt-get install 915resolution
then do ctrl-alt-backspace

It works perfectly with mine.

Then you try to uninstall Beryl and install Compiz by the link above.
As I know, Compiz is better than Beryl and work perfectly with my laptop which is the same specs as yours.

---

### Post by hyperair on 2007-07-15
So it seems that you've installed 915resolution and then Beryl refused to work again eh. Do you have copies of your xorg.conf before and after you installed 915resolution? I'd like to take a look at both of them.

As a side note I think you might want to know : [http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/). In Gutsy, you won't need 915resolution anymore.

---

### Post by tomaasj on 2007-07-15
Can anybody give suggestion how to solve problem ?

My xorg.conf file:

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection

Section "ServerFlags"
Option "AIGLX" "off"
EndSection

---

### Post by hyperair on 2007-07-15
Wait, this file is the one currently running? Sorry I mixed them up earlier. Could you remove this portion from the file:
```

Section "ServerFlags"
Option "AIGLX" "off"
EndSection

```

and then restart your X server and try again?

---

### Post by tomaasj on 2007-07-15
question: restarting X server is CTRL-Alt-Backspace ?

---

### Post by tomaasj on 2007-07-15
Hi,

removed the mentioned section from the xorg.conf file, restarted computer, but to no avail.  Desktop effects could not be enabled and Beryl window manager  setting to Beryl results in flickering of screen and nothing else.

What to do ?

gr. Tomaasj

---

### Post by hyperair on 2007-07-15
And the output of beryl --replace yields the same thing? Damn. What could be your problem I wonder.. Could you check if you have a folder "/usr/lib/fglrx" and post what are the contents?

---

### Post by tomaasj on 2007-07-15
contents of the folder are:

libGL.so.1.2.xlibmesa  libGL.so.1.xlibmesa


beryl --replace:

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : failed

Support for non power of two textures missing

---

### Post by hyperair on 2007-07-15
Excellent! I saw a fix somewhere...  Run this in the terminal:

```

LD_PRELOAD=/usr/lib/fglrx/libGl.so.1.2.xlibmesa beryl --replace

```

For the record, I got this fix from [http://ubuntuforums.org/showthread.php?t=352350](http://ubuntuforums.org/showthread.php?t=352350)

It's supposedly for ATi cards, as fglrx is a driver for ATi cards. I don't know why that folder exists on your system. Also, when you typed glxinfo, there were snippets of ATi stuff there. Again, I don't understand that, but try the fix anyway.

---

### Post by duydaniel on 2007-07-15
Here is my xorg.conf file: Intel 945GM and it works fine with Compiz Fusion with all the effects. However, I found that when I play mp3 by "Movie Player" the screen does not show the visual effects, it is choppy, but most time, it blank (dark)... :confused:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by tomaasj on 2007-07-15
Hi,

I immediately tried the fix, but still the same result.  Also, beryl --replace gave the same output as before.  

I dread the moment I have to replace my system with the backup.  Alot of work went into it since I did it 2 months ago.

Hopefully there are options left.

gr. Tomaasj

---

### Post by hyperair on 2007-07-15
@duydaniel: I'm not really sure, but I also face that problem on my computer, and it's running nVidia. Since this is almost completely unrelated, you should go post in another thread. You'd have more luck of someone helping you out that way. In my case, the visualizations lagged my entire computer, so i just turned it off. My primary music player is JuK anyway.

@tomaasj: I certainly hope so too. You say that it worked before you installed 915resolution and immediately after installing 915resolution Beryl refused to work again?

---

### Post by tomaasj on 2007-07-15
> **hyperair said:**
> 

@tomaasj: I certainly hope so too. You say that it worked before you installed 915resolution and immediately after installing 915resolution Beryl refused to work again?

That, plus the fact that I tinkered with the xorg.conf file using some advice on the threads to solve the resolution issue: to get it to 1280 800.

---

### Post by tomaasj on 2007-07-15
Hyperair,

tinkering involved, if I recall correctly NVIDIA files.  I removed everyhting related to that.  The only file which synaptic refuses to remove is: NVIDIA binary XFree86 4.x/X.Org driver

could this be related to the problems I'm having ?

Tomaasj

---

### Post by hyperair on 2007-07-15
Good grief. I have no idea, really. Could you find ALL or at least most of the advice you followed before it screwed up? Because you don't need much tinkering in your system to get your resolution. Just install 915resolution and it should work. Chances are the tinkering you had done previously caused Beryl to stop working.

---

### Post by tomaasj on 2007-07-15
is there a log somewhere which logs all the typing in the terminal ?  Maybe I am able to find some of the typing stuff I did...

---

### Post by duydaniel on 2007-07-15
My system graphic works properly now... since I went to synaptic and install the intel chip. I don't remember... just go to synaptic and type Intel (selected Name and Description)... then you will see an item which has i945. Then install it... the system then ask you to remove the old one.

Then... just try to remove the Beryl and install compiz fusion.
[HTML]http://ubuntuforums.org/showthread.p...=compiz+fusion[/HTML]

It should be working.
If it still not work, please consider to reinstall Ubuntu, that is what I thought, though I am noob here... but after a clean reinstall and install the intel chip -> compiz fusion -> work like charm with me.

---

### Post by tomaasj on 2007-07-16
I already tried to do a clean install.  If I get it running again I certainly try.  I'll let you know if it worked.

Thanks,

gr. Tomaasj

---

### Post by hyperair on 2007-07-16
So it's come to the clean install eh.. Don't forget to install 915resolution, and don't tweak your xorg.conf too much. As far as I know, Intel cards work with Beryl without needing any tweaking.

---

### Post by duydaniel on 2007-07-16
Yes... it works without any modifying the xorg.conf in my case.
Have you scan your Ubuntu CD for error?

---

### Post by tomaasj on 2007-07-16
:confused:  To make it even worse (I write this from Vista !) a worse-case Backup scenario has materilized:  

Made my last backup using Ghost.  Write my partitions as an Image to an external hardrive.  My laptop hardrive is divided in several partitions each having its own function eg  one has Vista, one has Ubuntu an another contains data.  I have a dualboot system on my laptop so I thought I was set.

Now disaster struck:  yesterday I used Ghost to write the Ubuntu Backup onto the partition of my laptop, everything OK but the moment I rebooted the laptop, choose Ubuntu,  see the Ubuntu bar, reboot FAILS !  

Doing it again, I noticed that Ghost wants to setup a ext2 filestructure on my partition which originally has an ext3 filestructure.  The external hardrive is NTFS.  I am not an expert but I think this is NOT GOOD.

Dreading the idea to setup everything from scratch: partioning harddisk, setup Ubuntu, Vista (my backup to allow me to control the laptop), etc. takes a lot of effort,

escpecially since 1) there are some conflicts with Vista.  Ubuntu does not load unless something has to be done with the bootloader etc.  and 2) wireless and Dell Inspiron and Ubuntu are not compatible.  I recall a lot of time and effort from IT expert to set it up for me.

I am depressed...

[-o< Can somebody suggest a way out ?  A terminal prompt appears when Ubuntu fails to boot...

---

### Post by duydaniel on 2007-07-16
> **tomaasj said:**
> :confused:  To make it even worse (I write this from Vista !) a worse-case Backup scenario has materilized:  

Made my last backup using Ghost.  Write my partitions as an Image to an external hardrive.  My laptop hardrive is divided in several partitions each having its own function eg  one has Vista, one has Ubuntu an another contains data.  I have a dualboot system on my laptop so I thought I was set.

Now disaster struck:  yesterday I used Ghost to write the Ubuntu Backup onto the partition of my laptop, everything OK but the moment I rebooted the laptop, choose Ubuntu,  see the Ubuntu bar, reboot FAILS !  

Doing it again, I noticed that Ghost wants to setup a ext2 filestructure on my partition which originally has an ext3 filestructure.  The external hardrive is NTFS.  I am not an expert but I think this is NOT GOOD.

Dreading the idea to setup everything from scratch: partioning harddisk, setup Ubuntu, Vista (my backup to allow me to control the laptop), etc. takes a lot of effort,

escpecially since 1) there are some conflicts with Vista.  Ubuntu does not load unless something has to be done with the bootloader etc.  and 2) wireless and Dell Inspiron and Ubuntu are not compatible.  I recall a lot of time and effort from IT expert to set it up for me.

I am depressed...

[-o< Can somebody suggest a way out ?  A terminal prompt appears when Ubuntu fails to boot...

Hi tomaasj.

If I understand correctly, your Vista still boots, but the Ubuntu doesn't due to Norton Ghost had mistakenly set up ext2 instead of ext3 when you restore the Ubuntu?

let us know :KS

---

### Post by tomaasj on 2007-07-16
Yes,

check this out:

[http://ubuntuforums.org/showthread.php?t=35087&highlight=Heliode](http://ubuntuforums.org/showthread.php?t=35087&highlight=Heliode)

---

### Post by duydaniel on 2007-07-16
> **tomaasj said:**
> Yes,

check this out:

[http://ubuntuforums.org/showthread.php?t=35087&highlight=Heliode](http://ubuntuforums.org/showthread.php?t=35087&highlight=Heliode)

Wow... it really help. I don't know if you have figured out how to fix your system. Just wait for someone who is good at Linux give advices.

I, too, have Dual Boot Vista and Ubuntu and the third partitions keeping data as you have. The last time, I did a clean install by using a partition program... then deleted the partition ext3 and swap. Finally, I have an unuse part of my hard drive.

Of course, at this state, Vista could not boot (I believe since I had not tried to boot from hard drive) because Bootloader in the Ubuntu partition was deleted. I then use the Ubuntu install CD and chose something like "using the greatest remain free space on hard drive to install" in the partitioning step.

Then, Ubuntu will automatically recognize Vista and make dual boot. I got into hassle before if I install Ubuntu with Vista otherwise... :(

---

### Post by hyperair on 2007-07-17
Meh... sounds bad. >< Norton Ghost right? I've used it once before, but I backed up and never restored it. xD. So you're saying that Ubuntu won't boot because Norton Ghost mistakenly created an ext2 drive instead of ext3 huh. Could you post any error messages that pop up when you boot Ubuntu?

By the way, if you're thinking of a reinstall, I reckon that you could just reformat that partition that Ghost has created with ext3 instead. No need to repartition your drives.

---

### Post by tomaasj on 2007-07-17
I think so to.  But how to do it ?  And how to re-installl the Backup image file ?  I posted in Ïnstallation and Upgrades" See what comes out of that...

---

### Post by hyperair on 2007-07-17
The easiest way out is a clean install. If you don't mind losing your configuration, it'll be very simple. Otherwise, there'll be repartitioning involved, and I cannot really help you there, as I've got absolutely zero experience. I installed Ubuntu 3 times because I screwed up 3 times within the same week. After that I learnt how to fix my problems on my own, or with the forum users' help.

Anyway... you could just run through the installation process from the LiveCD again, and when they ask you to select a partition, you select the partition you've installed Ubuntu on before. Then they'll make you format it and whatnot.. and specify your swap partition, which you probably created during the first time installation as well. Then it'll format everything for you and proceed normally without any intervention needed (if I'm not mistaken).

---

### Post by tomaasj on 2007-07-17
I went ahead with the Live CD as well, but realized that I had problems with the bootloader (?) before.  I am not an expert but doing it that way blocked the other OS to boot (in this case Vista) or vice versa.  Additional tinkering was needed to figure it all out.  Therefore this is no option for now.  I really would like to restore the partition filestructure to ext3 and re-install on it the Ubuntu Backup image...

I need something like a mini boot CD with Linux restore applications which allows me to do just that, I think...

---

