---
title: "Xgl and Compiz under Breezy"
date: 2006-02-20
forum: Desktop Environments
---

### Post by Milamber_Cubed on 2006-02-20
Hi all.

I just thought I would share my experiences of getting Xgl and Compiz working on my laptop under Breezy. It is a bit slow, but not much worse (if any) than when I was using the live CD for Dapper Flight 3 and got it working on that. The slowness is down to the i810 driver as far as I can tell. And maybe the fact that my graphics card has only 8MB of RAM :rolleyes: 

I am not sure how this will affect systems running on graphics hardware other than i810 driven ones, but I advise that you follow my guide (such as it is :S ) and look to the Nvidia/ATI Specific threads in the Dapper Development forum for specific xorg.conf settings before trying to get Xgl to run in the final couple of steps.

Before we start - I CAN'T BE HELD RESPONSIBLE IF THIS MESSES UP YOUR INSTALL!

EDIT 1 - Feb 21st - added libxcomposite1 to required packages.

EDIT 2 - RPMS were removed from suse server... put them in own web space and updated guide

EDIT 3 - Feb 22nd - Added info about newer RPMS. And clarified ln -s step for fonts folder

EDIT 4 - Feb 23rd - Removed link to newer SuSE RPMS - Couldn't get them working... :(

EDIT 5 - Apr 15th - Changed link for extra compiz libs - wget to forum attachments no longer works. Put in direct link to my web space ;)

First thing to do is get the rpms that were put out by SuSE (hosted on my web sapce :) ), convert them to debs and then install them. THESE ARE i586 RPMS - I DON'T KNOW WHAT WILL HAPPEN IF YOUR CPU DOESN'T MEET THIS REQUIREMENT!!

```

mkdir /tmp/milamber
cd /tmp/milamber
wget http://www.hep.man.ac.uk/u/shiv/ubuntu/xgl-cvs_060214-2.i586.rpm
wget http://www.hep.man.ac.uk/u/shiv/ubuntu/compiz-0.0.2-3.i586.rpm 
sudo apt-get install alien
sudo alien *.rpm
sudo dpkg -i x*.deb
sudo dpkg -i c*.deb

```

Then we make sure we have all the things we need to make it all work

```

sudo apt-get install libxfont1 gconf-editor libwnck18 libglitz1 libxcomposite1

```

Then we make a links/copies so that Xgl finds things in the places it expects them:

```

sudo ln -s /usr/share/X11/fonts/ /usr/X11R6/lib/X11/fonts
sudo cp /usr/lib/libdrm.so.1 /usr/lib/libdrm.so.2 

```

Now we edit the gdm configuration file - making a backup first, just in case ;)

```

cd /etc/gdm
sudo cp gdm.conf gdm.conf.backup
sudo gedit gdm.conf

```

Look in the file for an uncommented  line that says "0=Standard".
Comment it out and add the following:
```

#0=Standard
0=Xgl

```
NOTE - I think that ati users may need to make this "1=Xgl" - check the ATI thread for details.

then add the following to the very end of the file:

```

[server-Xgl]
name=Xgl server
command=/usr/X11R6/bin/Xgl :0 -fullscreen -ac -accel glx:fbo -accel xv:fbo
flexible=true

```

and now save the file. (Again, the exact format the "command" line will depend on your hardware - this works for me with the intel i810 driver)

Now do the following steps to create a script to load compiz with the correct settings:

```

sudo gedit /usr/bin/thefuture

```

and paste the following into it and save it

```

#!/bin/bash
gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher &

```

Save the file and then we make it executable

```

sudo chmod 755 /usr/bin/thefuture

```

You would think that we are now ready to go, but you would be wrong... for some reason some of the libraries didn't load properly on Breezy, so I copied them from my Dapper install an all worked fine :D I uploaded them on another thread, so they are available for download..

```

cd /tmp/milamber
wget http://www.hep.man.ac.uk/u/shiv/ubuntu/compiz-libs.tar.gz
sudo tar xzf compiz-libs.tar.gz
sudo mv *cube* *rotate* *zoom* /usr/lib/compiz/

```

Okay, so now you need to try and make sure that your xorg.conf file is set up properly. I will attach mine so that i810 users can compare - people using a different driver, you know what I am going to say :D - CHECK THE THREAD RELEVANT TO YOUR HARDWARE IN THE DAPPER FORUM. You can view mine here: [http://www.ubuntuforums.org/attachment.php?attachmentid=6308&stc=1&d=1140479785](http://www.ubuntuforums.org/attachment.php?attachmentid=6308&stc=1&d=1140479785)

Okay, so after checking out your xorg.conf file and making any changes needed, you are ready to try it out. If the next step doesn't work or if you want to stop using Xgl, all you need to do is change the correct part of the /etc/gdm/gdm.conf file to look like this:

```

0=Standard
#0=Xgl

```

and everything should be back as it was before you started playing :)

okay, so to test - you need to log out, switch to a terminal (ctrl+alt+f1) and do the following:

```

sudo killall gdm
#Wait a few seconds for this to happen
sudo killall gdm
#if this has worked you should get a message like "no process killed"
#if not keep doing the killall command until it does then do
sudo /etc/init.d/gdm start

```

This SHOULD bring up your normal login screen - log in as normal. Once logged in, open a terminal and run "thefuture". Note any error output in case it doesn't work. 

That's it!!! You should be up and running with Xgl and Compiz - Enjoy!

I would like to say that this is based on the Nvidia guide by poofyhairguy and this page here: [http://cerocoma.blogspot.com/2006/02/cambios-y-errores.html](http://cerocoma.blogspot.com/2006/02/cambios-y-errores.html)

---

### Post by Rob2687 on 2006-02-20
Let's see if it works..

---

### Post by Milamber_Cubed on 2006-02-20
It worked for me :) It was after having gone through PHG's Nvidia guide so I had an idea of what was required anyway...

---

### Post by rado_london on 2006-02-20
This doesnt work for me. I did everything and it was ok. But when I restarted gdm it gave a X Server error. For more information I have onboard graphics using the i810 driver.
This is the outputt of my xorg.conf:
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb,bg"
        Option          "XkbVariant"    ",phonetic"
        Option          "XkbOptions"    "grp:ctrl_shift_toggle,grp:lwin_switch,grp_led:scroll"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver "synaptics"
	Option "AlwaysCore"
	Option "Device" "/dev/input/event2"
	Option "Protocol" "event"
	Option "LeftEdge" "120"
	Option "RightEdge" "830"
	Option "TopEdge" "120"
	Option "BottomEdge" "650"
	Option "FingerLow" "14"
	Option "FingerHigh" "15"
	Option "MaxTapTime" "180"
	Option "MaxTapMove" "110"
	Option "ClickTime" "0"
	Option "EmulateMidButtonTime" "75"
	Option "VertScrollDelta" "10"
	Option "HorizScrollDelta" "0"
	Option "MinSpeed" "0.45"
	Option "MaxSpeed" "0.75"
	Option "AccelFactor" "0.020"
	Option "EdgeMotionMinSpeed" "200"
	Option "EdgeMotionMaxSpeed" "200"
	Option "UpDownScrolling" "1"
	Option "CircularScrolling" "0"
	Option "CircScrollDelta" "0.1"
	Option "CircScrollTrigger" "2"
	Option "SHMConfig" "true"
EndSection

Section "Device"
	BoardName	"915 GM"
	BusID		"PCI:0:2:0"
	Driver		"i810"
	Identifier	"Intel Corporation Intel Default Card"
	VendorName	"Intel"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Intel Default Card"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```


Hope you can help me because I love that glz thing!!!

---

### Post by Milamber_Cubed on 2006-02-20
Hard to say really. The only thing I can think of is that it is to do with the non-standard resolution maybe? Hard to tell without the error output from X :(

For a quick fix, you could replace all the graphics relevant bits of your xorg.cong with the corresponding bits from mine?

---

### Post by rado_london on 2006-02-20
I would like to provide you the error output but I dont know where and how to find it. Can u tell me please?

---

### Post by Rob2687 on 2006-02-20
Got it working on my Radeon 7000 but I get ugly corruption like other people with the same card.
I think it's not Xgl or Compiz but the drivers. If I use the EXA option then I get minor artifacts sometimes with regular xserver but similar to what I see with Xgl .

---

### Post by Milamber_Cubed on 2006-02-20
you might get more of an idea of what's going on with X by killing gdm and then running this from the command line - hopefully the error messages will be helpful :)
```

/usr/X11R6/bin/Xgl :0 -fullscreen -ac -accel glx:fbo -accel xv:fbo

```

Also, was the DRI stuff definetly working before?

---

### Post by rado_london on 2006-02-20
What is DRI stuff ?

---

### Post by rado_london on 2006-02-20
Here is the output of "/usr/X11R6/bin/Xgl :0 -fullscreen -ac -accel glx:fbo -accel xv:fbo":

```
/bin/sh: /etc/sysconfig/displaymanager: No such file or directory

Fatal Server Error:
Cannot move old log file ("/var/log/Xorg.93.log" to "/var/log/Xorg.93.log.old"


Please consult the The X.org Foundation Support
         at http://wiki.x.org
for help.

fatal Server Error:
Xorg Died, exit status 1
```

Hope this is helpful

---

### Post by Milamber_Cubed on 2006-02-20
DRI - basically if the 3d acceleration was working with your original X settings... best way to check is to revert back to "Standard" in the gdm.conf and log in - once logged in run (in a terminal) "glxinfo" The first few lines of out put should tell you either

Direct rendering : yes

OR 

Direct rendering : no

You want it to be yes... :)

---

### Post by Milamber_Cubed on 2006-02-20
[QUOTE=rado_london]Here is the output of "/usr/X11R6/bin/Xgl :0 -fullscreen -ac -accel glx:fbo -accel xv:fbo":

```
/bin/sh: /etc/sysconfig/displaymanager: No such file or directory

Fatal Server Error:
Cannot move old log file ("/var/log/Xorg.93.log" to "/var/log/Xorg.93.log.old"


Please consult the The X.org Foundation Support
         at http://wiki.x.org
for help.

fatal Server Error:
Xorg Died, exit status 1
```

Hope this is helpful[/QUOTE]

My mistake!

that should have been 

sudo /usr/X11R6/bin/Xgl :0 -fullscreen -ac -accel glx:fbo -accel xv:fbo

---

### Post by engla on 2006-02-20
I found ppc versions of the RPMs and tried for myself on my breezy intall. Just put ppc into the URLS instead of i586.

Unfortunately, it seems glibc version 2.4 is required and breezy only has 2.3.5:
/usr/X11R6/bin/Xgl: /lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/X11R6/bin/Xgl)

$ lf /lib/libc.so.6
lrwxrwxrwx  1 root root 13 2006-02-02 05:08 /lib/libc.so.6 -> libc-2.3.5.so


Thanks for giving this new possible solution anyway... I don't want to compile this myself..

---

### Post by rado_london on 2006-02-20
I have DRI enabled!

---

### Post by engla on 2006-02-20
[QUOTE=engla]I found ppc versions of the RPMs and tried for myself on my breezy intall. Just put ppc into the URLS instead of i586.

Unfortunately, it seems glibc version 2.4 is required and breezy only has 2.3.5:
/usr/X11R6/bin/Xgl: /lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/X11R6/bin/Xgl)

$ lf /lib/libc.so.6
lrwxrwxrwx  1 root root 13 2006-02-02 05:08 /lib/libc.so.6 -> libc-2.3.5.so


Thanks for giving this new possible solution anyway... I don't want to compile this myself..[/QUOTE]
Hmm... I just checked and this must be wrong... dapper only has libc v2.3.6.

Is this a problem with fakeroot, alien or the rpms? Or something completely different?

---

### Post by Milamber_Cubed on 2006-02-21
[QUOTE=rado_london]I have DRI enabled![/QUOTE]
Sorry about the delay in the reply - I had to get some sleep!!

have you tried seeing what output you get from doing the following after killing gdm?

```

sudo /usr/X11R6/bin/Xgl :0 -fullscreen -ac -accel glx:fbo -accel xv:fbo

```

I forgot to tell you about the sudo before :D

---

### Post by Milamber_Cubed on 2006-02-21
[QUOTE=engla]Hmm... I just checked and this must be wrong... dapper only has libc v2.3.6.

Is this a problem with fakeroot, alien or the rpms? Or something completely different?[/QUOTE]

It might just be down to the person who compiled these having a newer version of libc? Remember that this is done using SuSE RPMS so things may not work on every platform. I have very little experience (i.e. none) with linux on PPC so I am probably not going to be of much help :S

Maybe if you got the xgl deb from the dapper repository it would fix your problems? I have no idea how well this would work... if at all :???:

---

### Post by sanjose on 2006-02-21
works for me too on radeon 7200 but with the same curruption with this...

[quote=Rob2687]Got it working on my Radeon 7000 but I get ugly corruption like other people with the same card.
I think it's not Xgl or Compiz but the drivers. If I use the EXA option then I get minor artifacts sometimes with regular xserver but similar to what I see with Xgl .[/quote]


and i have to install also libxcomposiste1 co'z compiz is complaining about libXcomposiste.so.1

---

### Post by rado_london on 2006-02-21
This is the output of 
sudo /usr/X11R6/bin/Xgl :0 -fullscreen -ac -accel glx:fbo -accel xv:fbo :

```
Release Date: 9  February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: LINUX 2.6.10 , 686 [ELF]
Current Operating  System: Linux linux 2.6.12-10-386 #1 Mon Jan 16 17:18:08 UTC 2006 i686
Build Date: 10 October 2005

Module Loader present
OS Kernel: Linux version 2.6.12-10-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) 
#1 Mon Jan 16 17:18:08 UTC 2006
Markers: (--) probed, (**) from config file, (==) default settings,
(++) from command line, (!!) notice, (II) informational
(WW) warning, (EE) error, (NI) not implemented,(??) unknown
(==) Log file: "var/log/Xorg.93.log", Time: Tue Feb 21 13:29:06 2006
(==) using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extentions/libGLcore.a:m_debug_clip.o": No symbols found
Skipping "/usr/X11R6/lib/modules/extentions/libGLcore.a:m_debug_norm.0": No symbols found
Skipping "/usrX11R6/lib/modules/extentions/libGLcore.a:m_debug_xform.o": No symbols found
(WW) I810(0): No matching device section for instance (BUSID PCI:0:2:1) found
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o": No symbols found
(WW) I810(0): Failed to set up write-combining range (0xc0000000,0x10000000)
The XKEYBOARD keymap compiler (xkbcomp) reports:
>Warning                   Type "ONE_LEVEL" has 1 levels, but<RALT> has 2 symbols
>                                               Ignoring Extra symbols
Errors from xkbcomp are not fatal to the X server
Synaptics DeviceIni called
SynapticsCtrl called.
Synaptics DeviceOn called
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Error opening security policy file /usr/X11R6/lib/xserver/SecurityPolicy
Could not font path element /usr/X11R6/lib/X11/fonts/TTF , removing from list!
Could not font path element /usr/X11R6/lib/X11/fonts/Type1 , removing from list!
Could not font path element /usr/X11R6/lib/X11/fonts/100dpi , removing from list!
Could not font path element /usr/X11R6/lib/X11/fonts/75dpi , removing from list!


fatal server error:
could not open default font 'fixed'
Synaptics DeviceOff called

```

Hoep this help you to get an idea for my problem

---

### Post by Milamber_Cubed on 2006-02-21
[QUOTE=rado_london]This is the output of 
sudo /usr/X11R6/bin/Xgl :0 -fullscreen -ac -accel glx:fbo -accel xv:fbo :

```
Release Date: 9  February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: LINUX 2.6.10 , 686 [ELF]
Current Operating  System: Linux linux 2.6.12-10-386 #1 Mon Jan 16 17:18:08 UTC 2006 i686
Build Date: 10 October 2005

Module Loader present
OS Kernel: Linux version 2.6.12-10-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) 
#1 Mon Jan 16 17:18:08 UTC 2006
Markers: (--) probed, (**) from config file, (==) default settings,
(++) from command line, (!!) notice, (II) informational
(WW) warning, (EE) error, (NI) not implemented,(??) unknown
(==) Log file: "var/log/Xorg.93.log", Time: Tue Feb 21 13:29:06 2006
(==) using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extentions/libGLcore.a:m_debug_clip.o": No symbols found
Skipping "/usr/X11R6/lib/modules/extentions/libGLcore.a:m_debug_norm.0": No symbols found
Skipping "/usrX11R6/lib/modules/extentions/libGLcore.a:m_debug_xform.o": No symbols found
(WW) I810(0): No matching device section for instance (BUSID PCI:0:2:1) found
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o": No symbols found
(WW) I810(0): Failed to set up write-combining range (0xc0000000,0x10000000)
The XKEYBOARD keymap compiler (xkbcomp) reports:
>Warning                   Type "ONE_LEVEL" has 1 levels, but<RALT> has 2 symbols
>                                               Ignoring Extra symbols
Errors from xkbcomp are not fatal to the X server
Synaptics DeviceIni called
SynapticsCtrl called.
Synaptics DeviceOn called
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Error opening security policy file /usr/X11R6/lib/xserver/SecurityPolicy
Could not font path element /usr/X11R6/lib/X11/fonts/TTF , removing from list!
Could not font path element /usr/X11R6/lib/X11/fonts/Type1 , removing from list!
Could not font path element /usr/X11R6/lib/X11/fonts/100dpi , removing from list!
Could not font path element /usr/X11R6/lib/X11/fonts/75dpi , removing from list!


fatal server error:
could not open default font 'fixed'
Synaptics DeviceOff called

```

Hoep this help you to get an idea for my problem[/QUOTE]

Well to me it loks like you are trying to load some fonts that either arent there OR the link you created ( the "ln -s" line in the guide didnt work... Make sure that the link is correct and if tyhat doesn't work try comparing all the lines about fonts from your xorg.conf with mine and comment out any that aren't in mine.

---

### Post by rado_london on 2006-02-21
I compared all my lines in the xorg.conf and they are the same as yours. Now I am really confused. Anyone has any ideas.
Cheers

---

### Post by byoon on 2006-02-21
A couple of observations and requests for any suggestions:

1) I also had to install libxcomposiste1 in order to get things to work.  You might want to add this to your instructions.

2) It takes a long time for my splash screen to go away.  I can click it and it will disappear, but it seems like processes are still running because if I try to log out, the log out dialog box doesn't appear for a long time.  This actually happens on my experimental Dapper install, too.  Anyone else experiencing this?

3) The workspace switcher doesn't display correctly.  All four workspaces in the workspace switcher seem to get smashed into the space/box that one workspace would normall occupy.  Another way to describe it, instead of seeing 4x1 boxes I see a 1x1 box with all four workspaces smashed into it.  Yet another way to describe it, I see each of the four workspaces smashed into 1/4 the width.  Any ideas?  Cube is not very useful if I can't see a summary of what's in each workspace.

4) I get minor video corruption and resizing totem while playing videos does not really work.  I can live with this until I officially upgrade to dapper because I don't think this can be fixed using xgl and compiz, especially because these are the SUSE rpm packages converted into debs and weird things should be expected.

5) The resize sensitivity is too great, meaning that it is too easy to try and grab a window title bar to move it and end up resizing it instead.  The resize border width seems like it is several pixels deep, which ends up being about 1/5 if not 1/4 of the title bar.  Can I change the resize border width so that it is only a few pixels?

BTW, thanks for this guide.  Anybody try using Dapper's xgl and composite packages?

---

### Post by Milamber_Cubed on 2006-02-21
[QUOTE=byoon]A couple of observations and requests for any suggestions:

1) I also had to install libxcomposiste1 in order to get things to work.  You might want to add this to your instructions.
[/quote]
Will do that now :) I must have already had it installed (BTW, just nto be clear its libxcomposite1, right?
[QUOTE=byoon]
2) It takes a long time for my splash screen to go away.  I can click it and it will disappear, but it seems like processes are still running because if I try to log out, the log out dialog box doesn't appear for a long time.  This actually happens on my experimental Dapper install, too.  Anyone else experiencing this?
[/quote]
I haven't seen this - The fact that it happens on Dapper as well seems to point to it being something to do with your hardware or the way that it is detected ... I guess ??
[QUOTE=byoon]
3) The workspace switcher doesn't display correctly.  All four workspaces in the workspace switcher seem to get smashed into the space/box that one workspace would normall occupy.  Another way to describe it, instead of seeing 4x1 boxes I see a 1x1 box with all four workspaces smashed into it.  Yet another way to describe it, I see each of the four workspaces smashed into 1/4 the width.  Any ideas?  Cube is not very useful if I can't see a summary of what's in each workspace.
[/quote]
I have this problem as well and I haven't been able to fix it yet. I am tempted to try installing the debs from the Dapper repositories and see if that helps, but I haven't really had time yet.
[QUOTE=byoon]
4) I get minor video corruption and resizing totem while playing videos does not really work.  I can live with this until I officially upgrade to dapper because I don't think this can be fixed using xgl and compiz, especially because these are the SUSE rpm packages converted into debs and weird things should be expected.
[/quote]
Video is kind of unusable with the i810 driver because it doesn't really accelerate all that much and just passes it on to the CPU to do all the hard work. If/when better drivers are released this should get better :D
[QUOTE=byoon]
5) The resize sensitivity is too great, meaning that it is too easy to try and grab a window title bar to move it and end up resizing it instead.  The resize border width seems like it is several pixels deep, which ends up being about 1/5 if not 1/4 of the title bar.  Can I change the resize border width so that it is only a few pixels?
[/quote]
I think this is down to gnome-window-decorator (part of compiz, if I understand what is going on here) and i have the same problem. In fact if you watch the video put out recently the person doing the demo has the exact same problem! I don't know of any way to fix this, I guess it will be fixed in a later release... Maybe a post in the Xgl/compiz bug thread is worth a go?
[QUOTE=byoon]
BTW, thanks for this guide.  Anybody try using Dapper's xgl and composite packages?[/QUOTE]
Thinking about this for the past couple of days... I might give it a go tonight and report back!

---

### Post by Milamber_Cubed on 2006-02-21
[QUOTE=rado_london]I compared all my lines in the xorg.conf and they are the same as yours. Now I am really confused. Anyone has any ideas.
Cheers[/QUOTE]

okay... so it was saying that it couldnt find the fonts... try running this and see if you get similar output.

```

ls -la /usr/X11R6/lib/X11/fonts
#output should look like the following
lrwxrwxrwx  1 root root 21 2006-02-19 21:24 /usr/X11R6/lib/X11/fonts -> /usr/share/X11/fonts/

```

EDIT::

if the output is not the same/similar then do the following

```

sudo rm /usr/X11R6/lib/X11/fonts
sudo ln -s /usr/share/X11/fonts /usr/X11R6/lib/X11/fonts

```

---

### Post by arrizaba on 2006-02-21
Does anyone know if Xgl works for i915 graphics card?
Someone in this forum (sorry, I forgot his/her name) said he could not.

---

### Post by pmpc00 on 2006-02-21
Hey guys, has anyone seen this problem after running "thefuture"

user@host:~$ thefuture
user@host:~$ gnome-window-decorator, Failed to load shadow images
compiz: No composite extension

Any thoughts?

---

### Post by pmpc00 on 2006-02-21
I'll save some time and include this..


user@host:~$ cat /usr/bin/thefuture
#!/bin/bash
gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher &

---

### Post by Havoc on 2006-02-21
Did they remove the XGL and Compiz RPMs?

Anyways, If this is proven to work, at least for the minority, try posting a guide on the "Tips 'n Tricks" forum. ;)

---

### Post by Milamber_Cubed on 2006-02-21
[QUOTE=pmpc00]Hey guys, has anyone seen this problem after running "thefuture"

user@host:~$ thefuture
user@host:~$ gnome-window-decorator, Failed to load shadow images
compiz: No composite extension

Any thoughts?[/QUOTE]

This is exactly the output I get when I try and run "thefuture" when I am running a standard X session and not Xgl. Are you sure Xgl has actually started?

---

### Post by Milamber_Cubed on 2006-02-21
[QUOTE=Havoc]Did they remove the XGL and Compiz RPMs?

Anyways, If this is proven to work, at least for the minority, try posting a guide on the "Tips 'n Tricks" forum. ;)[/QUOTE]

They are gone!!

And I didn't keep them - I don't suppose that anyone kept them and can post them on here in a tar file or something??:???:

---

### Post by Milamber_Cubed on 2006-02-21
[QUOTE=arrizaba]Does anyone know if Xgl works for i915 graphics card?
Someone in this forum (sorry, I forgot his/her name) said he could not.[/QUOTE]

My graphics card is an intel 915GM (using the i810 driver, because they were merged) and it is working - the RPMS seem to be missing in action though :???: 

You might want to wait until we get hold of the rpms again...

---

### Post by pmpc00 on 2006-02-21
[QUOTE=Milamber_Cubed]This is exactly the output I get when I try and run "thefuture" when I am running a standard X session and not Xgl. Are you sure Xgl has actually started?[/QUOTE]


I guess i'm not sure if it started, how would i check?

---

### Post by Havoc on 2006-02-21
It's all in here:

[http://download.opensuse.org/distribution/SL-OSS-factory/inst-source/suse/i586/](http://download.opensuse.org/distribution/SL-OSS-factory/inst-source/suse/i586/)


;)

---

### Post by Milamber_Cubed on 2006-02-21
Found the RPMS on a mirror that I guess hasn't been updated yet. They are too big for me to upload onto here so I am going to upload them to my web space and change the guide in the first post to link to them there. Should be done in a few minutes. :D

---

### Post by Havoc on 2006-02-21
Ok, I get this:

```
havoc@Nosgoth:~$ thefuture
havoc@Nosgoth:~$ compiz: GLX_EXT_texture_from_pixmap is missing
compiz: Failed to manage screen: 0
compiz: No managable screens found on display :0.0
The program 'gnome-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 389 error_code 8 request_code 72 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

Poofyhairguy says that the "Cannot Manage Screen" is a typical problem and with a lot of retrying you can get rid of it, but I cannot!
Oh, and X starts fine.

Any thoughts?

:-k

---

### Post by Milamber_Cubed on 2006-02-21
[QUOTE=Havoc]Ok, I get this:

```
havoc@Nosgoth:~$ thefuture
havoc@Nosgoth:~$ compiz: GLX_EXT_texture_from_pixmap is missing
compiz: Failed to manage screen: 0
compiz: No managable screens found on display :0.0
The program 'gnome-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 389 error_code 8 request_code 72 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

Poofyhairguy says that the "Cannot Manage Screen" is a typical problem and with a lot of retrying you can get rid of it, but I cannot!
Oh, and X starts fine.

Any thoughts?

:-k[/QUOTE]
If you look at PHG's guide, there is a bit about enabling the composite extensions int the xorg.conf file. That might fix this problem. Check it out here 

[http://www.ubuntuforums.org/showthread.php?t=131267](http://www.ubuntuforums.org/showthread.php?t=131267)

---

### Post by Milamber_Cubed on 2006-02-21
[QUOTE=pmpc00]I guess i'm not sure if it started, how would i check?[/QUOTE]
Do this in a terminal

```

ps -A | grep Xgl

```

And see if it produces any output - if not then Xgl is not running.

---

### Post by pmpc00 on 2006-02-21
[QUOTE=Milamber_Cubed]Do this in a terminal

```

ps -A | grep Xgl

```

And see if it produces any output - if not then Xgl is not running.[/QUOTE]


Ahh yea, i never let the gdm server stop after changing the conf file.  Got it to work now with Xgl loaded. 

Thanks!

---

### Post by Milamber_Cubed on 2006-02-21
[QUOTE=pmpc00]Ahh yea, i never let the gdm server stop after changing the conf file.  Got it to work now with Xgl loaded. 

Thanks![/QUOTE]

Woo Hoo!

No Problemo btw... This site has been my saviour since I started using Ubuntu just before Christmas. I thought I would try and share something back :D

---

### Post by Havoc on 2006-02-21
I found the solution.The problem was, the XGL package from the Repo I gave had no /usr/bin/Xgl and I had to create a symlink from /usr/X11R6/bin/Xgl.Just as a reminder.

XGL RULEZ! :) :) :)

---

### Post by Milamber_Cubed on 2006-02-21
More success! Coolio!

About the Xgl location - that tripped me up as well but I made sure that in my post, I put the correct location for this guide :) Maybe I should have told people to make a sym-link? I just made the change in the gdm.conf file and then all was well :)

---

### Post by Havoc on 2006-02-21
One more question, then I stop talking - forever.

None of the keys (Such as F11 for the Expose thingie, or Alt-Tab or Whatever) work for me... Has anyone else encountered this problem? :-k

---

### Post by Havoc on 2006-02-21
Now everything works - WTF ??! :confused:

---

### Post by Milamber_Cubed on 2006-02-21
Do not question it.... just let it roll. Compiz does some crazy things with your keyboard settings for some reason. The other threads tell you to use the xmodmap command (or something similar) to fix it, but I managed to get things back to normal without having to do that somehow :???:

Also, there is a way to change the opacity of the windows described in the Nvidia thread, if you are interested. A quick search should find it :)

---

### Post by Rob2687 on 2006-02-21
Compiz doesn't mess with the keyboard. It's probably Xgl.

---

### Post by Havoc on 2006-02-21
Already got that, using transset, and above that, I can have my mouse wheel control the opacity! :p

---

### Post by Milamber_Cubed on 2006-02-21
[QUOTE=Rob2687]Compiz doesn't mess with the keyboard. It's probably Xgl.[/QUOTE]

Well when I start Xgl and log in I can use Win+R (A habbit I should break, I know) to bring up the Run Application box. After starting gnome-window-decorator and compiz from "thefuture" it stops working and I have to revert to using Alt+F2. Not really sure why this is, but that's why I said it was compiz doing some "crazy things". 

I guess it's intercepting all of the keyboard strokes once it's loaded (security issue there maybe?) and applying shortcuts as it sees fit?

I can live with it, so no big deal :)

---

### Post by Havoc on 2006-02-21
I think that Compiz *replaces* Metacity as the Window Manager.

First, look at the border.NOT what I had in my theme (though very pretty)
Compiz provides its own keyboard bindings.Just check gconf-->apps-->compiz for the full list.

My only problem is that I can't seem to put <Ctrl> as a modifier.

---

### Post by saVTRonic on 2006-02-21
```

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux ubuntu 2.6.12-10-k7 #1 Mon Feb 13 12:29:26 UTC 2006 i686
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-k7 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Feb 13 12:29:26 UTC 2006 T
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Feb 21 22:09:18 2006
(==) Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server

```

:confused: 

Ubuntu 5.10 / Nvidia

Any ideas ?

---

### Post by Milamber_Cubed on 2006-02-21
[QUOTE=Havoc]I think that Compiz *replaces* Metacity as the Window Manager.

First, look at the border.NOT what I had in my theme (though very pretty)
Compiz provides its own keyboard bindings.Just check gconf-->apps-->compiz for the full list.

My only problem is that I can't seem to put <Ctrl> as a modifier.[/QUOTE]

I think that you use <Control> - have a look at the settings for the rotate plugin, that uses Ctrl+Alt+Left/Right...

---

### Post by saVTRonic on 2006-02-21
Ok, i solved my problem, just some "ln -s". :)

Works but :

- kde app systray dont show
- zoom dont work

---

### Post by rado_london on 2006-02-21
[QUOTE=Milamber_Cubed]okay... so it was saying that it couldnt find the fonts... try running this and see if you get similar output.

```

ls -la /usr/X11R6/lib/X11/fonts
#output should look like the following
lrwxrwxrwx  1 root root 21 2006-02-19 21:24 /usr/X11R6/lib/X11/fonts -> /usr/share/X11/fonts/

```

EDIT::

if the output is not the same/similar then do the following

```

sudo rm /usr/X11R6/lib/X11/fonts
sudo ln -s /usr/share/X11/fonts /usr/X11R6/lib/X11/fonts

```[/QUOTE]
Thanks man it works, but I cannot get all the functions because I dont know how. Well is there a manual for using it. By the way it is completely unusable on my laptop but it is nice.

---

### Post by evil-nick on 2006-02-21
Sweet!  I didn't need to install Dapper or Gentoo after all!  Thanks much!

---

### Post by byoon on 2006-02-22
[QUOTE=byoon]A couple of observations and requests for any suggestions:

1) I also had to install libxcomposiste1 in order to get things to work.  You might want to add this to your instructions.
[/QUOTE]

I also downloaded compiz-0.0.2-4.i586.rpm instead of compiz-0.0.2-3.i586.rpm.  I can't tell if it made any difference whatsoever.

[QUOTE=byoon]
2) It takes a long time for my splash screen to go away.  I can click it and it will disappear, but it seems like processes are still running because if I try to log out, the log out dialog box doesn't appear for a long time.  This actually happens on my experimental Dapper install, too.  Anyone else experiencing this?
[/QUOTE]

I forgot to mention that I have an .Xsession file instead of a thefuture script.  I think if I used thefuture and ran it after logging into gnome, the splash screen issue would go away.  Don't care about trying it out because I am fine the way it is.

[QUOTE=byoon]
3) The workspace switcher doesn't display correctly.  All four workspaces in the workspace switcher seem to get smashed into the space/box that one workspace would normall occupy.  Another way to describe it, instead of seeing 4x1 boxes I see a 1x1 box with all four workspaces smashed into it.  Yet another way to describe it, I see each of the four workspaces smashed into 1/4 the width.  Any ideas?  Cube is not very useful if I can't see a summary of what's in each workspace.
[/QUOTE]

I'm actually using it the way it is now.  Kind of like that it is super small now.  All I need to see is if some window is in another workspace and it does that.

[QUOTE=byoon]
4) I get minor video corruption and resizing totem while playing videos does not really work.  I can live with this until I officially upgrade to dapper because I don't think this can be fixed using xgl and compiz, especially because these are the SUSE rpm packages converted into debs and weird things should be expected.
[/QUOTE]

This is fixed by setting the video.driver to OpenGL for Totem per this thread:

[http://www.ubuntuforums.org/showthread.php?t=133815&page=2]("http://www.ubuntuforums.org/showthread.php?t=133815&page=2")

[QUOTE=byoon]
5) The resize sensitivity is too great, meaning that it is too easy to try and grab a window title bar to move it and end up resizing it instead.  The resize border width seems like it is several pixels deep, which ends up being about 1/5 if not 1/4 of the title bar.  Can I change the resize border width so that it is only a few pixels?
[/QUOTE]

Once you get used to it, your brain adjusts.

> 
BTW, thanks for this guide.  Anybody try using Dapper's xgl and composite packages?

Thanks, again.  I will probably go full-time to Dapper soon, but this was a nice treat.

Cedega refuses to run in Breezy with this XGL stuff enabled.

---

### Post by GameGod on 2006-02-22
Is it just me, or are the two RPM links in the first post down?

---

### Post by GameGod on 2006-02-22
Hmmm, I found the RPMs here:
[http://linux.integrity.hu/pub/opensuse/distribution/SL-OSS-factory/inst-source/suse/i586/](http://linux.integrity.hu/pub/opensuse/distribution/SL-OSS-factory/inst-source/suse/i586/)

Edit: Don't use the compiz rpm from here (at least if you follow the guide...it's a long story!) (The one's in the original post are back up...)

---

### Post by Qoon3x on 2006-02-22
it's working!
[SIZE="1"]but i get an error when i type thefuture:

"/home/henk/.themes/Black/gtk-2.0/gtkrc:878: can't find picture in pixmap_pad: "Menu-Menubar/menu-overlay.png" 
compiz: Couldn't bind redirected window 0xe0117c to texture" 

any ideas what could be the problem?[/SIZE]
{FIXED}

And gdesklets aren't working good any more.. what should be transparant has now a black line around it and it is semi-transparant.
is there a fix for?

and what are all the keyboard bindings for the special effects?
i've got:
alt - tab
crtl - alt - left/right
f12

any more?

---

### Post by Milamber_Cubed on 2006-02-22
[QUOTE=Qoon3x]it's working!
[SIZE="1"]but i get an error when i type thefuture:

"/home/henk/.themes/Black/gtk-2.0/gtkrc:878: can't find picture in pixmap_pad: "Menu-Menubar/menu-overlay.png" 
compiz: Couldn't bind redirected window 0xe0117c to texture" 

any ideas what could be the problem?[/SIZE]
{FIXED}

And gdesklets aren't working good any more.. what should be transparant has now a black line around it and it is semi-transparant.
is there a fix for?

and what are all the keyboard bindings for the special effects?
i've got:
alt - tab
crtl - alt - left/right
f12

any more?[/QUOTE]
Default shortcuts can be found here:

[http://en.opensuse.org/Compiz](http://en.opensuse.org/Compiz)

Just scroll to the bottom of the page.

---

### Post by Jefim on 2006-02-22
Umph... I did everything step-by-step, but when I start gdm it loops for a while trying to show me the login screen and the tells, that x failed to start. The output is:
> Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
(II) SIS(0): Restoring by setting old mode 0x03

---

### Post by Svip on 2006-02-22
I did all the steps as explained in the first, but when I finally got there to try it, it almost seemed as if it has worked, but when I tried to start session with GNOME, nothing happen, I tried E17, no applications worked, and fluxbox won't start any applications.

So I was wondering; How would I get it to work under GNOME?  Note: When it loads, it doesn't load, it doesn't do anything, it just shows the mouse which I can move about, and a black background.

I am using i810.

It seems that now this has fucked up my GNOME, when I get it to start, a lot of windows pops up saying there have been errors in the configuration.  When I change back to the old one (the backup of the gdm.conf), it doesn't show errors, but it doesn't do anything, except my mouse still.

---

### Post by Jefim on 2006-02-22
Ok, not I'm getting the louzy GL_EXT_texture_from_pixmap is missing from compiz... window borders disapper and there is no way to communicate with the system (keyboard and mouse work, but shortcuts doint work, I can't select other windowx etc.)

---

### Post by Milamber_Cubed on 2006-02-22
[QUOTE=Svip]I did all the steps as explained in the first, but when I finally got there to try it, it almost seemed as if it has worked, but when I tried to start session with GNOME, nothing happen, I tried E17, no applications worked, and fluxbox won't start any applications.

So I was wondering; How would I get it to work under GNOME?  Note: When it loads, it doesn't load, it doesn't do anything, it just shows the mouse which I can move about, and a black background.

I am using i810.

It seems that now this has fucked up my GNOME, when I get it to start, a lot of windows pops up saying there have been errors in the configuration.  When I change back to the old one (the backup of the gdm.conf), it doesn't show errors, but it doesn't do anything, except my mouse still.[/QUOTE]

on i810, it shows me a black background etc. after running "thefuture" just switch desktops (ctrl+alt+left/right) and it should redrwa the desktop properly. Hope this helps... not sure what else to suggest really... :-?

---

### Post by Milamber_Cubed on 2006-02-22
[QUOTE=Jefim]Ok, not I'm getting the louzy GL_EXT_texture_from_pixmap is missing from compiz... window borders disapper and there is no way to communicate with the system (keyboard and mouse work, but shortcuts doint work, I can't select other windowx etc.)[/QUOTE]

The only time this happened to me was when I tried to use different RPMs than the ones I linked to. Did you use the ones in thye guide or the ones on the SuSE page?

---

### Post by Milamber_Cubed on 2006-02-22
[QUOTE=Jefim]Umph... I did everything step-by-step, but when I start gdm it loops for a while trying to show me the login screen and the tells, that x failed to start. The output is:[/QUOTE]

Are you using an SIS graphics card? If you are, you need to be sure that it actually supports 3d acceleration. AFAIK only some of them do... If yours does, make sure that it is enabled using tht standard gdm.conf file before trying the steps in this guide.

---

### Post by Jefim on 2006-02-23
Excuse me, but could you give me some pointers how exactly I check it (for sure)... because the sis driver is a bit crappy...
Besides, I used the suse rpms, but I'll try to install yours in a few minutes... Something tells me, that I won't be seeing compiz in action on my computer :D

---

### Post by Milamber_Cubed on 2006-02-23
[QUOTE=Jefim]Excuse me, but could you give me some pointers how exactly I check it (for sure)... because the sis driver is a bit crappy...
Besides, I used the suse rpms, but I'll try to install yours in a few minutes... Something tells me, that I won't be seeing compiz in action on my computer :D[/QUOTE]
Have a look at this.

[http://www.ubuntuforums.org/showpost.php?p=755550&postcount=11](http://www.ubuntuforums.org/showpost.php?p=755550&postcount=11)

It shows how to check to see if 3d acceleration is working. I think you might have more luck with the RPMs I linked to, I am probably going to remove the link to the SuSE rpms from my guide as I haven't been able to get them to work properly and have very similar problems to the ones you described.

Good luck!!!

---

### Post by rollininoh on 2006-02-23
only error i got was that libxfont1 was missing

so i started from scratch thinking maybe i skipped a step
heres what happens when i check to see if i have it

dave@laptop:/tmp/milamber$ sudo apt-get install libxfont1 gconf-editor libwnck18 libglitz1 libxcomposite1
Reading package lists... Done
Building dependency tree... Done
Package libxfont1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libxfont1 has no installation candidate


so how can i get libxfont1? i cant seem to apt-get it, it smply doesnt exist,

if possible step by step instructions would be awesome, i am literally a linux newb, ive been excited that i got ubuntu installed, and all hardware working firs try lol.

---

### Post by f0vela on 2006-02-24
this guide works like a charm! i got Xgl Running on my breezy system. :D

I also use the last tips on this thread:
[http://www.ubuntuforums.org/showthread.php?t=131267&highlight=xgl](http://www.ubuntuforums.org/showthread.php?t=131267&highlight=xgl)

Nice thing! thanks. :D
This is Amazing! :D \\:D/

---

### Post by Milamber_Cubed on 2006-02-25
[QUOTE=rollininoh]only error i got was that libxfont1 was missing

so i started from scratch thinking maybe i skipped a step
heres what happens when i check to see if i have it

dave@laptop:/tmp/milamber$ sudo apt-get install libxfont1 gconf-editor libwnck18 libglitz1 libxcomposite1
Reading package lists... Done
Building dependency tree... Done
Package libxfont1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libxfont1 has no installation candidate


so how can i get libxfont1? i cant seem to apt-get it, it smply doesnt exist,

if possible step by step instructions would be awesome, i am literally a linux newb, ive been excited that i got ubuntu installed, and all hardware working firs try lol.[/QUOTE]

You probably need to enable all of the sources in you apt coonfiguration.

The easiest way to do this is to edit the /etc/apt/sources.list file. In it there will be lots of lines commented out - with a '#' at the beginning. what you need to do is remove the # at teh start of the lines that start #deb. Save the file, then run "sudo apt-get update".

After that you should be good to follow the instructions on the guide.

---

### Post by magomago on 2006-02-25
I geth ithis error (Below)

also for some reason when I run thefuture my metacity theme dissapears and windows freeze in place




[q]

amarry@cv080006:~$ thefuture
amarry@cv080006:~$ compiz: GLX_EXT_texture_from_pixmap is missing
compiz: Failed to manage screen: 0
compiz: No managable screens found on display :0.0
The program 'gnome-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 390 error_code 8 request_code 72 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
[/q]

any ideas?

---

### Post by vbmaster on 2006-02-25
Hey guys,

I get the blackscreen too after runing 'thefuture'. I only see my mouse and if i click on the blackarea that would match the menus and buttons I can barely see the windows opening, but they disapear. Ctrl+Alt+left, right didn't worked. :(

I would love get xgl working, I've a GeForce4 MX 440, and my xorg.conf is this: 

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
#	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"pt"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true" 
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
        Option  "Composite" "Enable"
EndSection

```

Can anyone help me? or it's just my graphic board that it's too low?

Thanks ;)

---

### Post by gustavold on 2006-02-25
hi

i have the same video card and the same problem. Did you install the CVS's version of glitz? I didnt install because i dont want to compile, I installed the dapper version (0.5.3) but it still dont work... =(

can anyone make a .deb file of CVS glitz??

> 
Hey guys,

I get the blackscreen too after runing 'thefuture'. I only see my mouse and if i click on the blackarea that would match the menus and buttons I can barely see the windows opening, but they disapear. Ctrl+Alt+left, right didn't worked.

I would love get xgl working, I've a GeForce4 MX 440, and my xorg.conf is this:


---

### Post by Trojan1313 on 2006-02-25
tsuji@Tsunku:~$ xdriinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Screen 0: not direct rendering capable.

Is this fixable or is it my graphicscard that doesn't support it?
It works and stuff, but it's SLOW. :p

---

### Post by gustavold on 2006-02-25
does anyone know if i can use the nvidia-legacy driver ??

i tried all said here and i'm still seing a black screen when i run "thefuture" script...

i didnt install glitz directly from cvs. i build a .deb file from the cvs code. i made it because i need to restore my system to breezy after. it was my first .deb build, maybe i have made something wrong...

i attached my .deb file if anyone want to see/use

i hope i can see xgl/compiz running here :-|

---

### Post by Trojan1313 on 2006-02-25
[QUOTE=gustavold]does anyone know if i can use the nvidia-legacy driver ??

i tried all said here and i'm still seing a black screen when i run "thefuture" script...

i didnt install glitz directly from cvs. i build a .deb file from the cvs code. i made it because i need to restore my system to breezy after. it was my first .deb build, maybe i have made something wrong...

i attached my .deb file if anyone want to see/use

i hope i can see xgl/compiz running here :-|[/QUOTE]
Try making a marking on the desktop, moving a window, hovering a button or whatever you can think of. :)

---

### Post by gustavold on 2006-02-25
[QUOTE=Trojan1313]Try making a marking on the desktop, moving a window, hovering a button or whatever you can think of. :)[/QUOTE]

i see just a black screen but when i click i can see the menu during an instant. i can launch apps from the pannel but i cant see nothing

---

### Post by gustavold on 2006-02-25
$ thefuture 2> out.txt

out.txt:

compiz: pixmap 0x2c00024 can't be bound to texture
compiz: pixmap 0x2c00030 can't be bound to texture
compiz: pixmap 0x2c0009c can't be bound to texture
compiz: pixmap 0x2e00075 can't be bound to texture
compiz: Couldn't bind redirected window 0x100004d to texture
compiz: pixmap 0x2e00077 can't be bound to texture
compiz: Couldn't bind redirected window 0x1000003 to texture
compiz: pixmap 0x2e00079 can't be bound to texture
compiz: Couldn't bind redirected window 0x2a0001a to texture
compiz: pixmap 0x2e0007b can't be bound to texture
compiz: Couldn't bind redirected window 0x1200030 to texture
compiz: pixmap 0x2e00075 can't be bound to texture
compiz: Couldn't bind redirected window 0x100004d to texture
compiz: pixmap 0x2e00077 can't be bound to texture
compiz: Couldn't bind redirected window 0x1000003 to texture
compiz: pixmap 0x2e00075 can't be bound to texture
compiz: Couldn't bind redirected window 0x100004d to texture
compiz: pixmap 0x2e00077 can't be bound to texture
...

---

### Post by Trojan1313 on 2006-02-25
[QUOTE=gustavold]i see just a black screen but when i click i can see the menu during an instant. i can launch apps from the pannel but i cant see nothing[/QUOTE]
Ah, I see.

I had a similar problem, everything went black exept the mouse, and then I had to "wipe of the black" with windows and buttons. Thougt you had the same problem. :)

---

### Post by vbmaster on 2006-02-26
[QUOTE=Trojan1313]Ah, I see.

I had a similar problem, everything went black exept the mouse, and then I had to "wipe of the black" with windows and buttons. Thougt you had the same problem. :)[/QUOTE]

as I already said, I've the same problem too... :(

---

### Post by GameGod on 2006-02-26
Every time I run an OpenGL application (glxgears, Totem with OpenGL output), my xserver crashes (Xgl)... Is anyone else experiencing this?

This happens on both my PC (P4, 6600GT) and my Dad's PC (AMD64 X2, 6600)...

---

### Post by GameGod on 2006-02-26
Nevermind, I'm pretty sure the solution is here:

[http://www.ubuntuforums.org/showpost.php?p=743978&postcount=162](http://www.ubuntuforums.org/showpost.php?p=743978&postcount=162)

(I'll give it a shot when I get the chance...)

---

### Post by Milamber_Cubed on 2006-02-26
[QUOTE=GameGod]Every time I run an OpenGL application (glxgears, Totem with OpenGL output), my xserver crashes (Xgl)... Is anyone else experiencing this?

This happens on both my PC (P4, 6600GT) and my Dad's PC (AMD64 X2, 6600)...[/QUOTE]

Have a look in the nvidia specific thread for details on how your xorg.conf should look and the line in the /etc/gdm.conf file to start Xgl may need to be different as well (also in the nvidia thread)

---

### Post by Trojan1313 on 2006-02-27
[QUOTE=vbmaster]as I already said, I've the same problem too... :([/QUOTE]
Can you see the mouse?

Try moving it to where you have your gnome menu and push it, if you have the same problem as I had it will become visible, then start the calculator or something and move it across the screen until all the black is gone. :p

---

### Post by vbmaster on 2006-02-27
[QUOTE=Trojan1313]Can you see the mouse?

Try moving it to where you have your gnome menu and push it, if you have the same problem as I had it will become visible, then start the calculator or something and move it across the screen until all the black is gone. :p[/QUOTE]

Yes i can see the mouse, and when i move it over the things it's discription shows but desapears after a very few time. The same with the menus and windows, so if i start my calculator i'll see a white thing appearing but desapearing into the black in few time.

---

### Post by Trojan1313 on 2006-02-27
Hm, no clue then... perhaps you don't have DRI enabled?

If you don't have DRI, go to freedesktop.org, search for DRI, download common and the one for your driver (i810 in my case). Run the one for your driver and then the common on.
I should warn you though, this might break your X-server, so you should make backups if you want to attempt this.

EDIT:
It still sounds like we have the same problem when it comes down to it, your is just a little more... intense. :p
I think it was DRI that gimped my compiz/Xgl up.

---

### Post by Yeeha on 2006-02-27
VERY GOOD :P , but something is wrong with games... games are halftransparent?? Any ideas how to overcome this and has anyone else that problem?

---

### Post by vbmaster on 2006-02-27
Bah... i think I'll stop trying to be a superman and wait for Dapper... :)

I like to much my ut2k4 and Enemy territory running on Brezzy (like I never seen on Windows) :P

Thanks... and stay cool ;)

---

### Post by lizardking on 2006-02-27
Yahoooooooooooo!
my fujuztu siemen amilo with ubuntu breezy now have xgl compiz enable
thank You for this guide

my battery life is so short now and the CPU more hungry but the effect is spettacuular!:cool:

---

### Post by lizardking on 2006-02-28
[QUOTE=lizardking]Yahoooooooooooo!
my fujuztu siemen amilo with ubuntu breezy now have xgl compiz enable
thank You for this guide

my battery life is so short now and the CPU more hungry but the effect is spettacuular!:cool:[/QUOTE]
Only a problem:
if I press Sifth + Backspace it restart Xserver!
how to solve? 

thnx
:-#

---

### Post by Milamber_Cubed on 2006-02-28
[QUOTE=lizardking]Only a problem:
if I press Sifth + Backspace it restart Xserver!
how to solve? 

thnx
:-#[/QUOTE]

If you look on the nvidia Xgl thread, it recommends using and xmodmap command or something like that to fix this... should do the trick for you.

---

### Post by lizardking on 2006-02-28
[QUOTE=Milamber_Cubed]If you look on the nvidia Xgl thread, it recommends using and xmodmap command or something like that to fix this... should do the trick for you.[/QUOTE]
Fixed with
```
xmodmap /usr/share/xmodmap/xmodmap.it
```
italian = it in my case
thanx to all
\\:D/

---

### Post by Didius on 2006-03-02
Works like candy for me.. :D

BUT, I have the same problem as:
[QUOTE=Yeeha]VERY GOOD :P , but something is wrong with games... games are halftransparent?? Any ideas how to overcome this and has anyone else that problem?[/QUOTE]
I'don't play any 3D games, but games like enigma, wesnoth appear opaque.
Does anyone know what the problem could be?

---

### Post by B_612 on 2006-03-03
I Have some errors....

i trying to install the Xgl and compiz and my pc. installs sucefull but not running the xgl and compiz x.x

anyone can help me?

some "Docs"
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"abnt2"
	Option		"XkbLayout"	"br"
	Option		"XkbVariant"	"abnt2"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
	Driver		"savage"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"710E"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
	Monitor		"710E"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```
My xorg.conf

```

snails@azog:~$ /usr/X11R6/bin/Xgl :0 -fullscreen -ac -accel glx:fbo -accel xv:fbo
/bin/sh: /etc/sysconfig/displaymanager: Arquivo ou diretório não encontrado

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

snails@azog:~$

```
Trying To type the "/usr/X11R6/bin/Xgl :0 -fullscreen -ac -accel glx:fbo -accel xv:fbo" Command

```
snails@azog:~$ thefuture
snails@azog:~$ compiz: No composite extension
gnome-window-decorator, Failed to load shadow images

```
And trying to execute the "the future command"

I will be thankfull if anyone can help me\\:D/ 

(sorry about my bad english x.x)

---

### Post by frodon on 2006-03-03
This thread will help you : [http://www.ubuntuforums.org/showthread.php?t=131267&highlight=xgl+compiz](http://www.ubuntuforums.org/showthread.php?t=131267&highlight=xgl+compiz)

You may have to comment those lines : ```
Load	"dri"
Load	"GLcore"
```And you may have to enable the composite extension thanks to xorg, add that add the end of your xorg.conf : ```
Section "Extensions"
          Option  "Composite" "Enable"
EndSection
```

---

### Post by B_612 on 2006-03-03
I have now another error x.x

```
snails@azog:~$ thefuture
snails@azog:~$ compiz: GLX_EXT_texture_from_pixmap is missing
compiz: Failed to manage screen: 0
compiz: No managable screens found on display :0.0
The program 'gnome-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 389 error_code 8 request_code 72 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

x.x

---

### Post by frodon on 2006-03-03
> That should make compiz start working. If not, just keep using that command (maybe up to 20 times) till it does work. If you have problems, post them in thread so you can get help.Did you try at least 20 times ?

---

### Post by B_612 on 2006-03-03
[QUOTE=frodon]Did you try at least 20 times ?[/QUOTE]
hmm... ermmm... arhmmm... OF COURSE!:mad:

---

### Post by profediego on 2006-03-05
HI could someone tell where i can look for the entire list of key combinations i can use when using Xgl and COmpiz.

Thanks

---

### Post by lizardking on 2006-03-05
Some one knows if there is a way to enable the [compiz 0.05]("http://www.ubuntuforums.org/showthread.php?p=795932") in breezy?
with skydom animated plugin and many bug fixs!
thnx in advange

---

### Post by xsoft on 2006-03-09
[QUOTE=lizardking]Some one knows if there is a way to enable the [compiz 0.05]("http://www.ubuntuforums.org/showthread.php?p=795932") in breezy?
with skydom animated plugin and many bug fixs!
thnx in advange[/QUOTE]

I want to know, too...

please somebody?

---

### Post by linkunderscore on 2006-03-09
[QUOTE=profediego]HI could someone tell where i can look for the entire list of key combinations i can use when using Xgl and COmpiz.

Thanks[/QUOTE]


Check out the Dapper DEvelopement forums. Almost everything in there is realted to compiz and xgl.

---

### Post by barrosz on 2006-03-11
i got compiz 0.0.5 but the skydome isnt working i dont think it was included in this version 0.0.5.2, i followed the howto in the end of the first post, everything works fine except for skydome, also when i use the xmodmap for the alt gr key and for the shift-backspace bug alt-tab stops working and so does the ability to use the cube with ctrl-alt-arrow keys or mouse.all fine if i dont use xmodmap :P

---

### Post by lizardking on 2006-03-11
[QUOTE=barrosz]i got compiz 0.0.5 but the skydome isnt working i dont think it was included in this version 0.0.5.2, i followed the howto in the end of the first post, everything works fine except for skydome, also when i use the xmodmap for the alt gr key and for the shift-backspace bug alt-tab stops working and so does the ability to use the cube with ctrl-alt-arrow keys or mouse.all fine if i dont use xmodmap :P[/QUOTE]
me too
:-?

---

### Post by barrosz on 2006-03-11
been messing with keyboard layouts in gnome, added my countrys layout, also did this to activate win key:
xmodmap -e "clear Mod4"
xmodmap -e "add Mod4 = Super_L"
dunno how really but alt gr is working and all my portuguese keys work even if gnome says its layout is english. weird, anyway i thought this might help.

---

### Post by NoWhereMan on 2006-03-11
can anybody here with an S3 graphic card (laptop) tell if it works?

---

### Post by ubuntuuser on 2006-03-13
[EDIT] Never mind, should have searched more thoroughly.

I tried it and it works well, thanks a lot. But how can I make my windows transparent?

---

### Post by palermi on 2006-03-17
Hi, xgl work very well, but i see in the 

[http://fr2.rpmfind.net/linux/opensuse/distribution/SL-OSS-factory/inst-source/suse/i586/](http://fr2.rpmfind.net/linux/opensuse/distribution/SL-OSS-factory/inst-source/suse/i586/)

and so, i find new versions for compiz and xgl, you recommend to me that installs them? 

Thx.

---

### Post by lizardking on 2006-03-18
[QUOTE=palermi]Hi, xgl work very well, but i see in the 

[http://fr2.rpmfind.net/linux/opensuse/distribution/SL-OSS-factory/inst-source/suse/i586/](http://fr2.rpmfind.net/linux/opensuse/distribution/SL-OSS-factory/inst-source/suse/i586/)

and so, i find new versions for compiz and xgl, you recommend to me that installs them? 

Thx.[/QUOTE]
I think we should try including that dapper exits on 1st June.
But I don't know the result maybe xgl does'not work any more after that

---

### Post by lizardking on 2006-03-18
This is my result so nothing for now.
Moreover in gonf-editor I not see the skydome plugin..so...
```
lizardking@lizard:~$ xgl
gnome-window-decorator: Another window decorator is already running
compiz: Support for non power of two textures missing
compiz: Failed to manage screen: 0
compiz: No managable screens found on display :1.0

```

---

### Post by vignesh on 2006-03-18
HI! I followed  the exact procedure...I use Breezy .I have an nvidia geforce 2 MX.

vignesh@GLADIATOR:~$ thefuture
vignesh@GLADIATOR:~$
(gnome-window-decorator:11712): Gdk-WARNING **: locale not supported by Xlib

(gnome-window-decorator:11712): Gdk-WARNING **: cannot set locale modifiers
gnome-window-decorator, Failed to load shadow images
compiz: No composite extension

---

### Post by Milamber_Cubed on 2006-03-20
[QUOTE=vignesh]HI! I followed  the exact procedure...I use Breezy .I have an nvidia geforce 2 MX.

vignesh@GLADIATOR:~$ thefuture
vignesh@GLADIATOR:~$
(gnome-window-decorator:11712): Gdk-WARNING **: locale not supported by Xlib

(gnome-window-decorator:11712): Gdk-WARNING **: cannot set locale modifiers
gnome-window-decorator, Failed to load shadow images
compiz: No composite extension[/QUOTE]
The only time i have seen this error is with pmpc00 - have a look at our exchange, starting here:

[http://www.ubuntuforums.org/showthread.php?p=757752&highlight=shadow+images#post757752](http://www.ubuntuforums.org/showthread.php?p=757752&highlight=shadow+images#post757752)

---

### Post by winter_mute on 2006-03-20
Okay, so I installed everything, got it working, but I don't have the cube, rotate, or anything like that.  I don't even have multiple monitors any longer.  I went by your guide, plus all the ATI help posted.  Where can I enable the cube?

Edit:  Alright, I figured out what was wrong with the cube, but I still can't get the transparency active.  What library does that use?

---

### Post by Treviño on 2006-03-22
Hello, is there anyone who made this in a **kubuntu** ***breezy***? I mean using **KDE**...

I've a notebook with an ATi mobility radeon 9700 (fglrx) I've tried to apply this guide editing /etc/kde3/kdm/kdmrc instaad of /etc/gdm/gdm.conf with command:
```
ServerCmd=/usr/X11R6/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
```
then adding the /usr/bin/thefuture code into a ~/.kde/Autostart/xstart_script

Btw, Xgl server seems to start, but remain the gray screen with my mouse cursor. KDE is not loaded... 
Advices?

Thanks

PS: in kdm log I get this *error* /bin/sh: /etc/sysconfig/displaymanager: No such file or directory

---

### Post by Silent_Love on 2006-03-23
I can't get Ctrl + ALt + Left/Right arrow working. It's seem that i have only one workspace.

---

### Post by jonnyblue on 2006-03-24
[QUOTE=Treviño]Hello, is there anyone who made this in a **kubuntu** ***breezy***? I mean using **KDE**...

I've a notebook with an ATi mobility radeon 9700 (fglrx) I've tried to apply this guide editing /etc/kde3/kdm/kdmrc instaad of /etc/gdm/gdm.conf with command:
```
ServerCmd=/usr/X11R6/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
```
then adding the /usr/bin/thefuture code into a ~/.kde/Autostart/xstart_script

Btw, Xgl server seems to start, but remain the gray screen with my mouse cursor. KDE is not loaded... 
[/QUOTE]

I've got the same problem in gnome. Grey screen with mouse cursor... Nothing happens.

Thanks!

---

### Post by lizardking on 2006-03-24
[QUOTE=jonnyblue]I've got the same problem in gnome. Grey screen with mouse cursor... Nothing happens.

Thanks![/QUOTE]
idem

---

### Post by JedTheHead on 2006-03-24
Breezy, Radeon 9200 correctly configured with fglrx and followed these instructions and obtained the rpms from this forum.

One issue: because of the SuSE rpms (dloaded less than an hour ago), Xgl looks for /etc/sysconfig/displaymanager

sudo touch /etc/sysconfig/displaymanager 

seems to get it past this error, but I get the same as the above - plain X screen with forever spinning cursor.  

I tried all of this yesterday and had the same problem - with the exception of the /etc/sysconfig/dsplaymanager issue.

Also, I don't think "flexible=true" for Xgl works either - it gives an error as well.

Anyone have any ideas?!?!?  I am at Novell Brainshare with all the Xgl-enabled SuSE 10 users and I want to play too !  ;)  (And more importantly, show them that we can do it... heh)

Thanks for your efforts!!!

---

### Post by Treviño on 2006-03-24
Mh... Well... It seems I'm not alone, and first of all, *maybe*, kde isn't the problem and so also kubuntu breezy could work with xgl... Who knows! :)

Btw, I've seen in the SuSe wiki that in the file displaymanager (that is into another path) you must indicate the X server and changing it with XGL, maybe our problem is this...
We must find a displaymanager file to understand what is missing... 

Ideas?

PS: **_[lizardking]("http://www.ubuntuforums.org/member.php?u=5186")_** It seems we live really near, and that we do the same University :), btw I'm just on 2nd year. Are you a member of studenti.fi.it?

--------------------------

Edit: it seems that [JedTheHead]("http://www.ubuntuforums.org/member.php?u=29570") tought the same I had. :)

---

### Post by C_nemo on 2006-03-27
Thanks for the howto, 
It works on amd64 breezy as well, you just have to go through the OpenSuSE repositories and shop for the right packages. 
if you include libsvg and libsvg-cairo from the opensuse repositories (through alien) you will get the cube plugin working out of the box ( I think), worked for me, If anyone has plugins which refuse to load you can just look at the ldd ouput of the libraby and see if there are missing libraries

---

### Post by danielcs on 2006-03-27
I have a problem as well.

XLG+Compiz is partially working here, some plugins like **wobble** and **fade** work great but the **cube** and **transparency** don't.

I also noticed that before starting Compiz I have 4 virtual desktops as you can see in the attached image. When Compiz is running the desktop changer thingy gets messed up (as shown in the screen too). I'm left with only one desktop and if you check the changer thingy you'll see that it shows a desktop with messed up dimensions as well. Really strange!!

I can see some transparency in the title bars of windows but not in the middle of them. Also visible in the attached image.

One more thing I noticed: When I try to access the screensaver settings or when the screensaver is activated all my programs are closed and I'm sent back to the the login screen (like when you press the Shift+Backspace keys). Trying to run some stuff through Wine end up the same way.. back to the login screen. :(

I'm running Ubuntu Breezy (i386) here.

I appreciate if you can help.
BTW: Great guide on how to make it work. :KS

EDIT: Ok, got the Cube working! Here's how:
ALT+F2 > type gconf-editor > Press <enter>
Navigate to: apps > compiz > general > allscreens > options
Double-click **active_plugins** on the right pane.
Click Add and add these plugins, one by one: **cube**, **rotate** and **zoom**
Close gconf-editor, logout of your session and login again, CTRL+ALT+drag your desktop and you should see the cube!!!

The cube works but the little desktop switcher on the taskbar is still screwed.
And I still have the problems with the screensaver and Wine applications. :(

---

### Post by matheuswc on 2006-03-30
Error:


matheus@weber:~$ thefuture 
matheus@weber:~$ gnome-window-decorator, Failed to load shadow images
compiz: No composite extension

:confused:

---

### Post by danielcs on 2006-03-31
[QUOTE=matheuswc]Error:


matheus@weber:~$ thefuture 
matheus@weber:~$ gnome-window-decorator, Failed to load shadow images
compiz: No composite extension

:confused:[/QUOTE]

Try this.
ALT+F2, type **gksudo gedit** and put your password.
In gedit, click open and find the file **/etc/X11/xorg.conf**
Now scroll down to the end of the file and add this:
```
Section "Extensions"
	Option	"Composite"	"Enable"
EndSection
```

Save the file, logout and then login again.
If it doesn't work try rebooting the computer.

---

### Post by yootje on 2006-04-01
Besides other problems, I get the message /etc/sysconfig/displaymanager is not found (I'm not sure about the "/etc/", it could be an other directory.

Anyone who has a suggestion?

---

### Post by FedeXX on 2006-04-06
[QUOTE=vbmaster]Hey guys,

I get the blackscreen too after runing 'thefuture'. I only see my mouse and if i click on the blackarea that would match the menus and buttons I can barely see the windows opening, but they disapear. Ctrl+Alt+left, right didn't worked. :(

I would love get xgl working, I've a GeForce4 MX 440, and my xorg.conf is this: 

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
#	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"pt"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true" 
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
        Option  "Composite" "Enable"
EndSection

```

Can anyone help me? or it's just my graphic board that it's too low?

Thanks ;)[/QUOTE]

Same card, same problem... :-k No fix found...

---

### Post by yellow beard on 2006-04-07
awesome! got it going second time with no problems with my ati card. thanks alot!

---

### Post by tunafreedolphin on 2006-04-07
This worked perfectly for me. I have a NForce 4 motherboard, AMD 3700+ and a Nvidia 6800GS pci-e video card. 

Thanks!!!

---

### Post by yootje on 2006-04-09
[QUOTE=FedeXX]Same card, same problem... :-k No fix found...[/QUOTE]
I believe the section module eneds an extra #?

---

### Post by FedeXX on 2006-04-10
[QUOTE=yootje]I believe the section module eneds an extra #?[/QUOTE]

Mine xorg.conf has it too... Nothing to do, black screen. If in the black i type "killall compiz" something return visible... and in the console there are lots of lines like

compiz: Couldn't bind redirected window 0x2a0427f to texture
compiz: pixmap 0x2c00094 can't be bound to texture
compiz: Couldn't bind redirected window 0x2a0427f to texture
compiz: pixmap 0x2c00094 can't be bound to texture
compiz: Couldn't bind redirected window 0x2a0427f to texture
compiz: pixmap 0x2c00094 can't be bound to texture
compiz: Couldn't bind redirected window 0x2a0427f to texture

Any ideas?...

---

### Post by Straker on 2006-04-12
@Milamber_Cubed:

This line:

```

wget http://www.ubuntuforums.org/attachment.php?attachmentid=6289&d=1140433762

```

Is now busted.

Since the forum lockdown(?), you cant get a direct link using wget, it actually downloads the login.html page required for forum login.  Please move this to a direct link as in your other wgets, and update the how-to.  Thanks.

This is ridiculous, no searching unless you are logged in!  Nothing like building an iron curtain to spread the good news about Ubuntu. doh.  ](*,)

---

### Post by NoWhereMan on 2006-04-13
[QUOTE=Straker]This is ridiculous, no searching unless you are logged in!  Nothing like building an iron curtain to spread the good news about Ubuntu. doh.  ](*,)[/QUOTE]

Well, they must limit their bandwith use, somehow...

---

### Post by Jaimolistico on 2006-04-14
It works really fast for me!! I was a lot of time trying to install xgl on my computer, today I reinstalled it and I followed this instructions once more and they worked for me. I have to say that is AWESOME.

---

### Post by Milamber_Cubed on 2006-04-14
[QUOTE=Straker]@Milamber_Cubed:

This line:

```

wget http://www.ubuntuforums.org/attachment.php?attachmentid=6289&d=1140433762

```

Is now busted.

Since the forum lockdown(?), you cant get a direct link using wget, it actually downloads the login.html page required for forum login.  Please move this to a direct link as in your other wgets, and update the how-to.  Thanks.

This is ridiculous, no searching unless you are logged in!  Nothing like building an iron curtain to spread the good news about Ubuntu. doh.  ](*,)[/QUOTE]

Thanks for the heads up... sorted it now. It DOES seem all a bit heavy handed... especially the no searching bit. Ah well... :rolleyes:

---

### Post by Jureiz on 2006-04-14
Hi all, btw, I'm a newbie to this Ubuntu Breezy and xgl+compiz ( but not really a newbie to Linux =)   ).

I followed this instruction, and found it working. I forgot to thank you because I'm really amazed with this whole cool thing :D . Thanks a lot, man. Btw, there's something awkward. My friends, running a computer with Nvidia GeForce 4 MX, followed the same instructions as I did, but ended up with blank screen. Hmm, I don't know what's wrong with his computer. But, with the same computer, he couldn't install Ubuntu Drapper Drake, ended up with resolution problems. So, probably the problem is his graphic card. Wonder if there's a solution for that. 

Anyway, thanks man. I'm getting to love this ubuntu more nowadays ... :mrgreen:

---

### Post by Straker on 2006-04-15
[QUOTE=Jureiz]Hi all, btw, I'm a newbie to this Ubuntu Breezy and xgl+compiz ( but not really a newbie to Linux =)   ).

I followed this instruction, and found it working. I forgot to thank you because I'm really amazed with this whole cool thing :D . Thanks a lot, man. Btw, there's something awkward. My friends, running a computer with Nvidia GeForce 4 MX, followed the same instructions as I did, but ended up with blank screen. Hmm, I don't know what's wrong with his computer. But, with the same computer, he couldn't install Ubuntu Drapper Drake, ended up with resolution problems. So, probably the problem is his graphic card. Wonder if there's a solution for that. 

Anyway, thanks man. I'm getting to love this ubuntu more nowadays ... :mrgreen:[/QUOTE]

See this thread for help with your friend's Nvidia card: [http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+latest](http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+latest)

---

### Post by dengar on 2006-04-15
It seems I'm currently in the same boat as the people with the "/bin/sh: /etc/sysconfig/displaymanager: No such file or directory" problem. To be fair, I looked in said location, and there was indeed no displaymanager. Has anyone succsesfully resolved this problem?

(I'm using 810i btw)

---

### Post by Dropknee on 2006-04-15
Pls someone help me here I try a lot of thing but cant make it to work, I got the grey login screen with the busy cursor

this is my xorg
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig Screen 0" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # paths to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/CID"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load  "GLcore"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "Emulate3Buttons" "true"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 64.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 0"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon X800 XT (R420 JP)"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	Option	    "(null)"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon X800 XT (R420 JP)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig Screen 0"
	Device     "ATI Graphics Adapter 0"
	Monitor    "aticonfig Monitor 0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection
```

and this is my gdm.conf
```
# GDM Configuration file.  You can use gdmsetup program to graphically
# edit this, or you can optionally just edit this file by hand.  Note that
# gdmsetup does not tweak every option here, just the ones most users
# would care about.  Rest is for special setups and distro specific
# tweaks.  If you edit this file, you should run:
# /etc/init.d/gdm reload or /etc/init.d/gdm restart

# For full reference documentation see the gnome help browser under
# GNOME|System category.  You can also find the docs in HTML form on
# [http://www.gnome.org/projects/gdm/](http://www.gnome.org/projects/gdm/)
#
# NOTE: Some of these are commented out but still show their default values.
# If you wish to change them you must remove the '#' from the beginning of
# the line.  The commented out lines are lines where the default might
# change in the future, so set them one way or another if you feel
# strongly about it.
#
# Have fun! - George

[daemon]
# Automatic login, if true the first local screen will automatically logged
# in as user as set with AutomaticLogin key.
AutomaticLoginEnable=false
AutomaticLogin=

# Timed login, useful for kiosks.  Log in a certain user after a certain
# amount of time
TimedLoginEnable=false
TimedLogin=
TimedLoginDelay=30

# The gdm configuration program that is run from the login screen, you should
# probably leave this alone
#Configurator=/usr/sbin/gdmsetup --disable-sound --disable-crash-dialog

# The chooser program.  Must output the chosen host on stdout, probably you
# should leave this alone
#Chooser=/usr/lib/gdm/gdmchooser

# The greeter for local (non-xdmcp) logins.  Change gdmlogin to gdmgreeter to
# get the new graphical greeter.
Greeter=/usr/lib/gdm/gdmgreeter

# The greeter for xdmcp logins, usually you want a less graphically intensive
# greeter here so it's better to leave this with gdmlogin
#RemoteGreeter=/usr/lib/gdm/gdmlogin

# Launch the greeter with an additional list of colon seperated gtk 
# modules. This is useful for enabling additional feature support 
# e.g. gnome accessibility framework. Only "trusted" modules should
# be allowed to minimise security holes
#AddGtkModules=false
# By default these are the accessibility modules
#GtkModulesList=gail:atk-bridge:/usr/lib/gtk-2.0/modules/libdwellmouselistener:/usr/lib/gtk-2.0/modules/libkeymouselistener

# Default path to set.  The profile scripts will likely override this
DefaultPath=/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games
# Default path for root.  The profile scripts will likely override this
RootPath=/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games

# If you are having trouble with using a single server for a long time and
# want gdm to kill/restart the server, turn this on
#AlwaysRestartServer=false

# User and group used for running gdm GUI applicaitons.  By default this
# is set to user gdm and group gdm.  This user/group should have very
# limited permissions and access to ony the gdm directories and files.
User=gdm
Group=gdm

# To try to kill all clients started at greeter time or in the Init script.
# doesn't always work, only if those clients have a window of their own
#KillInitClients=true
LogDir=/var/log/gdm
# You should probably never change this value unless you have a weird setup
PidFile=/var/run/gdm.pid
# Note that a post login script is run before a PreSession script.
# It is run after the login is successful and before any setup is
# run on behalf of the user
PostLoginScriptDir=/etc/gdm/PostLogin/
PreSessionScriptDir=/etc/gdm/PreSession/
PostSessionScriptDir=/etc/gdm/PostSession/
DisplayInitDir=/etc/gdm/Init
# Distributions:  If you have some script that runs an X server in say
# VGA mode, allowing a login, could you please send it to me?
#FailsafeXServer=
# if X keeps crashing on us we run this script.  The default one does a bunch
# of cool stuff to figure out what to tell the user and such and can
# run an X configuration program.
XKeepsCrashing=/etc/gdm/XKeepsCrashing
# Reboot, Halt and suspend commands, you can add different commands
# separated by a semicolon and gdm will use the first one it can find
RebootCommand=/sbin/shutdown -r now \"Rebooted from gdm menu.\"
HaltCommand=/sbin/shutdown -h now \"Halted from gdm menu.\"
SuspendCommand=/usr/sbin/pmi action sleep
HibernateCommand=/usr/sbin/pmi action hibernate
# Probably should not touch the below this is the standard setup
ServAuthDir=/var/lib/gdm
# This is our standard startup script.  A bit different from a normal
# X session, but it shares a lot of stuff with that.  See the provided
# default for more information.
BaseXsession=/etc/gdm/Xsession
# This is a directory where .desktop files describing the sessions live
# It is really a PATH style variable since 2.4.4.2 to allow actual
# interoperability with KDM.  Note that <sysconfdir>/dm/Sessions is there
# for backwards compatibility reasons with 2.4.4.x
SessionDesktopDir=/etc/X11/sessions/:/etc/dm/Sessions/:/usr/share/gdm/BuiltInSessions/:/usr/share/xsessions/
# This is the default .desktop session.  One of the ones in SessionDesktopDir
DefaultSession=default.desktop
# Better leave this blank and HOME will be used.  You can use syntax ~/ below
# to indicate home directory of the user.  You can also set this to something
# like /tmp if you don't want the authorizations to be in home directories.
# This is useful if you have NFS mounted home directories.  Note that if this
# is the home directory the UserAuthFBDir will still be used in case the home
# directory is NFS, see security/NeverPlaceCookiesOnNFS to override this behaviour.
UserAuthDir=
# Fallback if home directory not writable
UserAuthFBDir=/tmp
UserAuthFile=.Xauthority
# The X server to use if we can't figure out what else to run.
StandardXServer=/usr/X11R6/bin/X
# The maximum number of flexible X servers to run.
#FlexibleXServers=5
# And after how many minutes should we reap the flexible server if there is
# no activity and no one logged on.  Set to 0 to turn off the reaping.
# Does not affect Xnest flexiservers.
#FlexiReapDelayMinutes=5
# the X nest command
Xnest=/usr/X11R6/bin/Xnest -br -audit 0 -name Xnest
# Automatic VT allocation.  Right now only works on Linux.  This way
# we force X to use specific vts.  turn VTAllocation to false if this
# is causing problems.
FirstVT=7
VTAllocation=true
# Should double login be treated with a warning (and possibility to change
# vts on linux and freebsd systems for console logins)
#DoubleLoginWarning=true
# Should a second login always resume the current session and
# switch vts on linux and freebsd systems for console logins
#AlwaysLoginCurrentSession=true

# If true then the last login information is printed to the user before
# being prompted for password.  While this gives away some info on what
# users are on a system, it on the other hand should give the user an
# idea of when they logged in and if it doesn't seem kosher to them,
# they can just abort the login and contact the sysadmin (avoids running
# malicious startup scripts)
#DisplayLastLogin=false

# Program used to play sounds.  Should not require any 'daemon' or anything
# like that as it will be run when no one is logged in yet.
SoundProgram=/usr/lib/gdmplay

# These are the languages that the console cannot handle because of font
# issues.  Here we mean the text console, not X.  This is only used
# when there are errors to report and we cannot start X.
# This is the default:
#ConsoleCannotHandle=am,ar,az,bn,el,fa,gu,hi,ja,ko,ml,mr,pa,ta,zh

# This determines whether gdm will honor requests DYNAMIC requests from
# the gdmdynamic command.
#DynamicXServers=false

# This determines whether gdm will send notifications to the console
#ConsoleNotify=true

[security]
# If any distributions ship with this one off, they should be shot
# this is only local, so it's only for say kiosk use, when you
# want to minimize possibility of breakin
AllowRoot=false
# If you want to be paranoid, turn this one off
AllowRemoteRoot=false
# This will allow remote timed login
AllowRemoteAutoLogin=false
# 0 is the most restrictive, 1 allows group write permissions, 2 allows all
# write permissions
RelaxPermissions=0
# Check if directories are owned by logon user.  Set to false, if you have, for
# example, home directories owned by some other user.
CheckDirOwner=true
# Number of seconds to wait after a bad login
#RetryDelay=1
# Maximum size of a file we wish to read.  This makes it hard for a user to DoS
# us by using a large file.
#UserMaxFile=65536
# If true this will basically append -nolisten tcp to every X command line,
# a good default to have (why is this a "negative" setting? because if
# it is false, you could still not allow it by setting command line of
# any particular server).  It's probably better to ship with this on
# since most users will not need this and it's more of a security risk
# then anything else.
# Note: Anytime we find a -query or -indirect on the command line we do
# not add a "-nolisten tcp", as then the query just wouldn't work, so
# this setting only affects truly local sessions.
DisallowTCP=true
# By default never place cookies if we "detect" NFS.  We detect NFS
# by detecting "root-squashing".  It seems bad practice to place
# cookies on things that go over the network by default and thus we
# don't do it by default.  Sometimes you can however use safe remote
# filesystems where this is OK and you may want to have the cookie in your
# home directory.
#NeverPlaceCookiesOnNFS=true

# XDMCP is the protocol that allows remote login.  If you want to log into
# gdm remotely (I'd never turn this on on open network, use ssh for such
# remote usage that).  You can then run X with -query <thishost> to log in,
# or -indirect <thishost> to run a chooser.  Look for the 'Terminal' server
# type at the bottom of this config file.
[xdmcp]
# Distributions: Ship with this off.  It is never a safe thing to leave
# out on the net.  Setting up /etc/hosts.allow and /etc/hosts.deny to only
# allow local access is another alternative but not the safest.
# Firewalling port 177 is the safest if you wish to have xdmcp on.
# Read the manual for more notes on the security of XDMCP.
Enable=false
# Honour indirect queries, we run a chooser for these, and then redirect
# the user to the chosen host.  Otherwise we just log the user in locally.
#HonorIndirect=true
# Maximum pending requests
#MaxPending=4
#MaxPendingIndirect=4
# Maximum open XDMCP sessions at any point in time
#MaxSessions=16
# Maximum wait times
#MaxWait=15
#MaxWaitIndirect=15
# How many times can a person log in from a single host.  Usually better to
# keep low to fend off DoS attacks by running many logins from a single
# host.  This is now set at 2 since if the server crashes then gdm doesn't
# know for some time and wouldn't allow another session.
#DisplaysPerHost=2
# The number of seconds after which a non-responsive session is logged off.
# Better keep this low.
#PingIntervalSeconds=15
# The port.  177 is the standard port so better keep it that way
#Port=177
# Willing script, none is shipped and by default we'll send
# hostname system id.  But if you supply something here, the
# output of this script will be sent as status of this host so that
# the chooser can display it.  You could for example send load,
# or mail details for some user, or some such.
#Willing=/etc/gdm/Xwilling

[gui]
# The specific gtkrc file we use.  It should be the full path to the gtkrc
# that we need.  Unless you need a specific gtkrc that doesn't correspond to
# a specific theme, then just use the GtkTheme key
#GtkRC=/usr/share/themes/Default/gtk-2.0/gtkrc

# The GTK+ theme to use for the gui
GtkTheme=Human
# If to allow changing the GTK+ (widget) theme from the greeter.  Currently
# this only affects the standard greeter as the graphical greeter does
# not yet have this ability
AllowGtkThemeChange=true
# Comma separated list of themes to allow.  These must be the names of the
# themes installed in the standard locations for gtk themes.  You can
# also specify 'all' to allow all installed themes.  These should be just
# the basenames of the themes such as 'Thinice' or 'LowContrast'.
GtkThemesToAllow=Human,HighContrast,HighContrastInverse,LowContrast

# Maximum size of an icon, larger icons are scaled down
#MaxIconWidth=128
#MaxIconHeight=128

[greeter]
# Greeter has a nice title bar that the user can move
#TitleBar=true
# Configuration is available from the system menu of the greeter
ConfigAvailable=false
# Face browser is enabled.  This only works currently for the
# standard greeter as it is not yet enabled in the graphical greeter.
Browser=false
# The default picture in the browser
#DefaultFace=/usr/share/pixmaps/nobody.png
# User ID's less than the MinimalUID value will not be included in the
# face browser or in the gdmselection list for Automatic/Timed login.
# They will not be displayed regardless of the settings for
# Include and Exclude.
MinimalUID=1000
# Users listed in Include will be included in the face browser and in
# the gdmsetup selection list for Automatic/Timed login.  Users
# should be separated by commas.
#Include=
# Users listed in Exclude are excluded from the face browser and from
# the gdmsetup selection list for Automatic/Timed login.  Excluded 
# users will still be able to log in, but will have to type their
# username.  Users should be separated by commas.  
Exclude=bin,daemon,adm,lp,sync,shutdown,halt,mail,news,uucp,operator,nobody,gdm,postgres,pvm,rpm
# By default, an empty include list means display no users.  By setting
# IncludeAll to true, the password file will be scanned and all users 
# will be displayed except users excluded via the Exclude setting and
# user ID's less than MinimalUID.  Scanning the password file can be
# slow on systems with large numbers of users and this feature should 
# not be used in such environments.  The setting of IncludeAll does
# nothing if Include is set to a non-empty value.
IncludeAll=true
# If user or user.png exists in this dir it will be used as his picture
#GlobalFaceDir=/usr/share/pixmaps/faces/
# File which contains the locale we show to the user.  Likely you want to use
# the one shipped with gdm and edit it.  It is not a standard locale.alias file,
# although gdm will be able to read a standard locale.alias file as well.
LocaleFile=/etc/gdm/locale.conf
# Logo shown in the standard greeter
#Logo=/usr/share/pixmaps/gdmDebianLogo.xpm
# The standard greeter should shake if a user entered the wrong username or
# password.  Kind of cool looking
#Quiver=true
# The Actions menu (formerly system menu) is shown in the greeter, this is the
# menu that contains reboot, shutdown, suspend, config and chooser.  None of
# these is available if this is off.  They can be turned off individually
# however
SystemMenu=true
# The Actions in the Actions menu require the root password
SecureSystemMenu=false
# Should the chooser button be shown.  If this is shown, GDM can drop into
# chooser mode which will run the xdmcp chooser locally and allow the user
# to connect to some remote host.  Local XDMCP does not need to be enabled
# however
#ChooserButton=true
# Welcome is for all console logins and RemoteWelcome is for remote logins
# (through XDMCP).
# DefaultWelcome and DefaultRemoteWelcome set the string for Welcome
# to "Welcome" and for DefaultWelcome to "Welcome to %n", and properly
# translate the message to the appropriate language.  Note that %n gets
# translated to the hostname of the machine.  These default values can
# be overridden by setting DefaultWelcome and/or DefaultRemoteWelcome to
# false, and setting the Welcome and DefaultWelcome values as desired.
# Just make sure the strings are in utf-8 Note to distributors, if you
# wish to have a different Welcome string and wish to have this
# translated you can have entries such as "Welcome[cs]=Vitejte na %n".
DefaultWelcome=true
DefaultRemoteWelcome=true
#Welcome=Welcome
#RemoteWelcome=Welcome to %n
# Don't allow user to move the standard greeter window.  Only makes sense
# if TitleBar is on
#LockPosition=false
# Set a position rather then just centering the window.  If you enter
# negative values for the position it is taken as an offset from the
# right or bottom edge.
#SetPosition=false
#PositionX=0
#PositionY=0
# Xinerama screen we use to display the greeter on.  Not for true
# multihead, currently only works for Xinerama.
#XineramaScreen=0
# Background settings for the standard greeter:
# Type can be 0=None, 1=Image, 2=Color
#BackgroundType=2
#BackgroundImage=
#BackgroundScaleToFit=true
BackgroundColor=#523921
# XDMCP session should only get a color, this is the sanest setting since
# you don't want to take up too much bandwidth
#BackgroundRemoteOnlyColor=true
# Program to run to draw the background in the standard greeter.  Perhaps
# something like an xscreensaver hack or some such.
#BackgroundProgram=
# if this is true then the background program is run always, otherwise
# it is only run when the BackgroundType is 0 (None)
#RunBackgroundProgramAlways=false
# Show the Failsafe sessions.  These are much MUCH nicer (focus for xterm for
# example) and more failsafe then those supplied by scripts so distros should
# use this rather then just running an xterm from a script.
#ShowGnomeFailsafeSession=true
#ShowXtermFailsafeSession=true
# Normally there is a session type called 'Last' that is shown which refers to
# the last session the user used.  If off, we will be in 'switchdesk' mode where
# the session saving stuff is disabled in GDM
#ShowLastSession=true
# Always use 24 hour clock no matter what the locale.
#Use24Clock=false
# Use circles in the password field.  Looks kind of cool actually,
# but only works with certain fonts.
UseCirclesInEntry=true
# Do not show any visible feedback in the password field. This is standard
# for instance in console, xdm and ssh.
#UseInvisibleInEntry=false
# These two keys are for the new greeter.  Circles is the standard
# shipped theme.  If you want gdm to select a random theme from a list
# then provide a list that is delimited by /: to the GraphicalThemes key and 
# set GraphicalThemeRand to true.  Otherwise use GraphicalTheme and specify
# just one theme.
GraphicalTheme=tango_gdm
#GraphicalThemes=circles/:happygnome
GraphicalThemes=circles
GraphicalThemeDir=/usr/share/gdm/themes/
GraphicalThemeRand=false
# If InfoMsgFile points to a file, the greeter will display the contents of the
# file in a modal dialog box before the user is allowed to log in.
#InfoMsgFile=
# If InfoMsgFile is present then InfoMsgFont can be used to specify the font
# to be used when displaying the contents of the file.
#InfoMsgFont=Sans 24
# If SoundOnLogin is true, then the greeter will beep when login is ready
# for user input.  If SoundOnLogin is a file and the greeter finds the
# 'play' executable (see daemon/SoundProgram) it will play that file
# instead of just beeping
SoundOnLogin=true
SoundOnLoginFile=/usr/share/sounds/question.wav
# If SoundOnLoginSuccess, then the greeter will play a sound (as above)
# when a user successfully logs in
#SoundOnLoginSuccess=false
#SoundOnLoginSuccessFile=
# If SoundOnLoginFailure, then the greeter will play a sound (as above)
# when a user fails to log in
#SoundOnLoginFailure=false
#SoundOnLoginFailureFile=

# The chooser is what's displayed when a user wants an indirect XDMCP
# session, or selects Run XDMCP chooser from the system menu
[chooser]
# Default image for hosts
#DefaultHostImg=/usr/share/pixmaps/nohost.png
# Directory with host images, they are named by the hosts: host or host.png
HostImageDir=/usr/share/hosts/
# Time we scan for hosts (well only the time we tell the user we are
# scanning actually, we continue to listen even after this has
# expired)
#ScanTime=4
# A comma separated lists of hosts to automatically add (if they answer to
# a query of course).  You can use this to reach hosts that broadcast cannot
# reach.
Hosts=
# Broadcast a query to get all hosts on the current network that answer
Broadcast=true
# Set it to true if you want to send a multicast query to hosts.
Multicast=false
# It is an IPv6 multicast address.It is hardcoded here and will be replaced when
# officially registered xdmcp multicast address of TBD will be available
#Multicast_Addr=ff02::1
# Allow adding random hosts to the list by typing in their names
#AllowAdd=true

[debug]
# This will enable debugging into the syslog, usually not neccessary
# and it creates a LOT of spew of random stuff to the syslog.  However it
# can be useful in determining when something is going very wrong.
Enable=false

[servers]
# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX). 
#1=Xgl 
# These are the standard servers.  You can add as many you want here
# and they will always be started.  Each line must start with a unique
# number and that will be the display number of that server.  Usually just
# the 0 server is used.
0=Standard
#1=Standard
# Note the VTAllocation and FirstVT keys on linux and freebsd.
# Don't add any vt<number> arguments if VTAllocation is on, and set FirstVT to
# be the first vt available that your gettys don't grab (gettys are usually
# dumb and grab even a vt that has already been taken).  Using 7 will work
# pretty much for all linux distributions.  VTAllocation is not currently
# implemented on anything but linux and freebsd.  Feel free to send patches.
# X servers will just not get any extra arguments then.
#
# If you want to run an X terminal you could add an X server such as this
#0=Terminal -query serverhostname
# or for a chooser (optionally serverhostname could be localhost)
#0=Terminal -indirect serverhostname
#
# If you wish to run the XDMCP chooser on the local display use the following
# line
#0=Chooser

## Note:
# is your X server not listening to TCP requests?  Perhaps you should look
# at the security/DisallowTCP setting!

# Definition of the standard X server.
[server-Standard]
name=Standard server
command=/usr/X11R6/bin/X -br -audit 0 
flexible=true

# To use this server type you should add -query host or -indirect host
# to the command line
[server-Terminal]
name=Terminal server
# Add -terminate to make things behave more nicely
command=/usr/X11R6/bin/X -br -audit 0 -terminate
# Make this not appear in the flexible servers (we need extra params
# anyway, and terminate would be bad for xdmcp choosing).  You can
# make a terminal server flexible, but not with an indirect query.
# If you need flexible indirect query server, then you must get rid
# of the -terminate and the only way to kill the flexible server will
# then be by Ctrl-Alt-Backspace
flexible=false
# Not local, we do not handle the logins for this X server
handled=false

# To use this server type you should add -query host or -indirect host
# to the command line
[server-Chooser]
name=Chooser server
command=/usr/X11R6/bin/X -br -audit 0
# Make this not appear in the flexible servers for now, but if you
# wish to allow a chooser server then make this true.  This is the
# only way to make a flexible chooser server that behaves nicely.
flexible=false
# Run the chooser instead of the greeter.  When the user chooses a
# machine they will get this same server but run with
# "-terminate -query hostname"
chooser=true
[server-Xgl] 
name=Xgl server 
command=/usr/X11R6/bin/Xgl :1 -fullscreen -ac -accel glx:fbo -accel xv:fbo
flexible=true
```


Pls help ](*,)

---

### Post by 23meg on 2006-04-16
Worked for me, but 2D performance is very low with my 64MB Geforce Go6200 running driver 8756; window resizing in apps with non-GTK widgets is especially slow. 2D performance is my #1 gripe with the present state of things on my machine (with Breezy's stock X), and I had a faint hope that XGL would accelerate things, but the opposite seems to be the case. I'll play with the options in the GDM configuration and see if that helps. 

*(Note to self: make a comprehensive post detailing all non-XGL 2D performance gripes)*

---

### Post by pwrstick on 2006-04-16
Thank you very much.  I missed this when I played with dapper, and didn't want to lost Automatix and everything just to get XGL working.

This, as far as I can tell after working with it for 5 minutes, works perfectly.  I'm playing a Lost episode and it does the wavy thing when I move the media window and plays it over the edge of the cube just like in the demonstration.

Fun!  Thanks for posting this.

P.S.  I'm using an Nvidia 6800GT and latest breezy

---

### Post by SirKillalot on 2006-04-16
[QUOTE=Dropknee]Pls someone help me here I try a lot of thing but cant make it to work, I got the grey login screen with the busy cursor

this is my xorg
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig Screen 0" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # paths to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/CID"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load  "GLcore"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "Emulate3Buttons" "true"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 64.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 0"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon X800 XT (R420 JP)"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	Option	    "(null)"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon X800 XT (R420 JP)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig Screen 0"
	Device     "ATI Graphics Adapter 0"
	Monitor    "aticonfig Monitor 0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection
```

and this is my gdm.conf
```
# GDM Configuration file.  You can use gdmsetup program to graphically
# edit this, or you can optionally just edit this file by hand.  Note that
# gdmsetup does not tweak every option here, just the ones most users
# would care about.  Rest is for special setups and distro specific
# tweaks.  If you edit this file, you should run:
# /etc/init.d/gdm reload or /etc/init.d/gdm restart

# For full reference documentation see the gnome help browser under
# GNOME|System category.  You can also find the docs in HTML form on
# [http://www.gnome.org/projects/gdm/](http://www.gnome.org/projects/gdm/)
#
# NOTE: Some of these are commented out but still show their default values.
# If you wish to change them you must remove the '#' from the beginning of
# the line.  The commented out lines are lines where the default might
# change in the future, so set them one way or another if you feel
# strongly about it.
#
# Have fun! - George

[daemon]
# Automatic login, if true the first local screen will automatically logged
# in as user as set with AutomaticLogin key.
AutomaticLoginEnable=false
AutomaticLogin=

# Timed login, useful for kiosks.  Log in a certain user after a certain
# amount of time
TimedLoginEnable=false
TimedLogin=
TimedLoginDelay=30

# The gdm configuration program that is run from the login screen, you should
# probably leave this alone
#Configurator=/usr/sbin/gdmsetup --disable-sound --disable-crash-dialog

# The chooser program.  Must output the chosen host on stdout, probably you
# should leave this alone
#Chooser=/usr/lib/gdm/gdmchooser

# The greeter for local (non-xdmcp) logins.  Change gdmlogin to gdmgreeter to
# get the new graphical greeter.
Greeter=/usr/lib/gdm/gdmgreeter

# The greeter for xdmcp logins, usually you want a less graphically intensive
# greeter here so it's better to leave this with gdmlogin
#RemoteGreeter=/usr/lib/gdm/gdmlogin

# Launch the greeter with an additional list of colon seperated gtk 
# modules. This is useful for enabling additional feature support 
# e.g. gnome accessibility framework. Only "trusted" modules should
# be allowed to minimise security holes
#AddGtkModules=false
# By default these are the accessibility modules
#GtkModulesList=gail:atk-bridge:/usr/lib/gtk-2.0/modules/libdwellmouselistener:/usr/lib/gtk-2.0/modules/libkeymouselistener

# Default path to set.  The profile scripts will likely override this
DefaultPath=/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games
# Default path for root.  The profile scripts will likely override this
RootPath=/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games

# If you are having trouble with using a single server for a long time and
# want gdm to kill/restart the server, turn this on
#AlwaysRestartServer=false

# User and group used for running gdm GUI applicaitons.  By default this
# is set to user gdm and group gdm.  This user/group should have very
# limited permissions and access to ony the gdm directories and files.
User=gdm
Group=gdm

# To try to kill all clients started at greeter time or in the Init script.
# doesn't always work, only if those clients have a window of their own
#KillInitClients=true
LogDir=/var/log/gdm
# You should probably never change this value unless you have a weird setup
PidFile=/var/run/gdm.pid
# Note that a post login script is run before a PreSession script.
# It is run after the login is successful and before any setup is
# run on behalf of the user
PostLoginScriptDir=/etc/gdm/PostLogin/
PreSessionScriptDir=/etc/gdm/PreSession/
PostSessionScriptDir=/etc/gdm/PostSession/
DisplayInitDir=/etc/gdm/Init
# Distributions:  If you have some script that runs an X server in say
# VGA mode, allowing a login, could you please send it to me?
#FailsafeXServer=
# if X keeps crashing on us we run this script.  The default one does a bunch
# of cool stuff to figure out what to tell the user and such and can
# run an X configuration program.
XKeepsCrashing=/etc/gdm/XKeepsCrashing
# Reboot, Halt and suspend commands, you can add different commands
# separated by a semicolon and gdm will use the first one it can find
RebootCommand=/sbin/shutdown -r now \"Rebooted from gdm menu.\"
HaltCommand=/sbin/shutdown -h now \"Halted from gdm menu.\"
SuspendCommand=/usr/sbin/pmi action sleep
HibernateCommand=/usr/sbin/pmi action hibernate
# Probably should not touch the below this is the standard setup
ServAuthDir=/var/lib/gdm
# This is our standard startup script.  A bit different from a normal
# X session, but it shares a lot of stuff with that.  See the provided
# default for more information.
BaseXsession=/etc/gdm/Xsession
# This is a directory where .desktop files describing the sessions live
# It is really a PATH style variable since 2.4.4.2 to allow actual
# interoperability with KDM.  Note that <sysconfdir>/dm/Sessions is there
# for backwards compatibility reasons with 2.4.4.x
SessionDesktopDir=/etc/X11/sessions/:/etc/dm/Sessions/:/usr/share/gdm/BuiltInSessions/:/usr/share/xsessions/
# This is the default .desktop session.  One of the ones in SessionDesktopDir
DefaultSession=default.desktop
# Better leave this blank and HOME will be used.  You can use syntax ~/ below
# to indicate home directory of the user.  You can also set this to something
# like /tmp if you don't want the authorizations to be in home directories.
# This is useful if you have NFS mounted home directories.  Note that if this
# is the home directory the UserAuthFBDir will still be used in case the home
# directory is NFS, see security/NeverPlaceCookiesOnNFS to override this behaviour.
UserAuthDir=
# Fallback if home directory not writable
UserAuthFBDir=/tmp
UserAuthFile=.Xauthority
# The X server to use if we can't figure out what else to run.
StandardXServer=/usr/X11R6/bin/X
# The maximum number of flexible X servers to run.
#FlexibleXServers=5
# And after how many minutes should we reap the flexible server if there is
# no activity and no one logged on.  Set to 0 to turn off the reaping.
# Does not affect Xnest flexiservers.
#FlexiReapDelayMinutes=5
# the X nest command
Xnest=/usr/X11R6/bin/Xnest -br -audit 0 -name Xnest
# Automatic VT allocation.  Right now only works on Linux.  This way
# we force X to use specific vts.  turn VTAllocation to false if this
# is causing problems.
FirstVT=7
VTAllocation=true
# Should double login be treated with a warning (and possibility to change
# vts on linux and freebsd systems for console logins)
#DoubleLoginWarning=true
# Should a second login always resume the current session and
# switch vts on linux and freebsd systems for console logins
#AlwaysLoginCurrentSession=true

# If true then the last login information is printed to the user before
# being prompted for password.  While this gives away some info on what
# users are on a system, it on the other hand should give the user an
# idea of when they logged in and if it doesn't seem kosher to them,
# they can just abort the login and contact the sysadmin (avoids running
# malicious startup scripts)
#DisplayLastLogin=false

# Program used to play sounds.  Should not require any 'daemon' or anything
# like that as it will be run when no one is logged in yet.
SoundProgram=/usr/lib/gdmplay

# These are the languages that the console cannot handle because of font
# issues.  Here we mean the text console, not X.  This is only used
# when there are errors to report and we cannot start X.
# This is the default:
#ConsoleCannotHandle=am,ar,az,bn,el,fa,gu,hi,ja,ko,ml,mr,pa,ta,zh

# This determines whether gdm will honor requests DYNAMIC requests from
# the gdmdynamic command.
#DynamicXServers=false

# This determines whether gdm will send notifications to the console
#ConsoleNotify=true

[security]
# If any distributions ship with this one off, they should be shot
# this is only local, so it's only for say kiosk use, when you
# want to minimize possibility of breakin
AllowRoot=false
# If you want to be paranoid, turn this one off
AllowRemoteRoot=false
# This will allow remote timed login
AllowRemoteAutoLogin=false
# 0 is the most restrictive, 1 allows group write permissions, 2 allows all
# write permissions
RelaxPermissions=0
# Check if directories are owned by logon user.  Set to false, if you have, for
# example, home directories owned by some other user.
CheckDirOwner=true
# Number of seconds to wait after a bad login
#RetryDelay=1
# Maximum size of a file we wish to read.  This makes it hard for a user to DoS
# us by using a large file.
#UserMaxFile=65536
# If true this will basically append -nolisten tcp to every X command line,
# a good default to have (why is this a "negative" setting? because if
# it is false, you could still not allow it by setting command line of
# any particular server).  It's probably better to ship with this on
# since most users will not need this and it's more of a security risk
# then anything else.
# Note: Anytime we find a -query or -indirect on the command line we do
# not add a "-nolisten tcp", as then the query just wouldn't work, so
# this setting only affects truly local sessions.
DisallowTCP=true
# By default never place cookies if we "detect" NFS.  We detect NFS
# by detecting "root-squashing".  It seems bad practice to place
# cookies on things that go over the network by default and thus we
# don't do it by default.  Sometimes you can however use safe remote
# filesystems where this is OK and you may want to have the cookie in your
# home directory.
#NeverPlaceCookiesOnNFS=true

# XDMCP is the protocol that allows remote login.  If you want to log into
# gdm remotely (I'd never turn this on on open network, use ssh for such
# remote usage that).  You can then run X with -query <thishost> to log in,
# or -indirect <thishost> to run a chooser.  Look for the 'Terminal' server
# type at the bottom of this config file.
[xdmcp]
# Distributions: Ship with this off.  It is never a safe thing to leave
# out on the net.  Setting up /etc/hosts.allow and /etc/hosts.deny to only
# allow local access is another alternative but not the safest.
# Firewalling port 177 is the safest if you wish to have xdmcp on.
# Read the manual for more notes on the security of XDMCP.
Enable=false
# Honour indirect queries, we run a chooser for these, and then redirect
# the user to the chosen host.  Otherwise we just log the user in locally.
#HonorIndirect=true
# Maximum pending requests
#MaxPending=4
#MaxPendingIndirect=4
# Maximum open XDMCP sessions at any point in time
#MaxSessions=16
# Maximum wait times
#MaxWait=15
#MaxWaitIndirect=15
# How many times can a person log in from a single host.  Usually better to
# keep low to fend off DoS attacks by running many logins from a single
# host.  This is now set at 2 since if the server crashes then gdm doesn't
# know for some time and wouldn't allow another session.
#DisplaysPerHost=2
# The number of seconds after which a non-responsive session is logged off.
# Better keep this low.
#PingIntervalSeconds=15
# The port.  177 is the standard port so better keep it that way
#Port=177
# Willing script, none is shipped and by default we'll send
# hostname system id.  But if you supply something here, the
# output of this script will be sent as status of this host so that
# the chooser can display it.  You could for example send load,
# or mail details for some user, or some such.
#Willing=/etc/gdm/Xwilling

[gui]
# The specific gtkrc file we use.  It should be the full path to the gtkrc
# that we need.  Unless you need a specific gtkrc that doesn't correspond to
# a specific theme, then just use the GtkTheme key
#GtkRC=/usr/share/themes/Default/gtk-2.0/gtkrc

# The GTK+ theme to use for the gui
GtkTheme=Human
# If to allow changing the GTK+ (widget) theme from the greeter.  Currently
# this only affects the standard greeter as the graphical greeter does
# not yet have this ability
AllowGtkThemeChange=true
# Comma separated list of themes to allow.  These must be the names of the
# themes installed in the standard locations for gtk themes.  You can
# also specify 'all' to allow all installed themes.  These should be just
# the basenames of the themes such as 'Thinice' or 'LowContrast'.
GtkThemesToAllow=Human,HighContrast,HighContrastInverse,LowContrast

# Maximum size of an icon, larger icons are scaled down
#MaxIconWidth=128
#MaxIconHeight=128

[greeter]
# Greeter has a nice title bar that the user can move
#TitleBar=true
# Configuration is available from the system menu of the greeter
ConfigAvailable=false
# Face browser is enabled.  This only works currently for the
# standard greeter as it is not yet enabled in the graphical greeter.
Browser=false
# The default picture in the browser
#DefaultFace=/usr/share/pixmaps/nobody.png
# User ID's less than the MinimalUID value will not be included in the
# face browser or in the gdmselection list for Automatic/Timed login.
# They will not be displayed regardless of the settings for
# Include and Exclude.
MinimalUID=1000
# Users listed in Include will be included in the face browser and in
# the gdmsetup selection list for Automatic/Timed login.  Users
# should be separated by commas.
#Include=
# Users listed in Exclude are excluded from the face browser and from
# the gdmsetup selection list for Automatic/Timed login.  Excluded 
# users will still be able to log in, but will have to type their
# username.  Users should be separated by commas.  
Exclude=bin,daemon,adm,lp,sync,shutdown,halt,mail,news,uucp,operator,nobody,gdm,postgres,pvm,rpm
# By default, an empty include list means display no users.  By setting
# IncludeAll to true, the password file will be scanned and all users 
# will be displayed except users excluded via the Exclude setting and
# user ID's less than MinimalUID.  Scanning the password file can be
# slow on systems with large numbers of users and this feature should 
# not be used in such environments.  The setting of IncludeAll does
# nothing if Include is set to a non-empty value.
IncludeAll=true
# If user or user.png exists in this dir it will be used as his picture
#GlobalFaceDir=/usr/share/pixmaps/faces/
# File which contains the locale we show to the user.  Likely you want to use
# the one shipped with gdm and edit it.  It is not a standard locale.alias file,
# although gdm will be able to read a standard locale.alias file as well.
LocaleFile=/etc/gdm/locale.conf
# Logo shown in the standard greeter
#Logo=/usr/share/pixmaps/gdmDebianLogo.xpm
# The standard greeter should shake if a user entered the wrong username or
# password.  Kind of cool looking
#Quiver=true
# The Actions menu (formerly system menu) is shown in the greeter, this is the
# menu that contains reboot, shutdown, suspend, config and chooser.  None of
# these is available if this is off.  They can be turned off individually
# however
SystemMenu=true
# The Actions in the Actions menu require the root password
SecureSystemMenu=false
# Should the chooser button be shown.  If this is shown, GDM can drop into
# chooser mode which will run the xdmcp chooser locally and allow the user
# to connect to some remote host.  Local XDMCP does not need to be enabled
# however
#ChooserButton=true
# Welcome is for all console logins and RemoteWelcome is for remote logins
# (through XDMCP).
# DefaultWelcome and DefaultRemoteWelcome set the string for Welcome
# to "Welcome" and for DefaultWelcome to "Welcome to %n", and properly
# translate the message to the appropriate language.  Note that %n gets
# translated to the hostname of the machine.  These default values can
# be overridden by setting DefaultWelcome and/or DefaultRemoteWelcome to
# false, and setting the Welcome and DefaultWelcome values as desired.
# Just make sure the strings are in utf-8 Note to distributors, if you
# wish to have a different Welcome string and wish to have this
# translated you can have entries such as "Welcome[cs]=Vitejte na %n".
DefaultWelcome=true
DefaultRemoteWelcome=true
#Welcome=Welcome
#RemoteWelcome=Welcome to %n
# Don't allow user to move the standard greeter window.  Only makes sense
# if TitleBar is on
#LockPosition=false
# Set a position rather then just centering the window.  If you enter
# negative values for the position it is taken as an offset from the
# right or bottom edge.
#SetPosition=false
#PositionX=0
#PositionY=0
# Xinerama screen we use to display the greeter on.  Not for true
# multihead, currently only works for Xinerama.
#XineramaScreen=0
# Background settings for the standard greeter:
# Type can be 0=None, 1=Image, 2=Color
#BackgroundType=2
#BackgroundImage=
#BackgroundScaleToFit=true
BackgroundColor=#523921
# XDMCP session should only get a color, this is the sanest setting since
# you don't want to take up too much bandwidth
#BackgroundRemoteOnlyColor=true
# Program to run to draw the background in the standard greeter.  Perhaps
# something like an xscreensaver hack or some such.
#BackgroundProgram=
# if this is true then the background program is run always, otherwise
# it is only run when the BackgroundType is 0 (None)
#RunBackgroundProgramAlways=false
# Show the Failsafe sessions.  These are much MUCH nicer (focus for xterm for
# example) and more failsafe then those supplied by scripts so distros should
# use this rather then just running an xterm from a script.
#ShowGnomeFailsafeSession=true
#ShowXtermFailsafeSession=true
# Normally there is a session type called 'Last' that is shown which refers to
# the last session the user used.  If off, we will be in 'switchdesk' mode where
# the session saving stuff is disabled in GDM
#ShowLastSession=true
# Always use 24 hour clock no matter what the locale.
#Use24Clock=false
# Use circles in the password field.  Looks kind of cool actually,
# but only works with certain fonts.
UseCirclesInEntry=true
# Do not show any visible feedback in the password field. This is standard
# for instance in console, xdm and ssh.
#UseInvisibleInEntry=false
# These two keys are for the new greeter.  Circles is the standard
# shipped theme.  If you want gdm to select a random theme from a list
# then provide a list that is delimited by /: to the GraphicalThemes key and 
# set GraphicalThemeRand to true.  Otherwise use GraphicalTheme and specify
# just one theme.
GraphicalTheme=tango_gdm
#GraphicalThemes=circles/:happygnome
GraphicalThemes=circles
GraphicalThemeDir=/usr/share/gdm/themes/
GraphicalThemeRand=false
# If InfoMsgFile points to a file, the greeter will display the contents of the
# file in a modal dialog box before the user is allowed to log in.
#InfoMsgFile=
# If InfoMsgFile is present then InfoMsgFont can be used to specify the font
# to be used when displaying the contents of the file.
#InfoMsgFont=Sans 24
# If SoundOnLogin is true, then the greeter will beep when login is ready
# for user input.  If SoundOnLogin is a file and the greeter finds the
# 'play' executable (see daemon/SoundProgram) it will play that file
# instead of just beeping
SoundOnLogin=true
SoundOnLoginFile=/usr/share/sounds/question.wav
# If SoundOnLoginSuccess, then the greeter will play a sound (as above)
# when a user successfully logs in
#SoundOnLoginSuccess=false
#SoundOnLoginSuccessFile=
# If SoundOnLoginFailure, then the greeter will play a sound (as above)
# when a user fails to log in
#SoundOnLoginFailure=false
#SoundOnLoginFailureFile=

# The chooser is what's displayed when a user wants an indirect XDMCP
# session, or selects Run XDMCP chooser from the system menu
[chooser]
# Default image for hosts
#DefaultHostImg=/usr/share/pixmaps/nohost.png
# Directory with host images, they are named by the hosts: host or host.png
HostImageDir=/usr/share/hosts/
# Time we scan for hosts (well only the time we tell the user we are
# scanning actually, we continue to listen even after this has
# expired)
#ScanTime=4
# A comma separated lists of hosts to automatically add (if they answer to
# a query of course).  You can use this to reach hosts that broadcast cannot
# reach.
Hosts=
# Broadcast a query to get all hosts on the current network that answer
Broadcast=true
# Set it to true if you want to send a multicast query to hosts.
Multicast=false
# It is an IPv6 multicast address.It is hardcoded here and will be replaced when
# officially registered xdmcp multicast address of TBD will be available
#Multicast_Addr=ff02::1
# Allow adding random hosts to the list by typing in their names
#AllowAdd=true

[debug]
# This will enable debugging into the syslog, usually not neccessary
# and it creates a LOT of spew of random stuff to the syslog.  However it
# can be useful in determining when something is going very wrong.
Enable=false

[servers]
# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX). 
#1=Xgl 
# These are the standard servers.  You can add as many you want here
# and they will always be started.  Each line must start with a unique
# number and that will be the display number of that server.  Usually just
# the 0 server is used.
0=Standard
#1=Standard
# Note the VTAllocation and FirstVT keys on linux and freebsd.
# Don't add any vt<number> arguments if VTAllocation is on, and set FirstVT to
# be the first vt available that your gettys don't grab (gettys are usually
# dumb and grab even a vt that has already been taken).  Using 7 will work
# pretty much for all linux distributions.  VTAllocation is not currently
# implemented on anything but linux and freebsd.  Feel free to send patches.
# X servers will just not get any extra arguments then.
#
# If you want to run an X terminal you could add an X server such as this
#0=Terminal -query serverhostname
# or for a chooser (optionally serverhostname could be localhost)
#0=Terminal -indirect serverhostname
#
# If you wish to run the XDMCP chooser on the local display use the following
# line
#0=Chooser

## Note:
# is your X server not listening to TCP requests?  Perhaps you should look
# at the security/DisallowTCP setting!

# Definition of the standard X server.
[server-Standard]
name=Standard server
command=/usr/X11R6/bin/X -br -audit 0 
flexible=true

# To use this server type you should add -query host or -indirect host
# to the command line
[server-Terminal]
name=Terminal server
# Add -terminate to make things behave more nicely
command=/usr/X11R6/bin/X -br -audit 0 -terminate
# Make this not appear in the flexible servers (we need extra params
# anyway, and terminate would be bad for xdmcp choosing).  You can
# make a terminal server flexible, but not with an indirect query.
# If you need flexible indirect query server, then you must get rid
# of the -terminate and the only way to kill the flexible server will
# then be by Ctrl-Alt-Backspace
flexible=false
# Not local, we do not handle the logins for this X server
handled=false

# To use this server type you should add -query host or -indirect host
# to the command line
[server-Chooser]
name=Chooser server
command=/usr/X11R6/bin/X -br -audit 0
# Make this not appear in the flexible servers for now, but if you
# wish to allow a chooser server then make this true.  This is the
# only way to make a flexible chooser server that behaves nicely.
flexible=false
# Run the chooser instead of the greeter.  When the user chooses a
# machine they will get this same server but run with
# "-terminate -query hostname"
chooser=true
[server-Xgl] 
name=Xgl server 
command=/usr/X11R6/bin/Xgl :1 -fullscreen -ac -accel glx:fbo -accel xv:fbo
flexible=true
```


Pls help ](*,)[/QUOTE]

same problem here!

---

### Post by pwrstick on 2006-04-16
I have noticed that transparencies don't seem to work.  The descriptive bar at the top of an application has a slight transparent gradient, but I cannot ALT-Mouse Wheel to set the transparency.

I'm not sure why this is.

---

### Post by Milamber_Cubed on 2006-04-16
[QUOTE=pwrstick]I have noticed that transparencies don't seem to work.  The descriptive bar at the top of an application has a slight transparent gradient, but I cannot ALT-Mouse Wheel to set the transparency.

I'm not sure why this is.[/QUOTE]

You need to load the opacity module as discussed in other threads. The version of compiz in the RPMs I used didn't include it.

---

### Post by 23meg on 2006-04-17
You can also use transset or transset-df to set opacity.

---

### Post by pwrstick on 2006-04-18
[QUOTE=Milamber_Cubed]You need to load the opacity module as discussed in other threads. The version of compiz in the RPMs I used didn't include it.[/QUOTE]

Alternatively I could get the new rpms and go through the tutorial again, right?  I've been trying to find them and can't -- where did you get them?  I'm on Suse's site ([http://en.opensuse.org/Xgl](http://en.opensuse.org/Xgl)) and can't seem to find files that are like the ones you've hosted.

---

### Post by FedeXX on 2006-04-18
[QUOTE=Dropknee]Pls someone help me here I try a lot of thing but cant make it to work, I got the grey login screen with the busy cursor

this is my xorg
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig Screen 0" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # paths to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/CID"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load  "GLcore"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "Emulate3Buttons" "true"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 64.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 0"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon X800 XT (R420 JP)"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	Option	    "(null)"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon X800 XT (R420 JP)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig Screen 0"
	Device     "ATI Graphics Adapter 0"
	Monitor    "aticonfig Monitor 0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection
```

and this is my gdm.conf
```
# GDM Configuration file.  You can use gdmsetup program to graphically
# edit this, or you can optionally just edit this file by hand.  Note that
# gdmsetup does not tweak every option here, just the ones most users
# would care about.  Rest is for special setups and distro specific
# tweaks.  If you edit this file, you should run:
# /etc/init.d/gdm reload or /etc/init.d/gdm restart

# For full reference documentation see the gnome help browser under
# GNOME|System category.  You can also find the docs in HTML form on
# [http://www.gnome.org/projects/gdm/](http://www.gnome.org/projects/gdm/)
#
# NOTE: Some of these are commented out but still show their default values.
# If you wish to change them you must remove the '#' from the beginning of
# the line.  The commented out lines are lines where the default might
# change in the future, so set them one way or another if you feel
# strongly about it.
#
# Have fun! - George

[daemon]
# Automatic login, if true the first local screen will automatically logged
# in as user as set with AutomaticLogin key.
AutomaticLoginEnable=false
AutomaticLogin=

# Timed login, useful for kiosks.  Log in a certain user after a certain
# amount of time
TimedLoginEnable=false
TimedLogin=
TimedLoginDelay=30

# The gdm configuration program that is run from the login screen, you should
# probably leave this alone
#Configurator=/usr/sbin/gdmsetup --disable-sound --disable-crash-dialog

# The chooser program.  Must output the chosen host on stdout, probably you
# should leave this alone
#Chooser=/usr/lib/gdm/gdmchooser

# The greeter for local (non-xdmcp) logins.  Change gdmlogin to gdmgreeter to
# get the new graphical greeter.
Greeter=/usr/lib/gdm/gdmgreeter

# The greeter for xdmcp logins, usually you want a less graphically intensive
# greeter here so it's better to leave this with gdmlogin
#RemoteGreeter=/usr/lib/gdm/gdmlogin

# Launch the greeter with an additional list of colon seperated gtk 
# modules. This is useful for enabling additional feature support 
# e.g. gnome accessibility framework. Only "trusted" modules should
# be allowed to minimise security holes
#AddGtkModules=false
# By default these are the accessibility modules
#GtkModulesList=gail:atk-bridge:/usr/lib/gtk-2.0/modules/libdwellmouselistener:/usr/lib/gtk-2.0/modules/libkeymouselistener

# Default path to set.  The profile scripts will likely override this
DefaultPath=/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games
# Default path for root.  The profile scripts will likely override this
RootPath=/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games

# If you are having trouble with using a single server for a long time and
# want gdm to kill/restart the server, turn this on
#AlwaysRestartServer=false

# User and group used for running gdm GUI applicaitons.  By default this
# is set to user gdm and group gdm.  This user/group should have very
# limited permissions and access to ony the gdm directories and files.
User=gdm
Group=gdm

# To try to kill all clients started at greeter time or in the Init script.
# doesn't always work, only if those clients have a window of their own
#KillInitClients=true
LogDir=/var/log/gdm
# You should probably never change this value unless you have a weird setup
PidFile=/var/run/gdm.pid
# Note that a post login script is run before a PreSession script.
# It is run after the login is successful and before any setup is
# run on behalf of the user
PostLoginScriptDir=/etc/gdm/PostLogin/
PreSessionScriptDir=/etc/gdm/PreSession/
PostSessionScriptDir=/etc/gdm/PostSession/
DisplayInitDir=/etc/gdm/Init
# Distributions:  If you have some script that runs an X server in say
# VGA mode, allowing a login, could you please send it to me?
#FailsafeXServer=
# if X keeps crashing on us we run this script.  The default one does a bunch
# of cool stuff to figure out what to tell the user and such and can
# run an X configuration program.
XKeepsCrashing=/etc/gdm/XKeepsCrashing
# Reboot, Halt and suspend commands, you can add different commands
# separated by a semicolon and gdm will use the first one it can find
RebootCommand=/sbin/shutdown -r now \"Rebooted from gdm menu.\"
HaltCommand=/sbin/shutdown -h now \"Halted from gdm menu.\"
SuspendCommand=/usr/sbin/pmi action sleep
HibernateCommand=/usr/sbin/pmi action hibernate
# Probably should not touch the below this is the standard setup
ServAuthDir=/var/lib/gdm
# This is our standard startup script.  A bit different from a normal
# X session, but it shares a lot of stuff with that.  See the provided
# default for more information.
BaseXsession=/etc/gdm/Xsession
# This is a directory where .desktop files describing the sessions live
# It is really a PATH style variable since 2.4.4.2 to allow actual
# interoperability with KDM.  Note that <sysconfdir>/dm/Sessions is there
# for backwards compatibility reasons with 2.4.4.x
SessionDesktopDir=/etc/X11/sessions/:/etc/dm/Sessions/:/usr/share/gdm/BuiltInSessions/:/usr/share/xsessions/
# This is the default .desktop session.  One of the ones in SessionDesktopDir
DefaultSession=default.desktop
# Better leave this blank and HOME will be used.  You can use syntax ~/ below
# to indicate home directory of the user.  You can also set this to something
# like /tmp if you don't want the authorizations to be in home directories.
# This is useful if you have NFS mounted home directories.  Note that if this
# is the home directory the UserAuthFBDir will still be used in case the home
# directory is NFS, see security/NeverPlaceCookiesOnNFS to override this behaviour.
UserAuthDir=
# Fallback if home directory not writable
UserAuthFBDir=/tmp
UserAuthFile=.Xauthority
# The X server to use if we can't figure out what else to run.
StandardXServer=/usr/X11R6/bin/X
# The maximum number of flexible X servers to run.
#FlexibleXServers=5
# And after how many minutes should we reap the flexible server if there is
# no activity and no one logged on.  Set to 0 to turn off the reaping.
# Does not affect Xnest flexiservers.
#FlexiReapDelayMinutes=5
# the X nest command
Xnest=/usr/X11R6/bin/Xnest -br -audit 0 -name Xnest
# Automatic VT allocation.  Right now only works on Linux.  This way
# we force X to use specific vts.  turn VTAllocation to false if this
# is causing problems.
FirstVT=7
VTAllocation=true
# Should double login be treated with a warning (and possibility to change
# vts on linux and freebsd systems for console logins)
#DoubleLoginWarning=true
# Should a second login always resume the current session and
# switch vts on linux and freebsd systems for console logins
#AlwaysLoginCurrentSession=true

# If true then the last login information is printed to the user before
# being prompted for password.  While this gives away some info on what
# users are on a system, it on the other hand should give the user an
# idea of when they logged in and if it doesn't seem kosher to them,
# they can just abort the login and contact the sysadmin (avoids running
# malicious startup scripts)
#DisplayLastLogin=false

# Program used to play sounds.  Should not require any 'daemon' or anything
# like that as it will be run when no one is logged in yet.
SoundProgram=/usr/lib/gdmplay

# These are the languages that the console cannot handle because of font
# issues.  Here we mean the text console, not X.  This is only used
# when there are errors to report and we cannot start X.
# This is the default:
#ConsoleCannotHandle=am,ar,az,bn,el,fa,gu,hi,ja,ko,ml,mr,pa,ta,zh

# This determines whether gdm will honor requests DYNAMIC requests from
# the gdmdynamic command.
#DynamicXServers=false

# This determines whether gdm will send notifications to the console
#ConsoleNotify=true

[security]
# If any distributions ship with this one off, they should be shot
# this is only local, so it's only for say kiosk use, when you
# want to minimize possibility of breakin
AllowRoot=false
# If you want to be paranoid, turn this one off
AllowRemoteRoot=false
# This will allow remote timed login
AllowRemoteAutoLogin=false
# 0 is the most restrictive, 1 allows group write permissions, 2 allows all
# write permissions
RelaxPermissions=0
# Check if directories are owned by logon user.  Set to false, if you have, for
# example, home directories owned by some other user.
CheckDirOwner=true
# Number of seconds to wait after a bad login
#RetryDelay=1
# Maximum size of a file we wish to read.  This makes it hard for a user to DoS
# us by using a large file.
#UserMaxFile=65536
# If true this will basically append -nolisten tcp to every X command line,
# a good default to have (why is this a "negative" setting? because if
# it is false, you could still not allow it by setting command line of
# any particular server).  It's probably better to ship with this on
# since most users will not need this and it's more of a security risk
# then anything else.
# Note: Anytime we find a -query or -indirect on the command line we do
# not add a "-nolisten tcp", as then the query just wouldn't work, so
# this setting only affects truly local sessions.
DisallowTCP=true
# By default never place cookies if we "detect" NFS.  We detect NFS
# by detecting "root-squashing".  It seems bad practice to place
# cookies on things that go over the network by default and thus we
# don't do it by default.  Sometimes you can however use safe remote
# filesystems where this is OK and you may want to have the cookie in your
# home directory.
#NeverPlaceCookiesOnNFS=true

# XDMCP is the protocol that allows remote login.  If you want to log into
# gdm remotely (I'd never turn this on on open network, use ssh for such
# remote usage that).  You can then run X with -query <thishost> to log in,
# or -indirect <thishost> to run a chooser.  Look for the 'Terminal' server
# type at the bottom of this config file.
[xdmcp]
# Distributions: Ship with this off.  It is never a safe thing to leave
# out on the net.  Setting up /etc/hosts.allow and /etc/hosts.deny to only
# allow local access is another alternative but not the safest.
# Firewalling port 177 is the safest if you wish to have xdmcp on.
# Read the manual for more notes on the security of XDMCP.
Enable=false
# Honour indirect queries, we run a chooser for these, and then redirect
# the user to the chosen host.  Otherwise we just log the user in locally.
#HonorIndirect=true
# Maximum pending requests
#MaxPending=4
#MaxPendingIndirect=4
# Maximum open XDMCP sessions at any point in time
#MaxSessions=16
# Maximum wait times
#MaxWait=15
#MaxWaitIndirect=15
# How many times can a person log in from a single host.  Usually better to
# keep low to fend off DoS attacks by running many logins from a single
# host.  This is now set at 2 since if the server crashes then gdm doesn't
# know for some time and wouldn't allow another session.
#DisplaysPerHost=2
# The number of seconds after which a non-responsive session is logged off.
# Better keep this low.
#PingIntervalSeconds=15
# The port.  177 is the standard port so better keep it that way
#Port=177
# Willing script, none is shipped and by default we'll send
# hostname system id.  But if you supply something here, the
# output of this script will be sent as status of this host so that
# the chooser can display it.  You could for example send load,
# or mail details for some user, or some such.
#Willing=/etc/gdm/Xwilling

[gui]
# The specific gtkrc file we use.  It should be the full path to the gtkrc
# that we need.  Unless you need a specific gtkrc that doesn't correspond to
# a specific theme, then just use the GtkTheme key
#GtkRC=/usr/share/themes/Default/gtk-2.0/gtkrc

# The GTK+ theme to use for the gui
GtkTheme=Human
# If to allow changing the GTK+ (widget) theme from the greeter.  Currently
# this only affects the standard greeter as the graphical greeter does
# not yet have this ability
AllowGtkThemeChange=true
# Comma separated list of themes to allow.  These must be the names of the
# themes installed in the standard locations for gtk themes.  You can
# also specify 'all' to allow all installed themes.  These should be just
# the basenames of the themes such as 'Thinice' or 'LowContrast'.
GtkThemesToAllow=Human,HighContrast,HighContrastInverse,LowContrast

# Maximum size of an icon, larger icons are scaled down
#MaxIconWidth=128
#MaxIconHeight=128

[greeter]
# Greeter has a nice title bar that the user can move
#TitleBar=true
# Configuration is available from the system menu of the greeter
ConfigAvailable=false
# Face browser is enabled.  This only works currently for the
# standard greeter as it is not yet enabled in the graphical greeter.
Browser=false
# The default picture in the browser
#DefaultFace=/usr/share/pixmaps/nobody.png
# User ID's less than the MinimalUID value will not be included in the
# face browser or in the gdmselection list for Automatic/Timed login.
# They will not be displayed regardless of the settings for
# Include and Exclude.
MinimalUID=1000
# Users listed in Include will be included in the face browser and in
# the gdmsetup selection list for Automatic/Timed login.  Users
# should be separated by commas.
#Include=
# Users listed in Exclude are excluded from the face browser and from
# the gdmsetup selection list for Automatic/Timed login.  Excluded 
# users will still be able to log in, but will have to type their
# username.  Users should be separated by commas.  
Exclude=bin,daemon,adm,lp,sync,shutdown,halt,mail,news,uucp,operator,nobody,gdm,postgres,pvm,rpm
# By default, an empty include list means display no users.  By setting
# IncludeAll to true, the password file will be scanned and all users 
# will be displayed except users excluded via the Exclude setting and
# user ID's less than MinimalUID.  Scanning the password file can be
# slow on systems with large numbers of users and this feature should 
# not be used in such environments.  The setting of IncludeAll does
# nothing if Include is set to a non-empty value.
IncludeAll=true
# If user or user.png exists in this dir it will be used as his picture
#GlobalFaceDir=/usr/share/pixmaps/faces/
# File which contains the locale we show to the user.  Likely you want to use
# the one shipped with gdm and edit it.  It is not a standard locale.alias file,
# although gdm will be able to read a standard locale.alias file as well.
LocaleFile=/etc/gdm/locale.conf
# Logo shown in the standard greeter
#Logo=/usr/share/pixmaps/gdmDebianLogo.xpm
# The standard greeter should shake if a user entered the wrong username or
# password.  Kind of cool looking
#Quiver=true
# The Actions menu (formerly system menu) is shown in the greeter, this is the
# menu that contains reboot, shutdown, suspend, config and chooser.  None of
# these is available if this is off.  They can be turned off individually
# however
SystemMenu=true
# The Actions in the Actions menu require the root password
SecureSystemMenu=false
# Should the chooser button be shown.  If this is shown, GDM can drop into
# chooser mode which will run the xdmcp chooser locally and allow the user
# to connect to some remote host.  Local XDMCP does not need to be enabled
# however
#ChooserButton=true
# Welcome is for all console logins and RemoteWelcome is for remote logins
# (through XDMCP).
# DefaultWelcome and DefaultRemoteWelcome set the string for Welcome
# to "Welcome" and for DefaultWelcome to "Welcome to %n", and properly
# translate the message to the appropriate language.  Note that %n gets
# translated to the hostname of the machine.  These default values can
# be overridden by setting DefaultWelcome and/or DefaultRemoteWelcome to
# false, and setting the Welcome and DefaultWelcome values as desired.
# Just make sure the strings are in utf-8 Note to distributors, if you
# wish to have a different Welcome string and wish to have this
# translated you can have entries such as "Welcome[cs]=Vitejte na %n".
DefaultWelcome=true
DefaultRemoteWelcome=true
#Welcome=Welcome
#RemoteWelcome=Welcome to %n
# Don't allow user to move the standard greeter window.  Only makes sense
# if TitleBar is on
#LockPosition=false
# Set a position rather then just centering the window.  If you enter
# negative values for the position it is taken as an offset from the
# right or bottom edge.
#SetPosition=false
#PositionX=0
#PositionY=0
# Xinerama screen we use to display the greeter on.  Not for true
# multihead, currently only works for Xinerama.
#XineramaScreen=0
# Background settings for the standard greeter:
# Type can be 0=None, 1=Image, 2=Color
#BackgroundType=2
#BackgroundImage=
#BackgroundScaleToFit=true
BackgroundColor=#523921
# XDMCP session should only get a color, this is the sanest setting since
# you don't want to take up too much bandwidth
#BackgroundRemoteOnlyColor=true
# Program to run to draw the background in the standard greeter.  Perhaps
# something like an xscreensaver hack or some such.
#BackgroundProgram=
# if this is true then the background program is run always, otherwise
# it is only run when the BackgroundType is 0 (None)
#RunBackgroundProgramAlways=false
# Show the Failsafe sessions.  These are much MUCH nicer (focus for xterm for
# example) and more failsafe then those supplied by scripts so distros should
# use this rather then just running an xterm from a script.
#ShowGnomeFailsafeSession=true
#ShowXtermFailsafeSession=true
# Normally there is a session type called 'Last' that is shown which refers to
# the last session the user used.  If off, we will be in 'switchdesk' mode where
# the session saving stuff is disabled in GDM
#ShowLastSession=true
# Always use 24 hour clock no matter what the locale.
#Use24Clock=false
# Use circles in the password field.  Looks kind of cool actually,
# but only works with certain fonts.
UseCirclesInEntry=true
# Do not show any visible feedback in the password field. This is standard
# for instance in console, xdm and ssh.
#UseInvisibleInEntry=false
# These two keys are for the new greeter.  Circles is the standard
# shipped theme.  If you want gdm to select a random theme from a list
# then provide a list that is delimited by /: to the GraphicalThemes key and 
# set GraphicalThemeRand to true.  Otherwise use GraphicalTheme and specify
# just one theme.
GraphicalTheme=tango_gdm
#GraphicalThemes=circles/:happygnome
GraphicalThemes=circles
GraphicalThemeDir=/usr/share/gdm/themes/
GraphicalThemeRand=false
# If InfoMsgFile points to a file, the greeter will display the contents of the
# file in a modal dialog box before the user is allowed to log in.
#InfoMsgFile=
# If InfoMsgFile is present then InfoMsgFont can be used to specify the font
# to be used when displaying the contents of the file.
#InfoMsgFont=Sans 24
# If SoundOnLogin is true, then the greeter will beep when login is ready
# for user input.  If SoundOnLogin is a file and the greeter finds the
# 'play' executable (see daemon/SoundProgram) it will play that file
# instead of just beeping
SoundOnLogin=true
SoundOnLoginFile=/usr/share/sounds/question.wav
# If SoundOnLoginSuccess, then the greeter will play a sound (as above)
# when a user successfully logs in
#SoundOnLoginSuccess=false
#SoundOnLoginSuccessFile=
# If SoundOnLoginFailure, then the greeter will play a sound (as above)
# when a user fails to log in
#SoundOnLoginFailure=false
#SoundOnLoginFailureFile=

# The chooser is what's displayed when a user wants an indirect XDMCP
# session, or selects Run XDMCP chooser from the system menu
[chooser]
# Default image for hosts
#DefaultHostImg=/usr/share/pixmaps/nohost.png
# Directory with host images, they are named by the hosts: host or host.png
HostImageDir=/usr/share/hosts/
# Time we scan for hosts (well only the time we tell the user we are
# scanning actually, we continue to listen even after this has
# expired)
#ScanTime=4
# A comma separated lists of hosts to automatically add (if they answer to
# a query of course).  You can use this to reach hosts that broadcast cannot
# reach.
Hosts=
# Broadcast a query to get all hosts on the current network that answer
Broadcast=true
# Set it to true if you want to send a multicast query to hosts.
Multicast=false
# It is an IPv6 multicast address.It is hardcoded here and will be replaced when
# officially registered xdmcp multicast address of TBD will be available
#Multicast_Addr=ff02::1
# Allow adding random hosts to the list by typing in their names
#AllowAdd=true

[debug]
# This will enable debugging into the syslog, usually not neccessary
# and it creates a LOT of spew of random stuff to the syslog.  However it
# can be useful in determining when something is going very wrong.
Enable=false

[servers]
# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX). 
#1=Xgl 
# These are the standard servers.  You can add as many you want here
# and they will always be started.  Each line must start with a unique
# number and that will be the display number of that server.  Usually just
# the 0 server is used.
0=Standard
#1=Standard
# Note the VTAllocation and FirstVT keys on linux and freebsd.
# Don't add any vt<number> arguments if VTAllocation is on, and set FirstVT to
# be the first vt available that your gettys don't grab (gettys are usually
# dumb and grab even a vt that has already been taken).  Using 7 will work
# pretty much for all linux distributions.  VTAllocation is not currently
# implemented on anything but linux and freebsd.  Feel free to send patches.
# X servers will just not get any extra arguments then.
#
# If you want to run an X terminal you could add an X server such as this
#0=Terminal -query serverhostname
# or for a chooser (optionally serverhostname could be localhost)
#0=Terminal -indirect serverhostname
#
# If you wish to run the XDMCP chooser on the local display use the following
# line
#0=Chooser

## Note:
# is your X server not listening to TCP requests?  Perhaps you should look
# at the security/DisallowTCP setting!

# Definition of the standard X server.
[server-Standard]
name=Standard server
command=/usr/X11R6/bin/X -br -audit 0 
flexible=true

# To use this server type you should add -query host or -indirect host
# to the command line
[server-Terminal]
name=Terminal server
# Add -terminate to make things behave more nicely
command=/usr/X11R6/bin/X -br -audit 0 -terminate
# Make this not appear in the flexible servers (we need extra params
# anyway, and terminate would be bad for xdmcp choosing).  You can
# make a terminal server flexible, but not with an indirect query.
# If you need flexible indirect query server, then you must get rid
# of the -terminate and the only way to kill the flexible server will
# then be by Ctrl-Alt-Backspace
flexible=false
# Not local, we do not handle the logins for this X server
handled=false

# To use this server type you should add -query host or -indirect host
# to the command line
[server-Chooser]
name=Chooser server
command=/usr/X11R6/bin/X -br -audit 0
# Make this not appear in the flexible servers for now, but if you
# wish to allow a chooser server then make this true.  This is the
# only way to make a flexible chooser server that behaves nicely.
flexible=false
# Run the chooser instead of the greeter.  When the user chooses a
# machine they will get this same server but run with
# "-terminate -query hostname"
chooser=true
[server-Xgl] 
name=Xgl server 
command=/usr/X11R6/bin/Xgl :1 -fullscreen -ac -accel glx:fbo -accel xv:fbo
flexible=true
```


Pls help ](*,)[/QUOTE]

Comment out "dri" and "Glcore" and try again...

> 
Originally Posted by Jureiz
Hi all, btw, I'm a newbie to this Ubuntu Breezy and xgl+compiz ( but not really a newbie to Linux =) ).

I followed this instruction, and found it working. I forgot to thank you because I'm really amazed with this whole cool thing . Thanks a lot, man. Btw, there's something awkward. My friends, running a computer with Nvidia GeForce 4 MX, followed the same instructions as I did, but ended up with blank screen. Hmm, I don't know what's wrong with his computer. But, with the same computer, he couldn't install Ubuntu Drapper Drake, ended up with resolution problems. So, probably the problem is his graphic card. Wonder if there's a solution for that.

Anyway, thanks man. I'm getting to love this ubuntu more nowadays ... 

I have the same problem on gnome (2 pages ago) but now i've installed kubuntu dapper drake and it works GREAT (except the common bugs of course :P)!

---

### Post by Masterillusionist on 2006-04-18
hi i've followed your guide but when i run thefuture i get:
```
glenn@ubuntu:~$ thefuture
glenn@ubuntu:~$ compiz: Couldn't load plugin 'libmenu.so'

```

but the windows work like they should and i've found the cube :D but how do i zoom out and how can i make the cube stay on a border?

thanks in advance

---

### Post by joshuafr on 2006-04-18
Hi all,
I'm under Kubuntu Breezy with a NVidia Geforce2MX card, I followed all instructions, but at the end I have :
compiz: Couldn't bind redirected window 0x160000a to texture
compiz: pixmap 0x2000fb can't be bound to texture
compiz: Couldn't bind redirected window 0x140000b to texture
compiz: pixmap 0x2000f9 can't be bound to texture
...
giving under KDEa black screen. "ALT-Tab" show a centred rectangle slicing, the screen comes white, and it's all :-(
Recompiling glitz do nothing, and I can't recompile compiz. 
Does someone can help me, please?

---

### Post by dnanar on 2006-04-18
Hi,

I try to install Xgl and Compiz on my Ubuntu Breezy with NVIDIA Geforce 4MX by following this tutorial.

Xgl work fine, but Compiz doesn't work. When i try to launch the "thefuture" script, the screen becomes black, i only see my mouse. When I try to click on a "hidden menu", i just see quickly the background window of the menu (a "white rectangle").
I think that i have the same problem as vbmaster and joshuafr.

I see a strange thing: i have DRI when i set /etc/gdm/gdm.conf to "0=Standart". When I set it to "0=Xgl", glxinfo say that i have no DRI.

My xorg.conf file:

```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
#	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
	Option		"XkbVariant"	"latin9"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option 		"RenderAccel" 		"true"
	Option 		"AllowGLXWithComposite" "true"
EndSection

Section "Monitor"
	Identifier	"IBM C50"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Monitor		"IBM C50"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
          Option  "Composite" "Enable"
EndSection

```


Thanks.



(sorry for my bad english, i' m french).

---

### Post by Milamber_Cubed on 2006-04-19
[QUOTE=Masterillusionist]hi i've followed your guide but when i run thefuture i get:
```
glenn@ubuntu:~$ thefuture
glenn@ubuntu:~$ compiz: Couldn't load plugin 'libmenu.so'

```

but the windows work like they should and i've found the cube :D but how do i zoom out and how can i make the cube stay on a border?

thanks in advance[/QUOTE]

You can ignore the libmenu error... it's not required for the version of compiz i link to.

As for shortcuts etc, have a look here

[http://en.opensuse.org/Compiz#Default_plugin_keyboard_shortcuts](http://en.opensuse.org/Compiz#Default_plugin_keyboard_shortcuts)

---

### Post by Milamber_Cubed on 2006-04-19
[QUOTE=joshuafr]Hi all,
I'm under Kubuntu Breezy with a NVidia Geforce2MX card, I followed all instructions, but at the end I have :
compiz: Couldn't bind redirected window 0x160000a to texture
compiz: pixmap 0x2000fb can't be bound to texture
compiz: Couldn't bind redirected window 0x140000b to texture
compiz: pixmap 0x2000f9 can't be bound to texture
...
giving under KDEa black screen. "ALT-Tab" show a centred rectangle slicing, the screen comes white, and it's all :-(
Recompiling glitz do nothing, and I can't recompile compiz. 
Does someone can help me, please?[/QUOTE]

Not really sure about this... the guide is intended for use with gnome so I am not even sure if it will work at all with kde.

---

### Post by Milamber_Cubed on 2006-04-19
[QUOTE=dnanar]Hi,

I try to install Xgl and Compiz on my Ubuntu Breezy with NVIDIA Geforce 4MX by following this tutorial.

Xgl work fine, but Compiz doesn't work. When i try to launch the "thefuture" script, the screen becomes black, i only see my mouse. When I try to click on a "hidden menu", i just see quickly the background window of the menu (a "white rectangle").
I think that i have the same problem as vbmaster and joshuafr.
[/QUOTE]

I had a similar issue.

After running "thefuture" i got a completelyblack screen this was fixed by pressing ctrl+alt+left to switch desktops and forcing a redraw of the whole screen. Give it a go ;)

---

### Post by joshuafr on 2006-04-19
Milamber_Cubed < Hi, I run KDE with gnome-window-decorator and gconf, like see in several tutorials. It's not a K problem but a compiz problem, I think. On a Gentoo forum, I saw that compiz must be linked with GLX and not mesa for avoiding this problem, but I don't know how to do that.
Thanks for your help!

---

### Post by ickyb0d on 2006-04-19
Hey guys, first off, big thanks for all these tutorials out here... if anything, there may be too many :D 

I've just started with ubuntu about a week ago (although i'm no stranger to *nix systems).  At first i upgraded to dapper, used XGL, but i wanted to try breezy as it is more stable and has more stuff readily available for it.  I've recently installed XGL and have *most* everything working.  I had a question about the transparency stuff...

[QUOTE=Milamber_Cubed]You need to load the opacity module as discussed in other threads. The version of compiz in the RPMs I used didn't include it.[/QUOTE]

[QUOTE=23meg]You can also use transset or transset-df to set opacity.[/QUOTE]


when in dapper i did have the transparency working with alt+scroll wheel; obviously this isn't the case in breezy.  Since it's not in the rpms, how do you go about installing this? is it as easy as...  

```

sudo apt-get install transset

```

i'm pretty sure i tried that and it couldn't find it.  i have universe and multiverse repos enabled.
also, once this is installed, how does one go about adding this to the compiz plugins?  any help on this would be great, and thanks for everything thus far.



EDIT:

hrm, i found [this]("http://moosy.blogspot.com/2006/03/drred-xgl-tweaks-part-2.html"), but i guess how would you bind it into your mouse wheel and incorporate into compiz...

---

### Post by dnanar on 2006-04-19
Hi,

I have solved my problem by using this simple command:

[QUOTE=http://infojulien.canalblog.com/archives/2006/03/01/1446696.html]

sudo ln -sf /usr/bin/Xorg /etc/X11/X
[/QUOTE]

Thanks for the tutorial :)

---

### Post by simonki on 2006-04-20
Has anyone managed to fix the 'black screen' on running /usr/bin/thefuture? When I start gdm with 0=Standard and run glxinfo it says DRI is enabled. When I start gdm with 0=Xgl and run glxinfo, DRI is disabled. Xgl works, but runs really slowly.
Hope somebody can help!

Thanks,
Simon

---

### Post by ickyb0d on 2006-04-20
i haven't found this on these forums yet... so here's what i've done to get transparency working in breezy (seemingly?) like i had it working in dapper.


first you need the following...

*transset
*transset-df
*xbindkeys

i've attached transset-df.  it's i386... if you need somethin else, it's probably out there.

install with
```

sudo dpkg -i transset-df_4-1_i386.deb

```

as with any other deb... -r to remove it...

the rest were in the repos, so just apt-get them.  once they're all done and installed.  edit your ~/.xbindkeysrc.  mine looks like this.

```

#increase opacity (less transparent)
"transset-df -p --inc 0.1"
    alt + b:4   (mouse)

#decrease opacity (more transparent)... setting a minimum to 0.2 opacity... don't wanna lose it!
"transset-df -p --min 0.2 --dec 0.1"
    alt + b:5   (mouse)

```


button 4 is scrollwheel up, button 5 is scrollwheel down.  now... this took some lil' workarounds for a few things...


1) i initially used xbindkeys-conf, a gui to edit my ~/.xbindkeysrc (which only appeared when i had compiz running).  this added some weird stuff to my file like *(#& b:4 (mouse)... so i had to clean that up

2) xbindkeys runs as a daemon.  so you should only have 1 running at a time.  i also made a point to POINT it to the file.  so when you run it run...

```

xbindkeys -f ~/.xbindkeysrc

```

otherwise it looks for some file in like /tmp or something.

anyways, this doesn't require a restart.  so hover over a window... hold down alt (you can change that if you want) and scroll up down...  voila! works right?  if not... make sure you have your compiz running... as i believe this only works under compiz.

---

### Post by Straker on 2006-04-22
Okay - after several tries I cannot get it to work.

I have an on-board GeForce 6100 - mobo: Epox 9GF6100-M.  I have the latest Nvidia drivers and its working fine.

I have a Athlon 64 X2 4400+, but I am using the 32-bit kernel 2.6.12-10-k7-smp to access both cores.  Hence, my Breezy is 32-bit.

Does XGL/Compiz not work with this kernel?  this CPU?  this on-board video?  Anybody with similar specs that has gotten it to work with Breezy?  I am hesitant to upgrade to Dapper because I rely too much on Crossover/Wine.

Thanks for any help.

---

### Post by christhemonkey on 2006-04-23
I finally have sweet sweet compiz working!
Love that cube!!!!


BUT;
my problems.

-I cant load the gconf pluginy thing and have the cube rotate working.
Which is annoying because id love to have my own picture on top of the cube and also to be inside the cube....

-It always says error loading libmenu.so which is a problem i had at one point, and then got rid of, but cant remember how.

-The latest nvidia driver STILL does not support direct rendering with Xgl and my card (FX5500).


Apart from that it works great!

Cheers so much!

---

### Post by kuziat on 2006-04-27
My problem is here:

#sudo apt-get install libxfont1 gconf-editor libwnck18 libglitz1 libxcomposite1
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
gconf-editor ya está en su versión más reciente.
libglitz1 ya está en su versión más reciente.
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
  libwnck18: Depende: libcairo2 (>= 1.0.2-2) pero 1.0.2-0ubuntu1.1 va a ser instalado
             Depende: libglib2.0-0 (>= 2.10.0) pero 2.8.3-0ubuntu1 va a ser instalado
             Depende: libpango1.0-0 (>= 1.12.1) pero 1.10.1-0ubuntu1 va a ser instalado
  libxcomposite1: Depende: x11-common (>= 7.0.0-0ubuntu3) pero no es instalable
E: Paquetes rotos

Can u help me?

---

### Post by WillFerrellLuva on 2006-04-27
Hi,

Im trying to set this up according but i cant seem to be able to download compiz-libs.tar.gz

does anybody no where I can get it?  when I "wget http://www.hep.man.ac.uk/u/shiv/ubuntu/compiz-libs.tar.gz" it keeps telling me that the connection is refused.

---

### Post by WillFerrellLuva on 2006-04-27
nevermind.....Im a moron.....I found it

---

### Post by riskbreaker927 on 2006-04-28
Well... what did you do? I'm getting the same error.

---

### Post by christhemonkey on 2006-04-28
Just to say, got the gconf thing working,
All that needed was for cube and rotate to be added to the active plugins in gconf (apps>gconf>allscreens>, something like that)

Now my problem is,
no matter what i do, cant figure out how to change to a pretty picture in the far background.
Any ideas?

---

### Post by christhemonkey on 2006-04-30
Ok, my ongoing saga,

Realised you need to activate the skydome plugin, which i did,

and then realised that the version of compiz i am using isnt compiled against libsvg or whatever it needs for skydome to work
so am going to try compiling from source.

---

### Post by CHNdonny on 2006-05-01
[QUOTE=danielcs]Try this.
ALT+F2, type **gksudo gedit** and put your password.
In gedit, click open and find the file **/etc/X11/xorg.conf**
Now scroll down to the end of the file and add this:
```
Section "Extensions"
	Option	"Composite"	"Enable"
EndSection
```

Save the file, logout and then login again.
If it doesn't work try rebooting the computer.[/QUOTE]
if add Section "Extensions"
	Option	"Composite"	"Enable"
EndSection ,maybe the drivers can't identify the displaycard  idon't know whether that will happen or not under nvidia . but under ati that goes wrong.

---

### Post by openback on 2006-05-04
Oh my god, thanks so much for this tutorial! It worked on the first try and it's great! I only have one question, I used to use nvidia-settings to adjust my gamma, as my monitor is horribly dark, but now I can't. What can I use to adjust  the gamma on startup?

---

### Post by Milamber_Cubed on 2006-05-05
[QUOTE=openback]Oh my god, thanks so much for this tutorial! It worked on the first try and it's great! I only have one question, I used to use nvidia-settings to adjust my gamma, as my monitor is horribly dark, but now I can't. What can I use to adjust  the gamma on startup?[/QUOTE]

Sadly, the answer to this is - I don't know! I am now using dapper and have switched to AIGLX to boot. Add to that the fact that I don't have an Nvidia card and I think you are beginning to see that I am probably not the best person to help you now! Maybe someone else has some ideas about your gamma issues??


Glad the guide helped you get up and running though :) Wobbly bits for everyone!!!

---

### Post by CHNdonny on 2006-05-05
i have tried,but when i execute  wget [http://www.hep.man.ac.uk/u/shiv/ubuntu/xgl-cvs_060214-2.i586.rpm](http://www.hep.man.ac.uk/u/shiv/ubuntu/xgl-cvs_060214-2.i586.rpm)  ,it couldn't be download it marks  403 Forbidden
what shall i do ,thank you

---

### Post by Milamber_Cubed on 2006-05-07
[QUOTE=CHNdonny]i have tried,but when i execute  wget [http://www.hep.man.ac.uk/u/shiv/ubuntu/xgl-cvs_060214-2.i586.rpm](http://www.hep.man.ac.uk/u/shiv/ubuntu/xgl-cvs_060214-2.i586.rpm)  ,it couldn't be download it marks  403 Forbidden
what shall i do ,thank you[/QUOTE]

I can only guess that the web server was down when you tried... should be working now.

---

### Post by got_nix on 2006-05-07
it worked flawlessly on my dell inspiron 6000 however its so slow :( that i see my self about to go comment out the xgl and uncoment the 0=standard line of my xorg.conf file any minute, and wobbly windows are so cool and i cant enjoy it :(

---

### Post by brunobruno on 2006-05-10
Nope i tried it 2, it didn't work :( . I get x server error, had to reedit gdm.conf file to fix the problem

---

### Post by nikolaos on 2006-05-20
i did everything in the guide, and in the one for nVidia cards. Thr error i ceep getting is this.

```

FATAL SERVER ERROR
no visual format found
Synaptics Deviceoff called
```

this happens when i sudo gdm ===>to start Gnome

---

### Post by themmm on 2006-05-26
Nice Guide!

It worked for me on ubuntu 6.06 with I810 onboard graphicscard in my notebook :D

---

### Post by patrick295767 on 2006-07-03
*With some delay with Xgl :-)*:
  
I got such error msg : 
```
# gnome-window-decorator
-l: gnome-window-decorator: command not found
```

gnome-window-decorator is not in the repos . 
(apt-cache search gnome-window   -> nthg ) 

what should be done to fix it ?

 
I have fvwm desktop only.
Should I install gnome then ?
  
I read that fvwm and xgl is not ready yet :-(
but:
> I have both running with no problem.

I setup FVWM to start with the fvwm-crystal in GDM menu.
I then setup XGL to work with GDM as described in the XGL Wiki Howto.
Because compiz is started from Gnome session mgr. after login,
it does not effect my FVWM.

So with one account I login to FVWM and I use another account to
login to XGL.

I haven't had any problems with either one. I have noticed
however that with out XGL/Compiz I was getting 789 fps on
GLX gears using an Nvidia Geforce 2 MX/MX400 32mg. With
XGL/Compiz installed I get 1260 fps.

By the way In FVWM I am using a modified version of PEM'S config.
screenshots here > [http://www.lynucs.org/?&Jupiter](http://www.lynucs.org/?&Jupiter)

---

### Post by slimdog360 on 2006-08-15
It killed gdm file. Im glad for the backup

---

### Post by profediego on 2006-08-16
i follow your steps but when trying to run thefuture i get this error:

/usr/bin/thefuture: line 2: gnome-window-decorator: orden no encontrada
profediego@Gestor-Informatica:~$ compiz.real: Couldn't load plugin 'libgconf.so'compiz.real: Couldn't load plugin 'libmenu.so'

could somebody help me fix this please. Thank You](*,)

---

### Post by klanman8908 on 2006-08-29
> **kuziat said:**
> My problem is here:

#sudo apt-get install libxfont1 gconf-editor libwnck18 libglitz1 libxcomposite1
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
gconf-editor ya está en su versión más reciente.
libglitz1 ya está en su versión más reciente.
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
  libwnck18: Depende: libcairo2 (>= 1.0.2-2) pero 1.0.2-0ubuntu1.1 va a ser instalado
             Depende: libglib2.0-0 (>= 2.10.0) pero 2.8.3-0ubuntu1 va a ser instalado
             Depende: libpango1.0-0 (>= 1.12.1) pero 1.10.1-0ubuntu1 va a ser instalado
  libxcomposite1: Depende: x11-common (>= 7.0.0-0ubuntu3) pero no es instalable
E: Paquetes rotos

Can u help me?

I have the same problem it can't get those files,  My guess is respositories or what ever the heck they are are wrong.  I am new to linux but would very much like to get this working.  If someone could post the respositories they are using the file that you put them in that would be great.

---

