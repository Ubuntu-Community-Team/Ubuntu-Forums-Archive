---
title: "MSI WindTop AE1900 (with touchscreen)"
date: 2009-06-25
forum: General Help
---

### Post by waldmeister on 2009-06-25
*File contents will be added later*

Hi all! 
This is my first time posting - so if i hit the wrong forum or sth else, pls tell me :)
So I am from germany, means two important things: First, the obligatory "Sorry for my english" and second, if you can not impress yourself while speaking english, you can ask me in German.

Today i will introduce the [MSI WindTop AE1900 ]("http://www.msi.com/index.php?func=proddesc&maincat_no=654&cat2_no=666&prod_no=1776") to the Ubuntu-Netbook-Remix-Community as the first i'd like to call "WebTop".
Yes, Firefox is THE application for using this device - more later.

_UNR 9.04_
get from [http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)
follow [https://wiki.ubuntu.com/UNR/Installation/Easy](https://wiki.ubuntu.com/UNR/Installation/Easy)
check BIOS (Del-Key) for Boot-Priorities
i did install on whole disk (attention: you might delete the Windows restore partitions)

now, techs.
Format is:** (how it worked out of the box) Device/Part/Funktion: Where to hack.**

**(little) resolution on 16:9 screen: as expected xorg.conf**
First meet and greet was at 11xxsomething 4:3. Does'nt matter what, ugly.
Inside GNOME you can set the resolution to 1360x768. REAL resolution is 136**6**x768.
Problem is some "multiple8"-thing.
So get your xorg.conf and add following modeline and preferred-command into your Monitor-Section:
```

Modeline "1366x768" 85.500 1366 1494 1624 1798 768 770 776 795 +hsync -vsync
Option "PreferredMode" "1366x768"

```** (partially) IDC 6881 Touchscreen : manual evtouch settings**
The Screen will react on finger-inputs, but very wierd. 
*(for hal check and if you know what you are doing: /usr/share/hal/fdi/policy/20-thirdparity/50-ideaco and [http://launchpadlibrarian.net/26936548/50-ideaco.fdi](http://launchpadlibrarian.net/26936548/50-ideaco.fdi))*
The calibration tool will not work. My panel seems to be head over heels.
But it may help you identifying the min and max values for your panel! Start the "move edges" mode and check the borders for their values:
x-left: will be MINX
y-bottom: will be MAXY
x-right: will be MAXX
y-top: will be MINY

now press enter and touch all the crosshairs. End the program and open a console.
Edit```
 /etc/evtouch/config
``` to the four values mentioned above.** Delete all other settings.**

Reboot your computer. If it does not work, try again. For Questions pls add your output of ```
lshal
``` (in a file) to your posting.
See also [https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/317094](https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/317094)

**(mostly) Suspend/Resume: add quirk to hal for pm-suspend**
Suspending in seconds - waking up in a few more seconds. GREAT!
But suddenly the screen is dark. Not black or blank. Only very dark.
Since the ACPI-Settings for brightness do not work, the system restores on the lowest level.
Try ```
pm-suspend --quirk-s3-bios
``` While resuming you shold see the INTEL-GMA-Bios and then a fully enlightend screen.
So add that quirk for your MSI-Machine:

```
/usr/share/hal/fdi/information/10freedesktop/...
```[B]

(mostly) general Touch feeling: modify GTK with .gtkrc-2.0[/B]
A very comfortable feeling ran through me, recognizing what people have done with the Ubuntu Desktop to make it more usable.
Optimized for showing only the most relevant information on small screens. But this is also the disadvantage - some items on the screen are to small for use with fingers. The whole menu is great, but e.g. i needed to resize the close-buttons to make them more hittable.
Also i resized all scrollbars.

Add to your (non)existing .gtkrc-2.0
```

gtk-icon-sizes = "gtk-large-toolbar=32,32:gtk-menu=24,24"
style "scroll"
{
    GtkScrollbar::slider-width        = 25
}

class "*" style "scroll"

```large-toolbar are the firefox-buttons, menu makes the close buttons larger. other gtk-icon-sizes-values are availible.

**(bad) Flash video: ask adobe**
My flash is stuttering with the nonfree-plugin.
Swfdec and gnash could not play some vids or my browsers kills itself.
Withe the adobe flashplugin it is possible to watch videos in fullscreen - but not with full joy.
Any hints??

**(unsolved) Switch-Touch: window-picker-applet**
Hardly nothing i did not test - but i can not find out where to change the appearence of the window-picker to support larger icons and more space between the buttons. Help is very appreciated.

**(unsolved) Multitouch: using synaptics**
Poorly scrolling or tapping with two or more fingers to left-middle-click or scroll does not work for me.
Does evtouch support this? Is it possible to use synaptics as input driver?

---

### Post by comtux on 2009-07-01
I don't have your particular system I have the AE1900-10SUS but I do have another netop that uses the 230 cpu and flash has always been a problem. Even now i have problems with the speed of flash but not nearly as much as i had with my netop 230

I think the problem will resume until flash can be compiled and optimized for our cpu's.

General Spec                 Brand       MSI                 Series       Wind Top                 Model       AE1900-10SUS                 Desktop Type       All-in-one PC                 Recommended Usage       Home / Home Office                 Processor       Intel Atom 330(1.6GHz)                 Processor Main Features       64 bit Dual Core Processor                 Cache Per Processor       1MB L2 Cache                 Memory       2GB DDR2 533                 Hard Drive       250GB SATA                 Optical Drive 1       Tray-load DVD Super Multi rewriter drive, support dual-layer burning                 Graphics       Integrated Intel GMA950, Share memory up to 228MB                 Audio       HD Audio, 2.0 Speakers with SRS Premium Sound                 Ethernet       Gigabit LAN                 Wireless Card       802.11b/g/n                 Power Supply       External 65W Power Adapter with Active PFC                 Monitor       Size: 16.13" (H) x 9.07" (V) (18.5" diagonal) 
Touch Screen 
Anti-glare
Resolution: WXGA (1366 x 768 pixels) 
Surface: 3H Hard-coating 
Brightness: 250cd/m2 
Contrast Ratio: 1000:1 
Viewing Angle: 170° Horizontal, 160° Vertical 
Color: 16.7 millions of colors 
Response: 5 ms 
Pixel Pitch: 0.3mm (H) x 0.3mm (V)                 Keyboard       Color-matched multimedia keyboard                 Mouse       Color-matched mouse                 Operating System       Windows Vista Home Basic                 Special Features       1.3MP Webcam with Microphone                 Motherboard                 Chipset       Intel 945GC                 CPU                 CPU Type       Intel Atom                 CPU FSB       533MHz                 CPU Speed       330(1.60GHz)                 L2 Cache Per CPU       1MB                 CPU Main Features       64 bit Dual Core Processor                 Graphics                 GPU/VPU Type       Intel GMA 950                 Graphics Interface       Integrated video                 Memory                 Memory Capacity       2GB DDR2                 Memory Speed       DDR2 533                 Memory Slots (Available/Total)       1 x SODIMM memory slot (occupied)                 Hard Drive                 HDD Capacity       250GB                 HDD Interface       SATA                 Optical Drive                 Optical Drive Type       DVD Super Multi                 Optical Drive Spec       Tray-load DVD Super Multi rewriter drive, support dual-layer burning                 Audio                 Audio Chipset       Integrated                 Display Spec                 Display Type       Touch Widescreen                 Screen Size       18.5"                 Communications                 LAN Speed       10/100/1000Mbps                 WLAN       802.11b/g/n                 Front Panel Ports                 Front USB       2                 Card Reader       4-in-1 Card Reader (support SD/MMC/MS/XD)                 Back Panel Ports                 Rear USB       2                 RJ45       1 port                 Physical Spec                 Dimensions       18.74" x 14.37" x 1.93"                 Manufacturer Warranty                 Parts       1 year limited                 Labor       1 year limited
[B]
[/B]

---

### Post by comtux on 2009-07-01
> **(unsolved) Multitouch: using synaptics**
Poorly scrolling or tapping with two or more fingers to left-middle-click or scroll does not work for me.
Does evtouch support this? Is it possible to use synaptics as input driver?The **evdev** driver can serve as both a pointer and a keyboard input device, and may be used as both the core keyboard and the core pointer. Multiple input devices are supported by multiple instances of this driver, with one Load directive for evdev in the Module section of your xorg.conf for each input device that will use this driver.

I tried using the synaptic driver and i couldn't get the driver to recognize the touch screen as a supported device.

---

### Post by GREZZO16 on 2009-07-05
hi to everyone
i've the msi ae1900-04IT (i'm from italy) and i'm pretty satisfied by this computer.

Now i've managed to install UNR 9.04 and i've managed to let it work propely ONLY with the infos of you thread and this one ( [http://ubuntuforums.org/showthread.php?t=1180382](http://ubuntuforums.org/showthread.php?t=1180382))

[s]i'm here to ask you 2 things:
1= what about expanding your thread with detailed instructions with the command-line commands? (i've not yet understood what i have to do to modify GTK)
2= what about merging the informations of you thread with the others in the other related thread? there are some useful things in both.

thank you[/s]

**EDIT: i've managed to fix other bugs (webcam and video performances) and i'll post them on the other thread. maybe we should create an official thread HERE and on msi official forum.**


byeeeeee

---

### Post by GREZZO16 on 2009-07-09
EHY LOOK HERE
[http://forum-en.msi.com/index.php?topic=128465.0](http://forum-en.msi.com/index.php?topic=128465.0)

msi start to support actively the forum!

in next days i'll post something in the guide section: an AE1900 LINUX GUIDE with everything i know (and suggestions allowed)

---

### Post by GREZZO16 on 2009-11-01
hi

with ubuntu 9.10 most of problems are solved by default.

only touchscreen and microphone don't work "out of the box".

here you are the solution
[http://forum-en.msi.com/index.php?topic=128477.0](http://forum-en.msi.com/index.php?topic=128477.0)

byeee

---

