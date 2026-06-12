---
title: "Dual head 9.10 Karmic: laptop screen blanks"
date: 2009-12-29
forum: Desktop Environments
---

### Post by njsharp on 2009-12-29
Kit: Toshiba Satellite A10 laptop i386 2.2GHz, 1Gb DRAM

Display 1024x768 driven by:
$ lspci
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
OS: 9.10 Karmic i386 final release updated from mirror on 2009-12-29.

LVDS1=1024x768
VGA1=polyview 1280x1024

I work best with the laptop screen as main desktop area and vga screen as extension, and at the polyview's best resolution.

Since the Intel 82852/855GM can only handle a virtual 2048x2048, I have to put the VGA1 logically below the LVDS1.  
Side by side would be more intuitive, since the polyview is physically to the right of the laptop, but that would require a virtual of 2302x1024 - not allowed.

Below should say it all to those who speak xrandr:

$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1792, maximum 2048 x 2048
VGA1 connected 1280x1024+0+768 (normal left inverted right x axis y axis) 338mm x 270mm
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm

The above was achieved with the System>Preferences>Display tool, though xrandr works too.

PROBLEM!!!!!!!!
=======
When I have achieved that layout, it is quite common for the laptop screen to go blank, sometimes with the backlight still on (the mouse cursor still shows if moved there), sometimes completely off.

On that machine, Fn+F5 normally toggles the display between L (laptop only), V (VGA only), and Both (L+V)

After a reboot: login screen is only on V which seems to be 1024x768
After login: V seems to be extended desktop, as it is on but completely empty (resolution : no idea) but L is black.

Fn+F5    Result
====    ======
1st    Mirror (L and V=1024x768) then L goes black in seconds
2nd   DT (DeskTop) on L; V=no signal; L goes black in seconds
3rd    DT on V=1280x1024; L black; System>Preferences>Display shows L is above and totally right of V; cannot turn on L as that would require 2304x1792
4th    As required!!  DT=L=1024x768; V=1280x1024 below L; But L turns black in minutes (:=(((
    L seems ON according to Display Prefs, but >OFF>ON does nothing
5th    As 1st again, and sequence repeats as above

This is a SHAMBLES and no, the kit is not faulty now, since reverting to 9.04 is OK.

Is this perhaps a problem with the 9.10 video driver, which I presume is:
xserver-xorg-video-intel (2:2.9.0-1ubuntu2)
as that is for 855 chips
I am puzzled to see that:
xserver-xorg-video-i740 (1:1.3.0-1) 
has loaded also as it does not seem to be required for the 855 chips in the machine.

In 9.04 on the same machine I see:
xserver-xorg-video-i740 (1:1.2.0-2)
xserver-xorg-video-intel-2.4 (2:2.4.1-1ubuntu11~ppa1)


I hope to see this resolved.  I cannot progress to Karmic until it is.

---

### Post by adamantivm on 2010-01-14
Hi njsharp,

I have a similar problem to the one you describe. I have posted about it, with no result, here: [http://ubuntuforums.org/showthread.php?t=1356111](http://ubuntuforums.org/showthread.php?t=1356111)

Basically, since the upgrade to Karmic, the video driver started working all wrong, particularly when configuring dual-head.

One thing that kind of worked for me a little was to disable desktop effects (compiz). This allows me to configure one screen on top of the other (I think even going beyond 2048x2048). It doesn't work perfect. For example, I can't get any "live video" to play (i.e.: webcam, mplayer, etc.) and some apps just don't display their fonts. But it's something.

For the record, I am running a Lenovo Thinkpad T60 with video card:

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
```


current xrandr setting:

```
VGA1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 474mm x 297mm
LVDS1 connected 1400x1050+280+1050 (normal left inverted right x axis y axis) 286mm x 214mm
```

Questions for you:
1) Did you get any additional info, tips, workaroudns, links to forums where somebody is actually following this or something?
2) How do you handle the "switching back to 9.04"?

Thanks

---

### Post by njsharp on 2010-04-26
Sorry, adamantivm, didn't come here again for ages, as you see.

Hmm, not sure overlapping is great, and perhaps YOU could go beyond 2048^2 - your HW looks younger than mine.

As to your Qs:
1 No!
2 I was trialling 9.10 on an additional HD, so switch back was unplug/plug

I am now trialling 10.04 RC on other HW.  Looks good, so will probably move to that on the laptop soon, but challenges are it is nearing its use-by date.  Screen fading (I now use the polycom as main), keyboard space bar dead (so USB kbd instead, which steals the last USB port!), and mouse instead of touchpad (a big hate of mine!).  So dual head on that laptop is fading from my interest.  For me, it was a way of getting more monitor space using HW I happen to have.  I suspect as the 1920x1080 monitors come near to my tightfisted wallet range I'd rather write on one big screen and be able to have eg OOo writer on one side and Firefox etc for research on the other.

I AM still interested in dual head though as I might trial an ASUS AT3IONT-I deluxe on 10.04 later this year, aiming at a DO LOTS box including HTPC, so perhaps a modest monitor on the VGA and an HDMI 1920x1080 as explained at:
[http://ubuntuforums.org/showthread.php?t=1458300](http://ubuntuforums.org/showthread.php?t=1458300)


Cheers

---

