---
title: "emerald help!!"
date: 2008-12-05
forum: General Help
---

### Post by sPiN1 on 2008-12-05
i've looked around on forums and can't figure out why my emerald won't load themes... when i type emerald --replace i get this error message

jason@jason:~$ emerald --replace

(emerald:16086): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

i'd love to get this laza theme working it looks quite nice.

---

### Post by sPiN1 on 2008-12-05
Bump

---

### Post by sPiN1 on 2008-12-05
:)

---

### Post by sPiN1 on 2008-12-05
can anyone help? this is really annoying!

---

### Post by sPiN1 on 2008-12-05
there are so many good emerald themes i would love to try out! i've been googleing this problem for a couple days now with no answers! :(

---

### Post by oldos2er on 2008-12-05
How did you install Emerald? Do you have a menu entry in System, Preferences, Emerald Theme Manager?

---

### Post by sPiN1 on 2008-12-05
> **oldos2er said:**
> How did you install Emerald? Do you have a menu entry in System, Preferences, Emerald Theme Manager?

i installed it with sudo apt-get, and yeah it's in preferences

---

### Post by sPiN1 on 2008-12-05
any other ideas?

---

### Post by mdurham on 2008-12-05
re-install Emerald

---

### Post by oldos2er on 2008-12-05
> **sPiN1 said:**
> any other ideas?

 What happens when you open Emerald and choose a theme? If it's working properly, you should see the theme change immediately. Are you running compiz-fusion as your window manager?

---

### Post by sPiN1 on 2008-12-06
> **oldos2er said:**
> What happens when you open Emerald and choose a theme? If it's working properly, you should see the theme change immediately. Are you running compiz-fusion as your window manager?
i dunno ;x

---

### Post by tjwoosta on 2008-12-06
first go to system-preferences-appearance and click the visual effects tab then put a check in the box that says extra (or custom if there is a custom box)


if you have already done this then the problem is probably that you are running the emerald --replace command from the terminal


you need to run the command from the run dialogue not the terminal

press alt-f2  to open the run dialogue and type this in the box that pops up
```
emerald --replace
```

---

### Post by sPiN1 on 2008-12-06
> **tjwoosta said:**
> first go to system-preferences-appearance and click the visual effects tab then put a check in the box that says extra (or custom if there is a custom box)


if you have already done this then the problem is probably that you are running the emerald --replace command from the terminal


you need to run the command from the run dialogue not the terminal

press alt-f2  to open the run dialogue and type this in the box that pops up
```
emerald --replace
```

when i did this it says the composite extension isn't available or something

---

### Post by eternalnewbee on 2008-12-06
Press ALT-F2, and enter ```
compiz --replace
```
If that doesn't work, then you can't run emerald.

---

### Post by tjwoosta on 2008-12-06
> when i did this it says the composite extension isn't available or something 

it sounds to me like your graphics card doesn't support compiz, if thats the case you will not be able to use the emerald themer


you can still install gtk themes


EDIT: please dont PM me, i always check all of the threads that i post in

---

### Post by sPiN1 on 2008-12-06
> **tjwoosta said:**
> it sounds to me like your graphics card doesn't support compiz, if thats the case you will not be able to use the emerald themer


you can still install gtk themes


EDIT: please dont PM me, i always check all of the threads that i post in

i have used emerald before, ~ a year ago so i know my graphics card does support it

---

### Post by russofris on 2008-12-06
After installing compizconfig-settings-manager, you'll see an app in "System Tools" called the "Compiz config icon".  Right click the manager's icon in the systray and select emerald to handle windows decorations.

Frank

---

### Post by sPiN1 on 2008-12-06
> **russofris said:**
> After installing compizconfig-settings-manager, you'll see an app in "System Tools" called the "Compiz config icon".  Right click the manager's icon in the systray and select emerald to handle windows decorations.

Frank

i don't seem to have that, perhaps i never installed compiz? is there an easy way of installation?

---

### Post by tjwoosta on 2008-12-06
> i don't seem to have that, perhaps i never installed compiz? is there an easy way of installation?

compiz comes installed on ubuntu by defualt

> After installing compizconfig-settings-manager, you'll see an app in "System Tools" called the "Compiz config icon". Right click the manager's icon in the systray and select emerald to handle windows decorations.


i think you are referring to compiz-fusion-icon, in which case you would need to install that seperatly

i do agree that he should install both compizconfig-settings-manager and compiz-fusion-icon

to do that you can just go to applications-add/remove  then set it to search for "all available application" then search for each of them and install

also could you please post the output of

```
lspci
```

also please post your /etc/xorg.conf

```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by sPiN1 on 2008-12-06
jason@jason:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV380 [Radeon X600 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV380 [Radeon X600]
03:03.0 Communication controller: Conexant HSF 56k Data/Fax Modem
03:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)


AND


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
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection

---

### Post by tjwoosta on 2008-12-06
strange...

it all looks normal to me

you have ati RV380 graphics card and the driver seems to be setup correctly

---

### Post by sPiN1 on 2008-12-06
ok now being the idiot i am i changed composite "0" to 1 and now my screen is way messed up and it seems it won't let me change it back :X

---

### Post by eternalnewbee on 2008-12-06
To install Compiz Fusion icon, go to Add/Remove, and compiz icon in the searchbar.

---

### Post by sPiN1 on 2008-12-06
i did this: Change:
Option "Composite" "0"
to:
Option "Composite" "1"

Save changes and exit editor.

From command line:
sudo apt-get install xserver-xgl

Restart X-server (Ctrl+Alt+Backspace -- I assume this works although I actually rebooted)


 and now my screen is messed up, i changed it back to 0 so i'm guessing it's the xserver?

---

### Post by tjwoosta on 2008-12-06
change it back, then save it and reboot

> sudo apt-get install xserver-xgl

i dont think you need xgl to use emerald

---

### Post by eternalnewbee on 2008-12-06
> i dont think you need xgl to use emerald
That's correct.

---

### Post by sPiN1 on 2008-12-06
ok i fixed it, but i was able to use visual effects with no composite extension error

---

### Post by sPiN1 on 2008-12-06
> **eternalnewbee said:**
> To install Compiz Fusion icon, go to Add/Remove, and compiz icon in the searchbar.

this found no matches

---

### Post by tjwoosta on 2008-12-06
> this found no matches

try searching synaptic instead

system-administration-synaptic package manager

> ok i fixed it, but i was able to use visual effects with no composite extension error

so it is working now or its not?

---

### Post by sPiN1 on 2008-12-06
> **tjwoosta said:**
> try searching synaptic instead

system-administration-synaptic package manager



so it is working now or its not?

when i switched back, i got the error again.

---

### Post by tjwoosta on 2008-12-06
what version of ubuntu are you using?

if unsure post the output of this command
```
uname -a
```

---

### Post by sPiN1 on 2008-12-06
i don't think my compiz is running

---

### Post by sPiN1 on 2008-12-06
jason@jason:~$ uname -a
Linux jason 2.6.24-22-generic #1 SMP Mon Nov 24 18:32:42 UTC 2008 i686 GNU/Linux
jason@jason:~$

---

### Post by tjwoosta on 2008-12-06
> i don't think my compiz is running

not yet..

thats what enabling the visual effects is supposed to do is turn on compiz

---

### Post by tjwoosta on 2008-12-06
well i dont know buddy...

i wish i could help more but im at a loss here

i mean it looks like your graphics are all set, i just dont understand why you get the error when trying to enable compiz

hopefully someone else can help sort this out

---

### Post by eternalnewbee on 2008-12-06
> i don't think my compiz is running
Go to Synaptic Package Manager, and enter compiz in the searchbar. Do you see compiz there? If so, is it installed or not?

---

### Post by sPiN1 on 2008-12-06
> **eternalnewbee said:**
> Go to Synaptic Package Manager, and enter compiz in the searchbar. Do you see compiz there? If so, is it installed or not?

it's running but yeah i dunno why i get the composite extension error anyone else have any ideas?

---

### Post by eternalnewbee on 2008-12-07
Have you tried ```
compiz --replace
```

---

### Post by sPiN1 on 2008-12-07
> **eternalnewbee said:**
> Have you tried ```
compiz --replace
```

yes, yes i have

---

### Post by sPiN1 on 2008-12-07
anyone else have any ideas?

---

### Post by sPiN1 on 2008-12-07
:)

---

### Post by sPiN1 on 2008-12-07
;)

---

### Post by cobra741 on 2008-12-07
Time for a rip and replace me thinks :) 

Note: This will install Compiz version 0.7.9 of compiz on your machine. whilst it's not the latest "stable" version it does work a treat, haven't had a single issue since i installed it about a month ago (and I've spent a stupid amount of time tinkering with it and haven't managed to break it yet :) )

jump into a terminal window and create a folder in your home drive.. lets say "compiz" (mkdir compiz)
go into the directory (cd compiz) 

enter this into your terminal window (without the quotes) "git clone git://anongit.compiz-fusion.org/users/omega/scripts"

this will download a compiz git script into your compiz directory. 
jump into the scripts folder and run the script "sudo ./git-compiz"

This will to a total reinstall of compiz and emerald on to your PC (along with pretty much all of the plugins) 

give your machine a reboot just for safety's sake and give it a shot :) 

Good luck!

---

### Post by sPiN1 on 2008-12-08
jason@jason:~/scripts$ sudo ./git-compiz

>>> G I T - C O M P I Z <<<
_____________________________________________________

 * Writing log file to /tmp/git-compiz-17069.log
_____________________________________________________

 * Checking minimal dependencies...........OK
_____________________________________________________

 * Checking internet connection...........OK
_____________________________________________________

 * Updating git-compiz script
 -> No update!
_____________________________________________________

>> compiz <<

 * Cloning compiz
 * Cleaning old compile
 * Configuring new version
 -> compiz's autogen.sh reports errors. Bailing.
_____________________________________________________

Failed to build compiz. No reason to continue.
jason@jason:~/scripts$

---

### Post by sPiN1 on 2008-12-08
;)

---

### Post by cobra741 on 2008-12-08
hhmmm buggah :(

looks like something's corrupt with your somethin' :) 

might be worth totally removing compiz and emerald from Synaptic and trying the script again. 

Other than that it might be worth asking around on the compiz-fusion forums

Hope you get it sorted mate :)


Edit: Acutally... it might be worth trying the script without the sudo. as compiz puts quite a lot into your home folder there's a chance it's getting confused. probably not but worth a try none the less!

---

### Post by russofris on 2008-12-09
Did you install the compiz fusion icon as instructed on page 2?


sudo apt-get install compizconfig-settings-manager

Frank

---

### Post by sPiN1 on 2008-12-10
> **russofris said:**
> Did you install the compiz fusion icon as instructed on page 2?


sudo apt-get install compizconfig-settings-manager

Frank

yeah 

jason@jason:~$ sudo apt-get install compizconfig-settings-manager
[sudo] password for jason: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compizconfig-settings-manager is already the newest version.
The following packages were automatically installed and are no longer required:
  libglitz-glx1 libglitz1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jason@jason:~$

---

### Post by sPiN1 on 2008-12-10
the problem is my compiz is not running, and can't run

---

### Post by sPiN1 on 2008-12-10
;)

---

### Post by sPiN1 on 2008-12-11
;)

---

### Post by sPiN1 on 2008-12-12
:)

---

### Post by rswoody2000 on 2008-12-12
I know you are looking for a solution but constanty adding a reply wont get you there any quicker. People would lose interest if thats what your doing. Doing that does increase your thread post count but thats not the way your supposed to go about it.

However i will look around on other threads if there is an asnwer to this problem your having as i have never come accross this pickle

---

