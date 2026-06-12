---
title: "xorg.conf &amp; SHMConfig for Synaptics Touchpad"
date: 2006-04-30
forum: Desktop Environments
---

### Post by Skizzler on 2006-04-30
Hi,  I have been reading a lot of threads on this forum, a couple wikis, and various blog posts concerning editing my xorg.conf so I can disable tapping on my Synaptics Touchpad, it's really bothersome when typing to accidentally tap it.

Anyway, in all of the other posts it seems like the key is putting ```
Option "SHMConfig" "on"
``` to enable the synclient commands that will allow me to disable tapping.  I've updated my xorg.conf to reflect this, but when starting up qsynaptics or attempting to see what's going on with synclient -l, I get the same message:  'Can't access shared memory area.  SHMConfig disabled?'  

I've restarted and still have this problem, so I don't understand what is missing to enable SHMConfig.  

Here is my xorg.conf where mouses and the touchpad are concerned:
```
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
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"on"
EndSection
```

Can anyone tell me what I might be missing?

---

### Post by chriscando on 2006-04-30
In you xorg.conf, in section "Module" do you load synaptics?  Here is my mine,
```

Section "Module"
        Load    "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
        Load    "synaptics"
EndSection

```

You might also check /var/log/Xorg.0.log to see for any helpful error messages.

---

### Post by Skizzler on 2006-04-30
It seems you were correct that I had not loaded the synaptics module in xorg.conf, however after fixing that and restarting I still have the 'Can't access shared memory.  SHMConfig disabled?' message.

I checked out the /var/log/Xorg.0.log file you talked about, and it seems that something certainly is wrong.  I did a cat /var/log/Xorg.0.log | grep -i "synaptics" and this is what showed up:
```
(**) |-->Input Device "Synaptics Touchpad"
(II) LoadModule: "synaptics"
(II) Loading /usr/X11R6/lib/modules/input/synaptics_drv.o
(II) Module synaptics: vendor="The XFree86 Project"
(II) LoadModule: "synaptics"
(II) Reloading /usr/X11R6/lib/modules/input/synaptics_drv.o
(II) Synaptics touchpad driver version 0.13.6
Synaptics Touchpad no synaptics event device found (checked 4 nodes)
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"

```

Unfortunately I'm not really sure what this is telling me other than the fact that something important-ish seems to be missing.  I guess I need some more advice as to my next step to solving this.

Edit:  I started up qsynaptics again and it told me that I didn't have the driver for the synaptics touchpad installed.  I went into the Synaptic Package Manager and searched for 'synaptics' and found that the xorg-driver-synaptics was already installed.  In case I missed something, I tried "sudo apt-get install xorg-driver-synaptics" and again confirmed that I *do* have a driver installed and it's the last version.

---

### Post by chriscando on 2006-04-30
you might want to check that you are loading the evdev module at startup.
check to see if it is running now by issuing:
lsmod |grep evdev
If not thing shows then edit your /etc/modules file and add evdev and reboot. Hopefully this works.

---

### Post by Skizzler on 2006-04-30
I checked lsmod | grep evdev, it is listed with "evdev 9088 0", but it wasn't specifically in the /etc/modules file.  I added to /etc/modules, but I see the same result on lsmod | grep evdev, and still can't access shared memory with synclient.

I don't know what's missing, from everything else I've read it seems I should have everything set properly so as to be able to use synclient commands.

Also, I just realized that I posted this while browsing in the **K**ubuntu Desktop Support section, and not properly in the Ubuntu section, since that is what I am using.  I hope this hasn't affected any of the possible solutions, and if so I apologize for my mistake.  Is there a mod who could please move this thread to the regular Ubuntu Desktop Support section?

---

### Post by GeneralZod on 2006-05-01
I think it's a bug (that's still affecting Dapper, annoyingly enough) :

[https://launchpad.net/bugs/3406](https://launchpad.net/bugs/3406)

---

### Post by Skizzler on 2006-05-01
Oof, that's unfortunate.  Does it mean for now that I'm out of luck on the fixage of this issue?

---

### Post by chriscando on 2006-05-01
Here is a part of my xorg.conf, maybe you can compare with yours.
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5 6 7"
        Option          "Buttons"               "9"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "SHMConfig"             "on"
        Option          "HorizScrollDelta"      "0"
EndSection


```

One other thing, in /boot/grub/menu.lst where you boot your 2.6 kernel, see if you have a string that has psmouse in it. Ive heard of people removing that to get it to work.

---

### Post by Skizzler on 2006-05-02
In /boot/grub/menu.lst there is no string with the word "psmouse" or any variant of "mouse".  

Thanks for all the help so far chris, it's too bad nothing is seeming to work.

 So far in typing this reply part of my lower thumb has hit the touchpad and my cursor has been displaced three times!  It's too bad the manufacturer (Averatec) didn't put a hardware disable switch, it seems like it'd be a pretty common annoyance.

---

### Post by nickleus on 2006-05-03
This is really amazing, I can't believe that something so simple as **disabling tapping has no solution**!

Since my thread here:
[http://www.ubuntuforums.org/showpost.php?p=942248&postcount=3]("http://www.ubuntuforums.org/showpost.php?p=942248&postcount=3")

has never been answered i'll post an update here of what i've recently tried and see if there are any genius' working on Ubuntu and if they can help me.

0. I'm running Ubuntu 5.10 on a Dell Inspiron 510m laptop.

1. I'm able to run *synclient*, and **synclient -l** reflects my configuration in **/etc/X11/xorg.conf**, but none of the options ever have any effect:
```
Section "Module"
...
    Load    "synaptics"
...
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "Emulate3Buttons"    "true"
    Option        "ZAxisMapping"        "4 5"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option  "LeftEdge"              "120"
    Option  "RightEdge"             "830"
    Option  "TopEdge"               "120"
    Option  "BottomEdge"            "650"
    Option  "FingerLow"             "14"
    Option  "FingerHigh"            "15"
    Option  "MaxTapTime"            "0"
    Option  "MaxTapMove"            "0"
    Option  "MaxDoubleTapTime"      "0"
    Option  "ClickTime"  "0"
    Option  "EmulateMidButtonTime"  "75"
    Option  "VertScrollDelta"       "10"
    Option  "HorizScrollDelta"      "0"
    Option  "MinSpeed"              "0.45"
    Option  "MaxSpeed"              "0.75"
    Option  "AccelFactor"           "0.020"
    Option  "EdgeMotionMinZ"    "30"
    Option  "EdgeMotionMaxZ"    "160"
    Option  "EdgeMotionMinSpeed"    "200"
    Option  "EdgeMotionMaxSpeed"    "200"
    Option  "EdgeMotionUseAlways"    "0"
    Option  "UpDownScrolling"       "1"
    Option "TouchpadOff" "0"
    Option "GuestMouseOff" "0"
    Option "LockedDrags" "0"
    Option "RTCornerButton" "2"
    Option "RBCornerButton" "3"
    Option "LTCornerButton" "0"
    Option "LBCornerButton" "0"
    Option "TapButton1" "0"
    Option "TapButton2" "0"
    Option "TapButton3" "0"
    Option  "CircularScrolling"     "0"
    Option  "CircScrollDelta"       "0.1"
    Option  "CircScrollTrigger"     "2"
    Option  "CircularPad"     "0"
    Option  "SHMConfig"  "true"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

``` 
2. **qsynaptics** also starts up no problem, but none of my applied changes have any effect.

3. There are no error messages in my **/var/log/Xorg.0.log**:
> (**) |-->Input Device "Synaptics Touchpad"
(II) LoadModule: "synaptics"
(II) Loading /usr/X11R6/lib/modules/input/synaptics_drv.o
(II) Module synaptics: vendor="The XFree86 Project"
(II) LoadModule: "synaptics"
(II) Reloading /usr/X11R6/lib/modules/input/synaptics_drv.o
(II) Synaptics touchpad driver version 0.13.6
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event1
(--) Synaptics Touchpad ALPS touchpad found
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
Synaptics DeviceInit called
SynapticsCtrl called.
Synaptics DeviceOn called
(--) Synaptics Touchpad ALPS touchpad found 
Does this line having anything to do with the problem, possibly indicating an incompatibility issue between an XFree86 driver and Xorg? (feel free to laugh at my ignorant question here =)
**Module synaptics: vendor="The XFree86 Project"**

4. **lsmod |grep evdev** returns:
> evdev 9088 1 
5. There's nothing about *psmouse* in **/boot/grub/menu.lst**

I must say that i was bedazzled at how easily it was to set up a wireless internet connection in Ubuntu, but I seriously/literally cannot work with ubuntu if every slightest touch i do on my touchpad causes me to select what is underneath (with annoying and unpredictable consequences). I am seriously going to have to find another distro, JUST BECAUSE OF THIS! Unbelievable. Why can't anybody just **fix** the stupid thing instead of making people wait for a new version of Ubuntu which from what i see still isn't fixed? Who has a solution?!

---

### Post by Skizzler on 2006-05-03
I guess I agree with nickleus that the lack of a solution on this issue is pretty surprising.  For me this begs the question - is this something that Ubuntu *should* be able to fix, or is it more hardware related and a simple patch can't fix it?

If it's true that FC4 and other distros can fix it, I'd assume it's the former, and that's a bit disappointing.  So far every other experience I've had with Ubuntu has been a positive one, but this touchpad tapping thing is becoming prohibitive to school work (currently a term paper) and especially coding.

Maybe somebody in the know can at least provide an ETA on a fix to this, so I know whether or not it'd be worthwhile to pick up a new distro? ><

---

### Post by nickleus on 2006-05-03
Yeah, it was no problem in FC4. Amen Skizzler. I'd like to keep ubuntu, but i need to know if this is going to be fixed or if i can just move on..

---

### Post by chriscando on 2006-05-04
What is the output when you run: synclient -l
And what is the output after you issue: synclient HorizScrollDelta=0

---

### Post by Skizzler on 2006-05-04
I am still returning the same error in both cases:
```
Can't access shared memory area.  SHMConfig disabled?
```

---

### Post by nickleus on 2006-05-05
i uninstalled ubuntu and installed freebsd 6 instead... maybe i'll install ubuntu later on when these things have been ironed out (including mplayer bugs, could never get mplayer to work properly either...)

---

### Post by jfdill_2 on 2006-05-05
I too have an Averatec.  I found this web page that looks promising, can't wait to try it, skip down to *Disabling the tap-to-click "feature" on a laptop touchpad*

[http://home.uchicago.edu/~chad/](http://home.uchicago.edu/~chad/)

Found another one from the Debian wiki, interesting with the funky quoted brackets around SHMconfig...

[http://wiki.debian.org/?SynapticsTouchpad](http://wiki.debian.org/?SynapticsTouchpad)

---

### Post by mjziegle on 2006-05-12
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
        Option          "MaxTapTime"            "0"
EndSection

The last two option lines will enable qsynaptics and turn off click to tap.  qsynaptics sucks since it doesn't remember the settings everytime gdm restarts.  MaxTapTime takes care of it permanently.

Let me know if it works for you.  Worked for me.

Thanks,

Matt

---

### Post by nickleus on 2006-05-12
no,  that didn't work. just installed Fedora Core 5 and it works right out of the box.

---

### Post by talionis on 2006-05-15
Matt, I can't thank you enough for that.  I was going *crazy* with that touchpad continuously shifting focus on me.  You've saved my sanity.  :P


Regards,
--J.R.

---

### Post by Morphius on 2006-06-02
If you are running dapper there is a known bug that will cause mouse issues for synaptic pads.

[https://launchpad.net/distros/ubuntu/+bug/47971](https://launchpad.net/distros/ubuntu/+bug/47971)

Check out the link for a work around.

---

### Post by Mythril on 2007-02-07
Check that your "Device" option is well-configured (cat /dev/your/device). If it is not, look at /proc/bus/input/devices and /dev/input/by-path/.

---

### Post by kuukie on 2007-02-10
Typing 'apropos keyboard' led me to 'man syndaemon' which is a fix for the tapping problem. Hope it helps.

---

### Post by Heinzelotto on 2007-02-11
I just got mine working with this page: [http://www.pc-erfahrung.de/linux/linux-touchpad.html](http://www.pc-erfahrung.de/linux/linux-touchpad.html)
it is written in german, I'll try to explain you the procedure:


open  your xorg.conf (after you made a backup of course ;)) in an editor.
Then navigate to the section "input device" (the one which specifies the properties of the mouse) and comment out everything except of the Identifier.

It should look then somehow like this:

```

Section "InputDevice"
    Identifier     "Configured Mouse"
    #Driver         "mouse"
    #Option         "CorePointer"
    #Option         "Device" "/dev/input/mice"
    #Option         "Protocol" "ExplorerPS/2"
    #Option         "ZAxisMapping" "4 5"
    #Option         "Emulate3Buttons" "false"
EndSection

```

Now just add these lines:

```

   Identifier	"Mouse1"
   Driver  	"synaptics"
   Option 	"Device"  	"/dev/psaux"
   Option	"Protocol"	"auto-dev"
   Option	"LeftEdge"      "1700"
   Option	"RightEdge"     "5300"
   Option	"TopEdge"       "1700"
   Option	"BottomEdge"    "4200"
   Option	"FingerLow"	"25"
   Option	"FingerHigh"	"30"
   Option	"MaxTapTime"	"180"
   Option	"MaxTapMove"	"220"
   Option	"VertScrollDelta" "100"
   Option	"MinSpeed"	"0.06"
   Option	"MaxSpeed"	"0.12"
   Option	"AccelFactor" "0.0010"
   Option	"SHMConfig"	"on"

```

it should now look like this:

```

Section "InputDevice"
    Identifier     "Configured Mouse"
    #Driver         "mouse"
    #Option         "CorePointer"
    #Option         "Device" "/dev/input/mice"
    #Option         "Protocol" "ExplorerPS/2"
    #Option         "ZAxisMapping" "4 5"
    #Option         "Emulate3Buttons" "false"

    Driver      "synaptics"
   Option       "CorePointer"                   #[COLOR="Red"]make sure you added this[/COLOR]
   Option       "Device"        "/dev/psaux"
   Option       "Protocol"      "auto-dev"
   Option       "LeftEdge"      "1700"
   Option       "RightEdge"     "5300"
   Option       "TopEdge"       "1700"
   Option       "BottomEdge"    "4200"
   Option       "FingerLow"     "25"
   Option       "FingerHigh"    "30"
   Option       "MaxTapTime"    "180"
   Option       "MaxTapMove"    "220"
   Option       "VertScrollDelta" "100"
   Option       "MinSpeed"      "0.06"
   Option       "MaxSpeed"      "0.12"
   Option       "AccelFactor" "0.0010"
   Option       "SHMConfig"     "on"
EndSection

```

also make sure you added the 
```
Option "CorePointer"
```
to make sure the touchpad is the main input device

if you plan to use a mouse which will be plugged into your laptop, you have to declare the mouse as "CorePointer" and the Touchpad as "AlwaysCore" as far as I understood that text ;)

Now save your configuration and restart X


I hope this will work for you, at least it did for me...
if it does, you can use your favourite synaptics-configuration-program to define the behaviour of your touchpad

---

### Post by Reschat on 2007-03-19
Now I have to write here if someone still have problems with it.

I have tryed for a few hours tryed to disable clik by tap and I finally got it - by changing the order of the settings.

Before (**When it didn't work**):
> 
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
	Identifier	"Configured Mouse"
   Driver      "synaptics"
   Option       "AlwaysCore"                  
   Option       "Device"        "/dev/psaux"
   Option       "Protocol"      "auto-dev"
   Option       "LeftEdge"      "1700"
   Option       "RightEdge"     "5300"
   Option       "TopEdge"       "1700"
   Option       "BottomEdge"    "4200"
   Option       "FingerLow"     "25"
   Option       "FingerHigh"    "30"
   Option       "MaxTapTime"    "0"
   Option       "MaxTapMove"    "220"
   Option       "VertScrollDelta" "100"
   Option       "MinSpeed"      "0.06"
   Option       "MaxSpeed"      "0.12"
   Option       "AccelFactor" "0.0010"
   Option       "SHMConfig"     "on"
EndSection

Now (**Working**):
> Section "InputDevice"
	Identifier	"Configured Mouse"
   Driver      "synaptics"
   Option       "AlwaysCore"                  
   Option       "Device"        "/dev/psaux"
   Option       "Protocol"      "auto-dev"
   Option       "LeftEdge"      "1700"
   Option       "RightEdge"     "5300"
   Option       "TopEdge"       "1700"
   Option       "BottomEdge"    "4200"
   Option       "FingerLow"     "25"
   Option       "FingerHigh"    "30"
   Option       "MaxTapTime"    "0"
   Option       "MaxTapMove"    "220"
   Option       "VertScrollDelta" "100"
   Option       "MinSpeed"      "0.06"
   Option       "MaxSpeed"      "0.12"
   Option       "AccelFactor" "0.0010"
   Option       "SHMConfig"     "on"
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

I can't believe that such a stupid thing fixed it all.

And remeber the:
>         Load    "synaptics"
Under: Section "Module"

I hope it helped.

---

### Post by Topinambur on 2007-04-01
Just followed the example of xorg.conf from [http://web.telia.com/~u89404340/touchpad/index.html]("http://web.telia.com/~u89404340/touchpad/index.html")
After restarting X both gsynaptics and qsynaptics worked.

Guys, don't forget to actually identify the input device such as "TouchPad" in Section "ServerLayout" of /etc/X11/xorg.conf. Otherwise, this device is not even going to get loaded. See the example below:

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	[COLOR="Navy"]**InputDevice    "TouchPad" "AlwaysCore"**[/COLOR]
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

---

### Post by Eothred on 2007-04-10
reschat: you're like my hero right now:) cheers mate!

---

### Post by Heinzelotto on 2007-04-21
@ reschat:

it didn't work because bot of your InputDevices had the same Identifier. change the Identifier of one of them and load it in the ServerLayout too. Like that:
```

InputDevice    "Configured Mouse"
InputDevice    "Configured Mouse2"  #name of your second Identifier

```

then it should work in both ways

---

### Post by Reschat on 2007-04-21
Heinzelotto - What?

It did work. And that was the whole reason I posted - because I got it to work by changing the order. 

And as you can read Eothred did the same and it worked for him too.

So why do you come here and say that what I did didn't work? It did and still does.

---

### Post by Charlietje on 2007-04-23
I have a strange problem on my Toshiba Satellite A110 touchpad.

When I start normal, I have my touchpad, but the scrollbar doesn't work.
When I log out, and log in again, i have my scrollbar working.
I have tried many things in the xorf.conf but it doesn't change.
Only thing i need to do is log out and log in.
Does anyone know why?

Thanks

---

### Post by jimlocke on 2007-04-26
I'd like to thank Topinambur for the comment about adding the device to the ServerLayout section of sorg.conf.
After seeing it it makes sense it should go there if it is not already, however I have not seen any other posts mentioning this fundamental requirement.

Going to reboot and see if this works!

---

### Post by cephlon on 2007-04-27
Reschat's solutions worked perfectly. No need to change the identifier for me. I did have to reboot though, not just log out.

---

### Post by j09 on 2007-05-01
Actually, yes, there is an easy answer to your question. Go to the "Synaptics Touchpad" part of your xorg.conf. Then add two more lines:
Option		"MaxTapTime"		"0"
Option		"MaxTapMove"		"0"

That's it. It has worked well for me, except that sometimes the computer seems to need to "re-load" the file, and tapping turns on until the next time I restart the computer. Once tapping is on, that doesn't take long. :)

---

### Post by jimlocke on 2007-05-17
Just to follow-up from my earlier post about trying the scrolling/touchpad fix after a reboot, it did work.
My touchpad now has proper vertical scrolling, and may have other improved functionality.

I'm in the process of seeing if this bug has been reported to Ubuntu development.
I think the operating system ought to update sections of this file to support existing devices automatically.

** If someone knows this bug has already been reported, please let me know to avoid a duplicate.  I'm not quite familiar enough w/ how to search bugs against Ubuntu.

---

### Post by L8erG8er on 2007-06-19
Skizzler, I don't know if you're checking back here, but I have a touchpad on a fairly old Compaq Presario, that would not work until I changed the SHMConfig line in xorg.conf to read "true", instead of "on".

That's what worked for me.

---

### Post by Escape311 on 2007-06-26
Heinzelotto: I just wanted to thank you for posting the info for xorg. I've been fighting this for a while and could not get my touchpad working. I have 3 other Dell laptops(D400, D600, and C640) that all work flawlessly but my X300 didn't work by default. After pasting what info you had up, in my xorg and rebooting, everything works now. 


Thanks again!!:D

---

### Post by Pronco on 2007-07-15
It works for me by identifying the  InputDevice "Synoptics Touchpad" in the ServerLayout section

Thank you!

---

### Post by Front187 on 2007-07-25
Awesome!  This fix allows me to access the synaptics configuration correctly.

Just remember to REBOOT, not just logout.  It will save you some undue headache.

---

### Post by Onimae on 2007-07-29
I didn't feel like making another thread for this because the OP has described all of the same symptoms I have had:

My touchpad doesn't seem to be recognized by my system. It works, but I can't do any configuring.

cat /proc/bus/input/devices outputs:
```

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
H: Handlers=mouse0 event0 ts0 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1 
B: EV=120013
B: KEY=100702002000 4380207af840d001 feffffdfffefffff ffffffffffffffff
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2 
B: EV=40001
B: SND=6

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/class/input/input4
H: Handlers=event4 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input5
H: Handlers=kbd event5 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button (CM)"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/class/input/input6
H: Handlers=kbd event6 
B: EV=3
B: KEY=4000 0 0

I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input8
H: Handlers=mouse1 event3 ts1 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

```

It would seem that it just sees it as a PS/2 mouse. Here are the relevant parts of my Xorg.conf:

```

...
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"true"
	Option		"VertEdgeScroll"	"true"
	Option		"HorizEdgeScroll"	"true"
EndSection
...

```

XOrg.0.log:

```

...
(II) Synaptics touchpad driver version 0.14.6 (1406)
Synaptics Touchpad no synaptics event device found (checked 17 nodes)
(EE) xf86OpenSerial: No Device specified.
Synaptics driver unable to open device
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"
...

```

Interestingly enough, tpconfig recognizes it:'

```

Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
Sensor type: unknown (0).
Geometry: rectangular/landscape/up.
Packets: absolute, 80 packets per second.
Corner taps disabled;           no tap gestures.
Edge motion: none.
Z threshold: 6 of 7.
2 button mode; corner tap is right button click.

```

So, only tpconfig seems to know that I have a synaptics touch pad. X ignores it completely. This is mostly for information, but I was also wondering if anyone had any insight as to how to fix this. I have tried all the suggestions in this thread to no avail. I would love any help you guys/gals could offer, as this is one of the two head aches my laptop is giving me right now.

**Peter**

EDIT:

*I should note that I had had a device specified in my Xorg.conf file, but it didn't make any difference. Removing was done on suggestion by another thread.*

---

### Post by AlfaTrion on 2007-08-24
thanks Heinzelotto
my touchpad is now not super sensitive and the scrolley part works too!

---

### Post by Paul.Spectre on 2007-12-12
> **Onimae said:**
> I didn't feel like making another thread for this because the OP has described all of the same symptoms I have had:

My touchpad doesn't seem to be recognized by my system. It works, but I can't do any configuring.

cat /proc/bus/input/devices outputs:
```

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
H: Handlers=mouse0 event0 ts0 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1 
B: EV=120013
B: KEY=100702002000 4380207af840d001 feffffdfffefffff ffffffffffffffff
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2 
B: EV=40001
B: SND=6

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/class/input/input4
H: Handlers=event4 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input5
H: Handlers=kbd event5 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button (CM)"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/class/input/input6
H: Handlers=kbd event6 
B: EV=3
B: KEY=4000 0 0

I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input8
H: Handlers=mouse1 event3 ts1 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

```

It would seem that it just sees it as a PS/2 mouse. Here are the relevant parts of my Xorg.conf:

```

...
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"true"
	Option		"VertEdgeScroll"	"true"
	Option		"HorizEdgeScroll"	"true"
EndSection
...

```

XOrg.0.log:

```

...
(II) Synaptics touchpad driver version 0.14.6 (1406)
Synaptics Touchpad no synaptics event device found (checked 17 nodes)
(EE) xf86OpenSerial: No Device specified.
Synaptics driver unable to open device
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"
...

```

Interestingly enough, tpconfig recognizes it:'

```

Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
Sensor type: unknown (0).
Geometry: rectangular/landscape/up.
Packets: absolute, 80 packets per second.
Corner taps disabled;           no tap gestures.
Edge motion: none.
Z threshold: 6 of 7.
2 button mode; corner tap is right button click.

```

So, only tpconfig seems to know that I have a synaptics touch pad. X ignores it completely. This is mostly for information, but I was also wondering if anyone had any insight as to how to fix this. I have tried all the suggestions in this thread to no avail. I would love any help you guys/gals could offer, as this is one of the two head aches my laptop is giving me right now.

**Peter**

EDIT:

*I should note that I had had a device specified in my Xorg.conf file, but it didn't make any difference. Removing was done on suggestion by another thread.*
Peter
I have the same symptoms that you reported - touchpad not detected, but tpconfig sees it. Anyone come up with a soultion to this one?

---

### Post by mrThefter on 2008-01-04
Chiming in here to say that my touchpad exhibits similar behavior as well.
Going to try a few things, I'll report back the news.

---

### Post by visolarpower on 2008-01-10
Thanks to all for the informative post.

I solved my problem reading this post, I just needed to load the touch pad config program and adjust the sensitivity to solve my issue.    

Cheer's Glen,  Ubuntu is outstanding on a IBM Thinkpad T42 :KS

---

### Post by rocko_mtv on 2008-01-13
I have had a time with this being a newbie to anything other than Win2K or XP and really want to stick with Ubuntu.  I am sure there are others out there still having problems with their TAP CLICK feature on their touch pads.  I feel it may help others to resolve this now until a fix is issued from the Ubuntu Gods.   

For other newbies as myself here are the keys to not "loosing it" trying to do this.

Make a backup by running this command from terminal:   sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup

If your edited xorg.conf file  has errors and you can't  boot back to the desktop you will want to run the following command when you get to the prompt to login:

sudo cp  /etc/X11/xorg.conf-backup /etc/X11/xorg.conf

enter your password if prompted.

Then you will reboot by typing in: sudo reboot

I hope this helps anyone who has tried to get this and it hasn't worked.  I appreciate all who donated to this thread!  Thanks.

Notice the synaptics in the LOAD section and none in the server section.  I also uncommented the CorePointer in the mouse section with an #. Not sure if it makes a difference with "AlwaysCore" in the touchpad section but  I left it anyway because it works.

Here is a copy of my working xorg.conf file that allowed me to access the tap click disable feature:


Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
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
	Load 	"synaptics"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver 		"synaptics"
	Option 		"AlwaysCore"
	Option 		"Device" "/dev/psaux"
	Option 		"Protocol" "auto-dev"
	Option 		"LeftEdge" "1700"
	Option 		"RightEdge" "5300"
	Option 		"TopEdge" "1700"
	Option 		"BottomEdge" "4200"
	Option 		"FingerLow" "25"
	Option 		"FingerHigh" "30"
	Option 		"MaxTapTime" "0"
	Option 		"MaxTapMove" "220"
	Option 		"VertScrollDelta" "100"
	Option 		"MinSpeed" "0.06"
	Option 		"MaxSpeed" "0.12"
	Option 		"AccelFactor" "0.0010"
	Option 		"SHMConfig" "true"
EndSection

Section "InputDevice"
	Identifier 	"Configured Mouse"
	Driver 		"mouse"
#     Option 		"CorePointer"
	Option 		"Device" "/dev/input/mice"
	Option 		"Protocol" "ExplorerPS/2"
	Option 		"ZAxisMapping" "4 5"
	Option 		"Emulate3Buttons" "true"
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
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
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
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
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
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


_____________________________________________________________________________________


Best wishes!
Rick

---

### Post by rosegarden78 on 2008-01-19
Oops ...

---

### Post by rosegarden78 on 2008-01-19
Synaptics works perfectly (like everything else) with Gutsy Gibbon.  I can't wait to see where this project will go.  I'm flabbergasted by the speed and quality of development.  Keep up the good work guys!

---

### Post by milia on 2008-04-08
Hello all.

I kinda encountered the same issue, wanted to halt the touchpad while typing.

So I started reading this thread, but was a bit lost, so I bumped into the following
link which solved my problem in 10 lines:

[http://www.ubuntugeek.com/disable-synaptics-touchpad-while-typing-in-ubuntu.html#more-135](http://www.ubuntugeek.com/disable-synaptics-touchpad-while-typing-in-ubuntu.html#more-135)

Just wanted to share.

---

### Post by dontknoit on 2008-04-26
This may seem like a stupid question...

If you are using Hardy why not just switch the input devices around

# From this 

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection




# to this

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection


# then go to system --> preferences --> mouse --> TouchPad Tab and uncheck the 'enable mouse clicks with touchpad'

Never got gsynaptics to work but this took care of the clicking...

---

