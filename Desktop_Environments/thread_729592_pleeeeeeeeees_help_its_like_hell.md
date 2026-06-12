---
title: "pleeeeeeeeees help its like hell"
date: 2008-03-20
forum: Desktop Environments
---

### Post by lookforlohith on 2008-03-20
my info is

lohi@lohi:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:01.0 Modem: Motorola Unknown device 3052 (rev 04)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 01)




lohi@lohi:~$ glxinfo
name of display: :0.0
X Error of failed request: BadAlloc (insufficient resources for operation)
Major opcode of failed request: 142 (GLX)
Minor opcode of failed request: 3 (X_GLXCreateContext)
Serial number of failed request: 16
Current serial number in output stream: 17


if i click restricted drivers its showing . no restricted drivers required

i installed ubuntu 7.04

ill update it later no problem

i installed beryl(though its dead project It may not slowdown my comp .cos i have 512mbram , no additional graphics card

a.nothing is working ,not even 3d cube desktop
b.videos playing doesnt have clarity


i love learning to correct my problem please as soon as possible brothers/sisters hellllllp me!!!!!!

---

### Post by amaroKer on 2008-03-20
I'm not sure exactly what you're asking.  

a.if nothing is working, 3D effects should be pretty low on the list, I think.  Maybe let us know some more specific problems.
b.what videos are not clear?  What are you playing them in?  What is the format?  Youtube doesn't have much clarity, but a ripped 350MB TV episode should.

Remember that we only know as much about your situation as you tell us.  Be specific.

---

### Post by lookforlohith on 2008-03-20
actually
i think i dont have sufficient drivers on my comp.........
and i dont know to install them as im new to linux.........
im playing in vlc player . normal .dat videos , it is like . small boxes appearing... in full picture...
see .. it happens when we first install xp. without drivers , videos exactly play like this....

and y my cube is not working and also glxinfo showing bad allocation problem as above

pleees brother see this

---

### Post by amaroKer on 2008-03-20
funny, i have never heard of .dat movie files.

what drivers do you think you don't have?
what driver do you install in XP so that you don't get the boxes?
what version of compiz are you running right now?

---

### Post by zxscooby on 2008-03-20
I would try removing beryl for now 
i think that error 
X Error of failed request: BadAlloc (insufficient resources for operation)
means you are low on memory
or a driver limitation

---

### Post by lookforlohith on 2008-03-20
sory its not dat . its  mpg

---

### Post by lookforlohith on 2008-03-20
i installer directx on windos to overcome video problem

and looking at my above information of glxinfo and others u suggest me which drivers should i install ....... please tell me a solution 


i dont thing i have some problem because of  beryl . before installing that also .. i had video problem....... but y beryl is not working?????????????

pleees see my comp information in first post

---

### Post by zxscooby on 2008-03-20
maby you are looking for aiglx?

look here
[http://ubuntuforums.org/archive/index.php/t-356722.html](http://ubuntuforums.org/archive/index.php/t-356722.html)

can you post your xorg.conf?

---

### Post by lookforlohith on 2008-03-20
there are lot of questions asked on similar basis but no one has answered it correctly...........

---

### Post by uberlube on 2008-03-20
1) do you have glx installed?
2) do you have a graphics card, or is it an integrated intel chipset?

---

### Post by lookforlohith on 2008-03-20
1.i dont have glx installed
2.i dont have separate graphiics card , its integrated

tell me how to install glx ill do it now

---

### Post by uberlube on 2008-03-20
First things first, I was under the impression that the intel integrated graphics chips are supposed to work out of the box, but I will check around real quick to see if there is a driver that is needed. For glx, open the synaptic package manager and search 'glx' and tell me if any of them are installed.

---

### Post by lookforlohith on 2008-03-20
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report


i dont know y..... it was working in the morning . now its showing this error

---

### Post by uberlube on 2008-03-20
open a terminal and type in:

```
sudo dpkg --configure -a
```

*type in your password*

Make sure that synaptic is closed for this and then try it again once configured

---

### Post by lookforlohith on 2008-03-20
u r amazing it worked 

and after searching glx .................

entity-gl
genome-compiz-manager
libgl1-mesa-dev
libgl1-mesa-dri-dbg
libgl1-mesa-glx-gdb
nvidia-glx
................................

---

### Post by uberlube on 2008-03-20
So beryl is working then?

---

### Post by lookforlohith on 2008-03-20
no. its not working , why did u ask that . tats my problem

---

### Post by uberlube on 2008-03-20
Sorry im doing 3 things at once here, i thought you were telling me that beryl was working but i didnt realize you were talking about the config. I have one of the forum staff to send me some quick info on the intel chipset you are using and one i have that i'll be able to continue helping.

---

### Post by lookforlohith on 2008-03-20
ya ill wait.........................

im online ....... i want to my . beryl to work today

---

### Post by lookforlohith on 2008-03-20
lohi@lohi:~$ glxinfo
name of display: :0.0
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17


i thing glx informtion is like this

---

### Post by uberlube on 2008-03-20
Go back into synaptic and search for intel and tell me if any of them are installed. Tell me which ones are there to.

---

### Post by lookforlohith on 2008-03-20
acpid
tomboy
whois
gnu-spell checker

only so much is installed in the list appearing

---

### Post by uberlube on 2008-03-20
Also can you activate compiz (extra desktop effects)?

---

### Post by lookforlohith on 2008-03-20
beryl is not working . i cannot expect comipz to work .. any how did u get wat problem i have and wat to install

y is my glxinfo showing error?????????

---

### Post by uberlube on 2008-03-20
Ok i think i know what the problem is here, open a terminal and type in:

```
sudo apt-get install xserver-xgl
```

Then if it installs reboot. Once back in the desktop beryl should work.

---

### Post by lookforlohith on 2008-03-20
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


it is showing like this

---

### Post by uberlube on 2008-03-20
sorry close the synaptic and try again

---

### Post by lookforlohith on 2008-03-20
its installing

---

### Post by lookforlohith on 2008-03-20
lohi@lohi:~$ sudo apt-get install xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsds0 libsomaplayer0 libconfuse0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libglitz-glx1 libglitz1
The following NEW packages will be installed:
  libglitz-glx1 libglitz1 xserver-xgl
0 upgraded, 3 newly installed, 0 to remove and 185 not upgraded.
Need to get 1843kB of archives.
After unpacking 4825kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main libglitz1 0.5.6-1 [76.6kB]
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main libglitz-glx1 0.5.6-1 [29.6kB]
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe xserver-xgl 7.2.0.git.20070224-0ubuntu3 [1737kB]
Fetched 1843kB in 19s (96.3kB/s)                                                                                            
Selecting previously deselected package libglitz1.
(Reading database ... 107014 files and directories currently installed.)
Unpacking libglitz1 (from .../libglitz1_0.5.6-1_i386.deb) ...
Selecting previously deselected package libglitz-glx1.
Unpacking libglitz-glx1 (from .../libglitz-glx1_0.5.6-1_i386.deb) ...
Selecting previously deselected package xserver-xgl.
Unpacking xserver-xgl (from .../xserver-xgl_7.2.0.git.20070224-0ubuntu3_i386.deb) ...
Setting up libglitz1 (0.5.6-1) ...

Setting up libglitz-glx1 (0.5.6-1) ...

Setting up xserver-xgl (7.2.0.git.20070224-0ubuntu3) ...


this is wat happened while installing

---

### Post by uberlube on 2008-03-20
k once done reboot and try opening beryl

---

### Post by lookforlohith on 2008-03-20
lohi@lohi:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x39 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

my $glxinfo is now like this.......

amazing

---

### Post by uberlube on 2008-03-20
And beryl still wont launch?

---

### Post by lookforlohith on 2008-03-20
wat did u ask i dint get..........

if i try to on beryl . my computer crashes...... showing a white screen i must reboot again to come back to normal

---

### Post by lookforlohith on 2008-03-20
brother y no reply

---

### Post by uberlube on 2008-03-20
Ok as far as I can tell something didnt install properly when you installed ubuntu. My suggestion is to format and reinstall ubuntu from scratch. Then make sure that the first thing you do is go to the thread listed below and follow the steps. If it still doesnt work after that then it is a hardware (or driver) incompatibility and your pretty much hooped. This is the extent of my knowledge for intel chipsets as i don't have one, but installing glx should have done the trick.

---

### Post by uberlube on 2008-03-20
[http://ubuntuforums.org/showthread.php?t=707473&highlight=intel](http://ubuntuforums.org/showthread.php?t=707473&highlight=intel)

---

### Post by lookforlohith on 2008-03-20
ok . but lots of thanks for helping me so much...... spending ur time . greatfull to u. brother

---

### Post by uberlube on 2008-03-20
np brother, hope it works out for you :)

---

### Post by lookforlohith on 2008-03-20
no brother ... before this when i try to start beryl there was a crash of computer now it has changed .......................  its not doing anything...

my comp is not getting crashed .plees continue ur help

---

### Post by uberlube on 2008-03-20
ok let me think here.....

do you have the compiz setting manager installed? if not use this in terminal:

```
sudo apt-get install compizconfig-settings-manager
```

Then run this in the terminal and tell me what it does:

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

---

### Post by lookforlohith on 2008-03-20
should i uninstall beryl before doing this

---

### Post by lookforlohith on 2008-03-20
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager


this was the reply

---

### Post by uberlube on 2008-03-20
ok go into the synaptic and search for compiz, then install the settings manager from in there

---

### Post by lookforlohith on 2008-03-20
ya i installed now . wat shall i do

---

### Post by uberlube on 2008-03-20
k now type in that second like i showed you before and tell me what the output is.

---

### Post by lookforlohith on 2008-03-20
lohi@lohi:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager


same

---

### Post by uberlube on 2008-03-20
nope i meant the second command:

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

---

### Post by p_quarles on 2008-03-20
Compiz doesn't exist in the Feisty repos. The Beryl settings manager is called, I believe, beryl-settings-manager.

---

### Post by lookforlohith on 2008-03-20
brother it just came to next line

---

### Post by lookforlohith on 2008-03-20
brother (p_quarel) ..... i just installed compiz manager  ..... .. i dint understand your post

---

### Post by uberlube on 2008-03-20
i think hes using 7.10 am i right? carrying on, press alt+F2 and type in 'compiz' and press enter. Does your desktop effects kick in now?

---

### Post by p_quarles on 2008-03-20
> **uberlube said:**
> i think hes using 7.10 am i right? carrying on, press alt+F2 and type in 'compiz' and press enter. Does your desktop effects kick in now?
Not according to the OP's profile, nor according to the original post itself. ;)

Also, beryl isn't in 7.10.

---

### Post by lookforlohith on 2008-03-20
no nothing is happened ............ wat should i do to on it

---

### Post by uberlube on 2008-03-20
> **p_quarles said:**
> Not according to the OP's profile, nor according to the original post itself. ;)

Also, beryl isn't in 7.10.

LoL, that was like 50 posts ago and Ive been awake for 29 hours. Do you have any advice for him cuz im stumped as of right now. I found this thread which  was trying to work from but apparently its not working for him.

[http://ubuntuforums.org/showthread.php?t=707473&highlight=intel](http://ubuntuforums.org/showthread.php?t=707473&highlight=intel)

---

### Post by uberlube on 2008-03-20
Sorry dude, but I dont know how much more I can do for you. Try out that thread that I posted and hopefully you can get it to work through there or the quarles will come back and help you. I really need to get some sleep 8-[

---

### Post by lookforlohith on 2008-03-20
brother from 20 min my internet was not working.now its fine... tell me pleees

---

### Post by p_quarles on 2008-03-20
@uberlube: Sleep is overrated. :D

@lookforlohith: First of all, please be a little more patient. You can't expect instantaneous help here. 

Ultimately, Beryl is a dead project that was shut down while still in alpha development. It works on some hardware, but it has a lot of problems. 

The best advice I can give you is to upgrade to Ubuntu 7.10, which includes a relatively more stable version of Compiz Fusion. If desktop effects are a high priority for you, this is what you should do, in my opinion.

---

### Post by lookforlohith on 2008-03-20
good night . no problem

bye

---

### Post by lookforlohith on 2008-03-20
brother actually im not urgent . its ok . problems do happen every where . im just thinking of fixing my problem will fetch me some knowledge . so ... its ok ... ill wait

---

### Post by trippinnik on 2008-03-20
can you post your /etc/X11/xorg.conf ? you can open it from the terminal 
```
gedit /etc/X11/xorg.conf
```

---

### Post by lookforlohith on 2008-03-21
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
	Identifier	"Intel Corporation 82865G Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"IBM 6332 E74"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Controller"
	Monitor		"IBM 6332 E74"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
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

---

### Post by lookforlohith on 2008-03-21
yes brother i have posted

---

### Post by trippinnik on 2008-03-22
ok, sorry for the long wait. your xorg.conf looks ok.  try 
```
 glxinfo |grep direct
```
in the terminal. and post the result.
Also have you tried simply using System - Appearance - Desktop Effects to turn them on?

---

