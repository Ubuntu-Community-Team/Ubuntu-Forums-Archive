---
title: "Comp Freezes when startin Celestia"
date: 2006-08-21
forum: Desktop Environments
---

### Post by buddy_krish on 2006-08-21
Previously I posted a problem about Computer freezing after ~30 min....

Now, my computer freezes when I start celestia or billiards or any other High end games....

I'm sure this could be the problem with my Video Drivers....But i dunno how to solve it...I think this is the reason for my previous problem too....

m new to Linux....previously used Shitty Windows.....

Anyone....Please guide me......

---

### Post by encompass on 2006-08-21
It is important to get your hardware inforamtion... what kind of computer and graphics card that you have...
sounds like an ati right?

---

### Post by buddy_krish on 2006-08-21
Im on AMD 3000+, Gigabyte mother board....

n Via RAID card....  :-(

---

### Post by encompass on 2006-08-21
I am sorry?
Don't quite understand the computer things there.
Was that an Nvidia Graphics card?

---

### Post by buddy_krish on 2006-08-22
Well...Im not a computer geek...Just learning.....


Here is what my xorg.conf copy......

May be this would help.........  :-)


==========================Code Start===================

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
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
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
	Driver		"via"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
	Monitor		"SyncMaster"
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
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


==================================End of Code=====================

---

### Post by encompass on 2006-08-22
You won't get much for 3d support for now... but try this...
sudo dpkg-reconfigure xserver-xorg
let everything be a default by pressing enter... except for the graphics driver.
Select the vesa driver.
Then select defaults for the resto fo it... and then reboot.
Did it help at all?  are you getting crashes?

---

### Post by buddy_krish on 2006-08-22
Did select VESA.....and rebooted the system......

I had trouble logging into my user account...it never crossed the login screen...The login screen came again and again...... :-(

I was able to login to ROOT account.....and thats where I am now....

Did not test the Celestia or any other softwares yet...Will let u know the results again... 

Now, How shud I go about logging into my USER account again. :-(

---

### Post by buddy_krish on 2006-08-22
Chkd with Celestia just now........

Worked fine......Just fine.....

But taking up 100% CPU....Is that a problem????

---

### Post by encompass on 2006-08-22
The reason it is taking so much speed is because your CPU has to do the 3d work now... not your special 3d card.
Sounds like a driver issue.
and you have a root acount?  is this account called root...
if so your not supposed to have one.  That would be weird.
I can't remember the command... but I am trying to probe for your graphics card.  LEt me get back to you.

---

### Post by encompass on 2006-08-22
ok... try this command...
```
lspci
```
look for some line that starts with VGA
or...
```
lspci | grep VGA
```

---

### Post by kwalo on 2006-08-22
I'm using S3 Savage PRO DDR graphic card. It sometimes freezes, when I use programs, that make heavy use of OpenGL. It also broke my system, when I tried to install xorg-aiglx, using [this]("http://www.ubuntuforums.org/showthread.php?t=145068") HOWTO. Maybe the next release of xorg will support these cards better.

---

### Post by buddy_krish on 2006-08-23
The account name is ROOT....

===================================

root@vampiro:~# lspci |grep VGA
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)

===================================

What do I do now???

---

### Post by encompass on 2006-08-23
wow, do you remember ever creating a root account?  Cause you shouldn't be able to use it... none the less lets try making a new user and see if that works to login with... if so... then we know it is somehting inside your account that is making it kick back out.
type this at a terminal..
```
adduser testing
```
fill in the password and other what not it may ask for... don't worry it is temporary... just make sure you remember the password.
now log back out to the gdm login screen and try the account.  did it work?
if not reboot and try it then.  Now?
thanks for trying it.
I love these!:---) :-({|= :redface: :tongue: :rolleyes: :confused: :KS

---

### Post by encompass on 2006-08-23
> **kwalo said:**
> I'm using S3 Savage PRO DDR graphic card. It sometimes freezes, when I use programs, that make heavy use of OpenGL. It also broke my system, when I tried to install xorg-aiglx, using [this]("http://www.ubuntuforums.org/showthread.php?t=145068") HOWTO. Maybe the next release of xorg will support these cards better.

do what I told buddy.. the xserver-xorg one. (reconfigure your xorg to use vesa) At least for now.

---

### Post by buddy_krish on 2006-08-23
I was able to create the account and get into it without any problem.....Infact I can get into any other users account but not my own account..... :-(

I changed the driver preference to VESA from my user account....Could this have caused the problem by any chance????

I did not create anyy ROOT account....It was already there....I first created my USER account and then some how I managed to change the pwd of the ROOT account on the system....Thats how I managed to get the ROOT account....

---

### Post by encompass on 2006-08-23
ok that explains it... you have activated the account
no big deal... jsut change the password for that account to something very difficult to guess or you could get hacked with it.
Sounds like your account has some error in it... happens when people try to go to far on costumizing there acount, they kinda get trigger happy cause they never could do that with windows.
Here is what we can do... 
Option 1.
We can create a new account with your root account that will be your new one and copy all the data from your old account over to your new one.
Option 2.
We can try to delete the file that is giving you problems... but without much of an error I think we will have to guess at the common ones.  I wish Gnome had a nice we to rebuild the accounts so that they are up and working again.
That or make a fail safe way to stop problems from happening to the log in sequence... I know windows doesn't have it... it would be cool to see gnome come up with it.
What you may want to do is talk to me personally and I can come in and try to find the file(s) cause the problem.  You can see me do it... called VNC.
PM me if you want me to help you out in that way.

---

### Post by buddy_krish on 2006-08-25
Looks like the problem is solvd for now....

I could login to my user account from the Root account and i manipulated something.....Next time I logged in...I cud login to my user account as well..... :) 

Next time I have ne problem, I will certainly contact U so that U can login to my system....

Thanks for all the help.....

---

