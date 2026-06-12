---
title: "[SOLVED] No Scolling Touchpad on New Dell Inspiron 1420"
date: 2007-07-26
forum: Dell  Ubuntu Support
---

### Post by apswartz on 2007-07-26
I received my new Dell yesterday with Ubuntu preinstalled and the Touchpad is not recognized. I tried the fixes mentioned in the forum and have not been able to correct the problem. 
e.g. [http://ubuntuforums.org/showthread.php?t=168581&highlight=touchpad+dell](http://ubuntuforums.org/showthread.php?t=168581&highlight=touchpad+dell)

Here is the report from my Xorg.0.log

[INDENT](II) Synaptics touchpad driver version 0.14.6 (1406)
Synaptics Touchpad no synaptics event device found (checked 19 nodes)
(**) Option "Device" "/dev/psaux"
(**) Option "SHMConfig" "on"
(**) Option "HorizScrollDelta" "0"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"[/INDENT]

Is this a common problem? Has anybody received a Dell 1420 with Ubuntu where the touchpad is recognized and the scrolling works?

---

### Post by purplearcanist on 2007-07-27
Yes, I have the same problem, I received a dell inspiron 1420 and the touchpad WON'T SCROLL:mad:!

---

### Post by flowbot on 2007-07-29
i'm having no luck, either ... i've tried doing some of the stuff mentioned in [this](http://ubuntuforums.org/showthread.php?t=168581&highlight=touchpad+dell) thread, but to no avail. whenever i try to start gsynaptics, i always get the message:

> GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics


i guess that's because the synaptics driver isn't loading (it can't find the input device):

```

shayne@laptop:~$ cat /var/log/Xorg.0.log | grep synaptics
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
(II) LoadModule: "synaptics"
(II) Reloading /usr/lib/xorg/modules/input//synaptics_drv.so
Synaptics Touchpad no synaptics event device found (checked 19 nodes)
(II) UnloadModule: "synaptics"

```

here's the relevant sections from my Xorg.conf:

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

...

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
    Load           "synaptics"
EndSection

...

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "AlwaysCore"
    Option         "SendCoreEvents" "True"
#    Option         "Device" "/dev/input/mouse0"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
    Option         "SHMConfig" "True"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
#    Option         "Device" "/dev/input/mice"
#    Option         "Protocol" "ImPS/2"
#    Option         "ZAxisMapping" "4 5"
#    Option         "Emulate3Buttons" "true"
EndSection

```

if this helps anyone to troubleshoot, here's my input devices:

```

shayne@laptop:~$ cat /proc/bus/input/devices 
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
H: Handlers=mouse0 ts0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1 
B: EV=120013
B: KEY=1007 2002000 4380207a f840d001 feffffdf ffefffff ffffffff ffffffff
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=0a5c Product=4502 Version=0111
N: Name="Broadcom Corp"
P: Phys=usb-0000:00:1a.0-2.2/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2 
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf f3cfffff ffffffff fffffffe
B: LED=7

I: Bus=0003 Vendor=0a5c Product=4503 Version=0111
N: Name="Broadcom Corp"
P: Phys=usb-0000:00:1a.0-2.3/input0
S: Sysfs=/class/input/input3
H: Handlers=mouse1 ts1 event3 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input4
H: Handlers=kbd event4 
B: EV=40001
B: SND=6

I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input5
H: Handlers=mouse2 ts2 event5 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/class/input/input6
H: Handlers=event6 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input7
H: Handlers=kbd event7 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button (CM)"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/class/input/input8
H: Handlers=kbd event8 
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0003 Vendor=1241 Product=1166 Version=0110
N: Name="HID 1241:1166"
P: Phys=usb-0000:00:1d.0-1/input0
S: Sysfs=/class/input/input9
H: Handlers=mouse3 ts3 event9 
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103

```

i **really, really** want to get my scroll-thing happening on my trackpad.

---

### Post by neptho on 2007-07-30
You've taken out what it wants to work.  Try the following:

```
Section "ServerLayout"
        Identifier      "Default Layout"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
       ... more here ...
        Inputdevice     "Synaptics Touchpad"
EndSection

.... the rest ...

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig" "on"
EndSection

...yet more...
```

---

### Post by AndyQ on 2007-07-30
I think the newer Dells have a different Trackpoint that isn't currently recognised by the synaptics driver.

I have exactly the same issue with my 1720, and the synaptics driver just won't load.

---

### Post by flowbot on 2007-07-30
> **AndyQ said:**
> I think the newer Dells have a different Trackpoint that isn't currently recognised by the synaptics driver.

I have exactly the same issue with my 1720, and the synaptics driver just won't load.

is true ... i've tried everything, including neptho's suggestion ... just won't happen :(

---

### Post by apswartz on 2007-07-30
None of the suggested fixes works for me. Touchpad just isn't recognized.

---

### Post by apswartz on 2007-07-31
I downloaded and tried the newest live cds with Knoppix, SimplyMEPIS, and PCLinoxOS and none of them recognized the Trackpad on my Dell 1420.

---

### Post by sciurus on 2007-07-31
Please submit any additional information to [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/129477](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/129477)

---

### Post by laetfut on 2007-08-01
I am totally new to ubuntu.  I have a dell inspiron 1420 also.  my scrool bar also isn't working.  will an update eventually be made that solves this problem?

---

### Post by apswartz on 2007-08-01
> **laetfut said:**
> I am totally new to ubuntu.  I have a dell inspiron 1420 also.  my scrool bar also isn't working.  will an update eventually be made that solves this problem?

sciuris submitted a bug report, so we can hope that it will be assigned for the next release of the synaptic driver. You can follow that [bug report here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/129477").

---

### Post by tube013 on 2007-08-04
A [_[COLOR="Blue"]patch[/COLOR]_]("http://lkml.org/lkml/2007/8/4/41") was sent to linux kernel mailing list, and noted in the [_[COLOR="Blue"]bug[/COLOR]_]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/129477/") for this..  I've typed up a work-around fix for feisty.. it will need to be redone with every new kernel install though, until it is incorporated into the kernel.


[http://lkml.org/lkml/2007/8/4/41](http://lkml.org/lkml/2007/8/4/41)

I just used the above link, and got the scrolling working with the latest feisty updated kernel 2.6.20-16.29.

This is just a work around, by hand patching alps.c and recompiling all the modules in that directory...

(ala this howto I followed a while ago for my evdo card and airprime.c [http://samat.org/weblog/20070127-high-speed-cellular-wireless-modems-in-ubuntu-linux-6-10.html](http://samat.org/weblog/20070127-high-speed-cellular-wireless-modems-in-ubuntu-linux-6-10.html))

Basically here is a work around until an updated kernel comes down the tree.

#Get kernel source/Build utils
```
sudo apt-get install build-essential linux-headers linux-source
cd /usr/src
sudo tar xjvf linux-source-2.6.20.tar.bz2
cd /usr/src/linux-source-2.6.20/drivers/input/mouse
```

#backup original source
```
sudo cp alps.c alps.c.old
```

#Patch/edit alps.c (I just did this by hand)
```
gksu gedit alps.c
  -Goto Line 55, and add this below it (no quotes): "{ { 0x73, 0x02, 0x50 }, 0x4f, 0x4f, ALPS_FW_BK_1 } /* Dell Vostro 1400 */"
  -Save the file
```

#Rebuild the driver... I'm not sure how to just do the one for alps.. but his will only do the ones in the mouse directory.
```
sudo make -C /lib/modules/`uname -r`/build M=`pwd`
```

# Backup orginial modules
```
cd /lib/modules/2.6.20-16-generic/kernel/drivers/input/mouse/
sudo mkdir old
sudo mv * old
sudo tar cvvf  old.tar old/
sudo rm -Rf old/
```

# Install new modules
```
sudo cp /usr/src/linux-source-2.6.20/drivers/input/mouse/*.ko /lib/modules/2.6.20-16-generic/kernel/drivers/input/mouse/
sudo depmod -a
```

Reboot.. if you have the synaptics settings in your xorg.conf, you should have scrolling working!

---

### Post by apswartz on 2007-08-04
Bless you tube013,
I will try this out and let you know if it works for me.

---

### Post by apswartz on 2007-08-04
tube013,
what a beautiful thing it is when the trackpad works!

Many Thanks.

As far as I am concerned this temporary work-around makes this a SOLVED issue.

---

### Post by AndyQ on 2007-08-04
I can also confirm that the same fix works for 1720 too.

The only slight problem I had was that after the reboot, it failed to boot into X and I had to re-install the NVidia driver (which claimed that the old version had been messed with). This I suspect had something to do with the new mouse drivers (although I'm guessing here).

So thanks very much tube13 for the fix info and the instructions!

---

### Post by jdelaros1 on 2007-08-06
I tried the workaround and scrolling works now on my 1420, but only up/down, sideways scrolling does not work. Am I missing something in xorg.conf?

---

### Post by jdelaros1 on 2007-08-06
Nevermind, HorizScrollDelta was set to 0 in xorg.conf. I guess the question now is what is a good value to set this param to?

---

### Post by jdelaros1 on 2007-08-06
If you bought a Dell Inspiron 1420n with Ubuntu pre-installed, go to [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Scrolling_feature_on_touchpad_does_not_work](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Scrolling_feature_on_touchpad_does_not_work). You don't have to recompile the module, just install a DKMS deb package.

---

### Post by apswartz on 2007-08-06
Actually there is a new kernel that contains a fix here...
[https://bugs.launchpad.net/redfish/+bug/129477/comments/24](https://bugs.launchpad.net/redfish/+bug/129477/comments/24)

---

### Post by LMP900 on 2007-08-06
> **jdelaros1 said:**
> If you bought a Dell Inspiron 1420n with Ubuntu pre-installed, go to [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Scrolling_feature_on_touchpad_does_not_work](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Scrolling_feature_on_touchpad_does_not_work). You don't have to recompile the module, just install a DKMS deb package.

Thanks for the link, jdelaros. :)

---

### Post by anje on 2007-08-06
> **jdelaros1 said:**
> If you bought a Dell Inspiron 1420n with Ubuntu pre-installed, go to [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Scrolling_feature_on_touchpad_does_not_work](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Scrolling_feature_on_touchpad_does_not_work). You don't have to recompile the module, just install a DKMS deb package.

Yes, thank you!  This worked well!

---

### Post by kuja on 2007-08-07
This got the scrolling working indeed, but I am having an issue with it right now. It seems like the touchpad has been made rather a bit less sensitive. Is t here anything I can do about it? I tried playing wiht ksynaptics, but it seemed to cause problems also (the touchpad with it running seemed even less sensitive, I sooner or later lost the ability to scroll (weird), and if I left my finger stationary on the pad, it would drift up and to the left, infinitely, so it was a fight to use) 
?
I']d love to have the scrolling working and a nice, responsive pad. Any suggestions? :confused:

---

### Post by freeflyer57 on 2007-08-09
I have ordered an Inspiron 1420N. Is this touchpad problem widespread or does it effect everybody?

---

### Post by Vogateer on 2007-08-09
It's not a bad problem, but there's no scrolling on the laptop unless you install the package or upgrade the kernel. I own one, and it's great, but you'll have to deal with the laptop being so new that it's not entirely supported (video drivers don't support the newest bits, so you can't have the 3D effects of Compiz until Gutsy).

---

### Post by inchaos on 2007-08-15
So which fix is better?  
I used the fix on the wiki which involved installing a new package and I got scrollbar functionality (both horizontal and vertical) however I also noted a decrease in sensitivity.  In addition sometimes the touchpad goes crazy and highlights things or stops responding completely.  It reminds me of the synaptics bug I had with a broadcom driver and my HP Pavillion dv5000.  

Has anyone noted this same issue with the kernal update?

---

### Post by phynix on 2007-08-15
I don't know if this will help you with the sensitivty or not. I wanted to install touchpad but it gave me that error something like SHM...

So I added this line to my xorg.conf

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"50"
	**Option		"SHMConfig"		"true"**

hope this helps.

---

### Post by inchaos on 2007-08-15
I tried it, so far it seems the same but I'll wait and see, maybe I need a reboot first.

It's not terrible, it's not lagging, but no matter what I change the sensitivity to it remains the same.

---

### Post by daageep on 2007-08-16
Will someone please post their xorg.conf here with the synaptics bits? i don't have an original version. Thank you!

---

### Post by daageep on 2007-08-16
I got vertical scrolling working!! =)

I'm on a Debian system though. I had to download the kernel sources, recompile, etc (everything this thread said to do). Now when I cat /proc/bus/devices/input, I see the alps device. Previously I did not.

The section "inputdevice" for synaptics was added to my xorg.conf. I simply added the settings below to achieve what I wanted.

From what I remember when doing this a while ago, the SHM option is only to let GUI applications change your settings. Don't quote me on it though! It has nothing to do with sensitivity directly.

Add these two lines to your Section "InputDevice" for the synaptics:

Option "MinSpeed" "0.55"
Option "MaxSpeed" "0.6"

They should be self explanatory. Change the settings to whatever you like.

---

### Post by inchaos on 2007-08-16
That worked wonderfully!

Thanks so much!

I'm not sure if this is coincidence or not, but since I added that line to my xorg.conf file about the SHM option, my touchpad hasn't been buggy...no randomly selecting things or jumping around the screen for no reason.

---

### Post by inchaos on 2007-08-16
> **daageep said:**
> Will someone please post their xorg.conf here with the synaptics bits? i don't have an original version. Thank you!

Here is what I have:

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"50"
	Option		"SHMconfig"		"true"
	Option		"MinSpeed"		"0.55"
	Option		"MaxSpeed"		"0.8"
EndSection

---

### Post by ayu on 2007-08-19
Hello,
I have a Vostro 1400, from which I heard is like the 1420, so these guides should work.  Anyways, after I first installed Ubuntu, I tried Dell's dkms ps_mouse deb on 2.6.20-16, and got the vertical scrollbar to work.  After playing around with it for a while, I have since updated to 2.6.22-9 and realized that I've lost all my touchpad settings.  Of course Dell's ps_mouse wouldn't work on the new kernel, so I followed the directions posted earlier in this thread ([http://ubuntuforums.org/showpost.php?p=3132270&postcount=12](http://ubuntuforums.org/showpost.php?p=3132270&postcount=12)), substituting the respective lines for my new kernel, installed, and rebooted, and got my vertical scrolling back.  /proc/bus/input/devices indeed shows the Alps touchpad.  I've then played around with xorg.conf touchpad settings, and rebooted several times, but realized I couldn't get some of the fancy settings listed when you man synaptics.  Ok, I thought, at least I have scrolling.  But when I boot my machine up today, I've lost it.  Devices only shows a ps/2 generic mouse.  The only thing I can think of that I changed since last boot was replacing piix with ide_generic in /etc/modules to get my dvd drive to work.  Any ideas on how to fix this?  Thanks!

---

### Post by ayu on 2007-08-21
Has anybody tried this with the 2.6.22-9 kernel?  Thanks!

---

### Post by quidpro on 2007-08-24
I got my 1420 a few weeks ago and chose the Windows install over the Ubuntu so I could play with the integrated camera. I figured I could install Ubuntu myself, which I did only today once I came across the break=top and modprobe piix info yada yada.

I have just now looked into the scrolling touchpad issue and came across the link here to grab the deb from dell's wiki. That worked great. Rebooted the GUI and had scrolling, and by default it was even more responsive than in Vista! Very fast, which I like.

Just now I installed gsynaptics (sudo apt-get install gsynaptics) and tried to run it. I got a message saying to add a line to xorg.conf.

This is what I ended up with which worked after a alt+ctrl+backspace reboot:

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "50"
    Option         "SHMConfig" "true"
EndSection

(The line to add was "SHMconfig" "true") 

Now when I run gsynaptics from the terminal I can config the touchpad graphically, and I am playing with something I've never used before, which is the Circular Scrolling! I think I like it better than the typical scrolling, but I'm still getting used to it. Kinda has that ipod feel to it. Are there laptops out there with this feature done this way? I've only ever seen the usual vertical/horizontal implementations.

Another thing I'd be interested in, if anyone knows, is the 'hot spot' feature that I had on an older dell from a ways back. You could assign a tap in one of the touch pad corners to behave certain ways. I set mine to use a tap in one corner as a middle mouse click, which made it easier to open new firefox tabs via links. Not driving me crazy or anything, but just wondering...

Thanks for the help everyone!

---

### Post by ayu on 2007-08-25
> **quidpro said:**
> Another thing I'd be interested in, if anyone knows, is the 'hot spot' feature that I had on an older dell from a ways back. You could assign a tap in one of the touch pad corners to behave certain ways. I set mine to use a tap in one corner as a middle mouse click, which made it easier to open new firefox tabs via links. Not driving me crazy or anything, but just wondering...


If you are willing to edit xorg.conf manually, there are tons of options for touchpads that you can see by 'man synaptics.'  I think it's one of the options, but I don't think it's supported by the Dell driver right now, at least it didn't work when I tried playing around with it.

Also, has anyone gotten this to work with the new kernel? Thanks!

---

### Post by ayu on 2007-08-27
> **ayu said:**
> If you are willing to edit xorg.conf manually, there are tons of options for touchpads that you can see by 'man synaptics.'  I think it's one of the options, but I don't think it's supported by the Dell driver right now, at least it didn't work when I tried playing around with it.

Also, has anyone gotten this to work with the new kernel? Thanks!

Yay! :) It works with 2.6.22-10.  Even the virtual corner buttons work!

---

### Post by deserthowler on 2007-09-08
Just downloaded gsynaptics and added "SHMConfig" "on" to xorg.conf and now it doesn't scroll or tap.  HOORAY!!!  Great tip.  Too bad Dell didn't install it as default.

I like the use of gsynaptics instead of editing xorg.conf because then each user can set their own. 

Earl

---

