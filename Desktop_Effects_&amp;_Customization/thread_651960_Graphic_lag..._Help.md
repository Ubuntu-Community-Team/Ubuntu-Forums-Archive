---
title: "Graphic lag... Help"
date: 2007-12-28
forum: Desktop Effects &amp; Customization
---

### Post by Hannibal-King on 2007-12-28
I have some problems making compiz fusion running smoothly.. Or actually also Ubuntu itself..

Even tho I've not enabled all the graphics my window lag a bit when I move them sideways..
When I move it sideways it slowly refreshes like I had a REALLY low refresh rate:
|...........................|
-|...........................|
--|...........................|
---|...........................|
----|...........................|
I'm running 1400x1050@60 Hz... I am unable to change the 60 hertz.. I feel like I've tried everything.. But this should not be a problem since I have a LCD screen.. or?

My spec's:
IBM Thinkpad T60
SXGA+, 14.1"
1.83 Duo T5600
3Gb ram 667 Mhz
ATI x1400 128mb (512)
100gb 7200 rpm

Model 2007-FUG

Anyone...?

---

### Post by Forlong on 2007-12-28
Go to *System &#8594; Administration &#8594; Restricted Drivers Manager* and enable the driver for your graphics card.

---

### Post by Hannibal-King on 2007-12-28
No.. you don't understand.. I already did all these things and my compiz fusion IS working perfectly.. I just have this problem making it runnings smoothly..

---

### Post by Forlong on 2007-12-28
Aha. Is it better when turning off Compiz? Because you said it's a problem with Ubuntu in general at first.

---

### Post by Hannibal-King on 2007-12-28
No.. It does it no matter if I have compiz turned on or off... 
I can live with it.. It's just frustrating because I wanna show ubuntu off too some vista lovers  :P

---

### Post by LinuxIsInnovation on 2007-12-28
Open synaptic and search for xserver-xgl
If it is installed, remove the package, and reboot your computer..

---

### Post by LinuxIsInnovation on 2007-12-28
> **Hannibal-King said:**
> No.. It does it no matter if I have compiz turned on or off... 
I can live with it.. It's just frustrating because I wanna show ubuntu off too some vista lovers  :P

Wow.. that's the exact thing I am doing now at my college.. 2 of them have already switched to Ubuntu, and 1 is dual booting :D

---

### Post by Forlong on 2007-12-28
Yeah, you can't use Xgl without Compiz.
Try removing it
```
sudo apt-get remove xserver-xgl

```
But it shouldn't lag when using Compiz... :???:
So tell us if it's still lagging after rebooting, maybe it's a driver issue.

---

### Post by Hannibal-King on 2007-12-28
Nope.. removing xserver-xgl did not help.. It just made me COMPLETELY unable to use compiz-fusion.. but the refresh lag is still there.

it still does lag with the window like in my first post..
With AND without compiz fusion.. it just more clear with compiz because of the whoppling effect.. But it also does it with all visual effects turned off..

Anyone..?

---

### Post by Forlong on 2007-12-28
What's the output of ```
fglrxinfo
```

---

### Post by Hannibal-King on 2007-12-28
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6473 (8.37.6)

```

---

### Post by LinuxIsInnovation on 2007-12-28
Looks predominantly like a driver problem.

---

### Post by LinuxIsInnovation on 2007-12-28
ATI does have a lot of issues with graphics on Ubuntu/Debian

---

### Post by Forlong on 2007-12-28
Run this
```
sudo dpkg-reconfigure xserver-xorg
```
and try to set the correct refresh rate there.

---

### Post by Hannibal-King on 2007-12-28
Error:
"No X server known for your video hardware"

Then I get to choose from a list of drivers.. ati, vesa etc. etc..
Choosing ati does not change a thing..

---

### Post by Forlong on 2007-12-28
Hm... let's see your xorg.conf:
```
grep -v ^# /etc/X11/xorg.conf
```

---

### Post by Hannibal-King on 2007-12-28
```
root@Tronic:~# grep -v ^# /etc/X11/xorg.conf

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

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
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-149
        VertRefresh     60-85
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1400x1050@75"
        EndSubSection
EndSection

Section "Extensions"
        Option          "Composite"     "Enable"
        Option          "Composite"     "1"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Inputdevice     "Synaptics Touchpad"
EndSection
Section "Module"
        Load            "glx"
EndSection
Section "Extensions"
        Option          "Composite"     "0"
EndSection

```

---

### Post by BDSX on 2007-12-28
> **Hannibal-King said:**
> I have some problems making compiz fusion running smoothly.. Or actually also Ubuntu itself..

Even tho I've not enabled all the graphics my window lag a bit when I move them sideways..
When I move it sideways it slowly refreshes like I had a REALLY low refresh rate:
|...........................|
-|...........................|
--|...........................|
---|...........................|
----|...........................|
I'm running 1400x1050@60 Hz... I am unable to change the 60 hertz.. I feel like I've tried everything.. But this should not be a problem since I have a LCD screen.. or?

My spec's:
IBM Thinkpad T60
SXGA+, 14.1"
1.83 Duo T5600
3Gb ram 667 Mhz
ATI x1400 128mb (512)
100gb 7200 rpm

Model 2007-FUG

Anyone...?


I had the same issue, browsed through the ubuntu forums and saw following howto's documenting how to resolve the issue:

[URL="http://ubuntuforums.org/showthread.php?t=239617&highlight=anti+aliasing"]http://ubuntuforums.org/showthread.php?t=239617&highlight=anti+aliasing
[/URL]
[URL="http://ubuntuforums.org/showthread.php?t=646356&highlight=anti+aliasing"]http://ubuntuforums.org/showthread.php?t=646356&highlight=anti+aliasing
[/URL]

They tell you to:
1. Check your driver installation
2. Synch to Vblank 
3. [optitional], enable other settings like: anti aliasing (remove jaggies) configure video playback through openGL  , ...

I think your drivers are fine, so you just need to :
1. go to System => Preferences => Advanced desktop effects settings (compizconfig, may need to be installed)
2. go to "general options" 
3. Under the tab "Display settings" 
4. Uncheck "Detect refresh rate", and Check "Sync to Vblank"

that worked for me (should be vendor independant) hopefully it 'll work for you to


Good luck with it,
BDSX

---

### Post by Hannibal-King on 2007-12-28
Nope.. I did what you stated.. Nothing happened.. Still exact same problem..

I did what I could (since I have a ATI x1400 card and not a Nvidia) in the two post's you linked to.. Nothing.. Still same exact same problem..

Let me state again.. This problem seems to have nothing to do with Compiz Fusion since I have the problems whether compiz is turned on or not.. It seems like a problems with my driver or refresh rate, but I have no idea how to fix it and I also can't find anything about it..

Anyone..?

---

### Post by BDSX on 2007-12-29
Yes it is a sync problem and i also had it with compiz on and off
 (it was even irritating me long before compiz existed, been using linux since suse 8.1)

Does enabling vertical sync using fglrxconfig do anything?

if that doens't help either, maybe you should try with the opensource driver and using the /etc/drirc method linked to in this blog article:

[http://www.chownlife.com/archives/2007/07/syncing_to_vblank.html]("http://www.chownlife.com/archives/2007/07/syncing_to_vblank.html")


I hope you succeed because i also have an ati laptop would love to know a solution for this tearing issue (can't try anything on it now, dad uses it for school and i should study)


Good luck!
BDSX

---

### Post by Hannibal-King on 2007-12-31
Nope.. that didn't help either..

Okay this is starting to frustrate me.. it does the tearing a little fast now, but now you just get a headek instead of being annoyed..

Anyone...?

---

### Post by Hannibal-King on 2008-01-05
Bump.....

---

### Post by alejo0823 on 2008-01-06
well I had that exact problem I partially solved it by enabling vsync or vblank I don't know how is it in English, the problem just solve by enabling it although some lag its still there but its very little

---

### Post by airbornemist6 on 2008-01-07
When I had ubuntu on my desktop (took it off since it's a gaming rig and linux is pointless on it, got a laptop now) my x1950 was producing a similar problem. I never had the problem in Feisty, but I upgraded to Gutsy and all of a sudden uber lag. It seems like it has something to do with the driver, like maybe it doesn't like Gutsy... or something. Sorry I can't provide more help...

---

### Post by majirequiem on 2008-02-17
I am having the same problem as Hanibal. My fglrx info says i have ATI and what have you. Switching to vblank or what not and taking off direct sync causes some tearing. The only thing I noticed is that fglrxinfo is ATI, but when i do Grep | OpenGL, it says mesa.

Any advice? I am a total linux newb, so keep it easy for us new people. Id really love to get into linux but its pretty tough with the x1400 mobility.

---

