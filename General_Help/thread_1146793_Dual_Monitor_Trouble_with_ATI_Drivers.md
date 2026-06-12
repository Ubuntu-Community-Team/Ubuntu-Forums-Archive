---
title: "Dual Monitor Trouble with ATI Drivers"
date: 2009-05-02
forum: General Help
---

### Post by all2human on 2009-05-02
Wondering if anyone can help me out: I'm having trouble getting my monitors set up properly after installing 9.04.  

My graphics card is an ATI Radeon HD4870. I've installed the proprietary AMD drivers using **System > Administration > Hardware Drivers** so that I can use compiz, and am now trying to get it so that my monitors are not mirrored. When I run the Catalyst Control Center, under Display manager, under Multi-Display the "Display Configuration" dropdown is grayed out, and it says "Unknown" there. In the area where it shows an outline of the displays, it's a single rectangle with "1:2" in it, instead of showing separate rectangles for monitors "1" and "2".

Something that might be relevant: if I switch back to the open drivers, unchecking the option for mirrored screen does nothing until I manually change the resolution on one of the monitors so that it's different from the other one.  Before I do this, telling it to identify monitors shows WDE 22" on both screens; after I've changed the resolution, I get the correct identifications--Acer 23" on one and WDE 22" on the other.

I'm pretty much new to linux/ubuntu, but I was running 8.10 for a few weeks before I reinstalled (clean) and I had dual monitors working fine there with the proprietary drivers. Any ideas?

---

### Post by all2human on 2009-05-03
Anyone know what I should check into?

---

### Post by tiny122 on 2009-05-04
Roughly in the same boat.  I can get Ubuntu to work as one big screen but what I am after is to get 2 independent desktops (one on each screen) so when an App is maximized it maximizes to the physical screen it is in and not across both screens.

run ATI Radeon 4670 with the Catalyst Control Center installed.

---

### Post by karrank% on 2009-05-04
> **all2human said:**
> Wondering if anyone can help me out: I'm having trouble getting my monitors set up properly after installing 9.04.  

My graphics card is an ATI Radeon HD4870. I've installed the proprietary AMD drivers using **System > Administration > Hardware Drivers** so that I can use compiz, and am now trying to get it so that my monitors are not mirrored. When I run the Catalyst Control Center, under Display manager, under Multi-Display the "Display Configuration" dropdown is grayed out, and it says "Unknown" there. In the area where it shows an outline of the displays, it's a single rectangle with "1:2" in it, instead of showing separate rectangles for monitors "1" and "2".

Something that might be relevant: if I switch back to the open drivers, unchecking the option for mirrored screen does nothing until I manually change the resolution on one of the monitors so that it's different from the other one.  Before I do this, telling it to identify monitors shows WDE 22" on both screens; after I've changed the resolution, I get the correct identifications--Acer 23" on one and WDE 22" on the other.

I'm pretty much new to linux/ubuntu, but I was running 8.10 for a few weeks before I reinstalled (clean) and I had dual monitors working fine there with the proprietary drivers. Any ideas?

Running 8.04 w/IGP ATI 3200 on ASRock 780G mobo but I had dualscreen probs similar to this until I installed ATI Catalyst Control Center. Add/Remove>Other>ATI Catalyst Control Center.
Fiddling with the settings provided by Ubuntu didn't seem to work as reliably as the ATI CCC.

---

### Post by all2human on 2009-05-04
Thanks for the reply.  I've been trying to use the CCC like you say; once I installed 9.04, though, I didn't have access to the same options in it.  Under 8.10 I could change the settings under multi-display; under 9.04 I don't seem to be able to.

I figured out that if I used the "Display" under preferences, I could get it to unmirror if I unchecked the box and then set the resolutions on the monitors so that they were different (as they should be).  Without changing the resolutions it would stay mirrored even with the box unchecked.

So now my main question is the same one as tiny122's: how do you get it to maximize only to one monitor, instead of across both?

---

### Post by jazzgillum on 2009-05-04
I can't get dual monitors to work at all. Running Ubuntu Studio based on Hardy Heron. Radeon 7000 card. Asus A7N8X-E motherboard. "Add/Remove Applications" indicats I've got Catalyst Control Center installed. But how do I get to it?! I figured it would show up in System|Preferences or System|Administration, but I don't see it!

---

### Post by Stickee on 2009-05-04
> **jazzgillum said:**
> I can't get dual monitors to work at all. Running Ubuntu Studio based on Hardy Heron. Radeon 7000 card. Asus A7N8X-E motherboard. "Add/Remove Applications" indicats I've got Catalyst Control Center installed. But how do I get to it?! I figured it would show up in System|Preferences or System|Administration, but I don't see it!
Check Applications -> Accessories.

Mine is there, but the option to use Xinerama, i.e. dual monitors, is greyed out. :(

---

### Post by Silmaril89 on 2009-06-13
I'm having the exact same problems.  I really need dual monitors working in Ubuntu.  Someone please help.  I'm willing to try anything.

---

### Post by Hamal on 2009-06-18
I'm having issues with dual monitor support too, however I have a "workable" solution so far.

Simply ditch the third pary ATI drivers and use Ubuntu's "Display" dialog.

The only problem with this is that you lose Compiz support, but the open source drivers should be able to do this for you anyway. Unfortunately, I'm still experimenting on how to get the Open Source drivers doing the 3D thing so bear with me.

If anyone else can give us a heads up that would be cool.

---

### Post by Hund on 2009-06-18
I couldnt get my second monitor to work at all with Ubuntu 9.04 and my 4850 card. Thats why Im back with Ubuntu 8.10 again. Hopefully theres a solution for it soon enough.

---

### Post by jens-mct on 2009-06-22
**I also can't extends my screen anymore (which i could with U8 )**
[IMG]http://img177.imageshack.us/i/screenshotcatalystcontr.png/%5D%5BIMG%5Dhttp://img177.imageshack.us/img177/4204/screenshotcatalystcontr.png[/IMG]U9
[IMG]http://img177.imageshack.us/img177/4204/screenshotcatalystcontr.png[/IMG]
U8 (good dutch version)
[IMG]http://www.greandi.be/dumpbox/linux/CCCU8.png[/IMG]
[IMG]http://www.greandi.be/linux/CCCU8.png[/IMG]

---

### Post by Johnny B on 2009-06-22
# sudo cp /etc/X11/xorg.conf /etc/X11xorg.conf.backup
then edit your /etc/X11/xorg.conf

you should have two sections for monitor0 and monitor1, if you only have one, copy it and change it to monitor1
look up the correct horizontal and vertical settings for your monitor, dont copy mine! 
BE CAREFUL EDITING THIS FILE! DOUBLE CHECK YOUR WORK!
then reboot and if theres any problems, restore the backup xorg.conf from recovery mode.

> Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer AL1917W"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Acer AL1917W"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

---

