---
title: "fglrx in Fedora 10"
date: 2008-11-25
forum: Fedora/RedHat and derivatives
---

### Post by Izek on 2008-11-25
Just wondering, how do I go about installing fglrx or the ati.com linux catalyst for fedora? radeonhd driver doesn't work (at least not in Ubuntu) even though my Integrated Radeon HD 3200 is a Radeon HD.

---

### Post by igknighted on 2008-11-26
[http://forums.fedoraforum.org/showthread.php?t=205030&highlight=fglrx](http://forums.fedoraforum.org/showthread.php?t=205030&highlight=fglrx)

Not likely for fglrx, but unlike Ubuntu, Fedora will have the latest radeonhd driver, so your chances are good that it will work.

---

### Post by Izek on 2008-11-26
Yeah, I don't think I'll use Fedora ever with how that's going (10+ steps to get fglrx, and the build from F9 I don't know how to do). I don't even know how to start rpmfusion either. -_-

---

### Post by Antman on 2008-11-28
Last thing I heard was that AMD/ATi has released the 8.11 driver which supports X.Org 7.4 (used in Fedora 10).

I'm going to try them on my T60 laptop since I REALLY want to run F10 on it but need fglrx working to run World of Warcraft and some other games (I don't want to downgrade certain parts of F10 just to run it).
Now I'll just run the binary directly (instead of using livna's kmod) and see how it works with WOW.

Fedora is ahead of the curve and AMD/ATi has a problem keeping up a lot of times. That's why I like nVidia... always a lot quicker with their linux support. But, since I have several laptops with ATI x1300's in them... I'm kinda stuck with AMD. :(

---

### Post by adromidon on 2009-01-17
Just so you know comming from someone who divides their time between Ubuntu and Fedora. F10 has issues with fglrx however these are no longer do to the xorg version that was fixed in 8.11 as mentioned here however F10 decided to use a loading screen similar to the Ubuntu one and called it Plymoth this is the thing that currently causes issues with the fglrx driver.

I agree with most people that this is just down right ridiculous seeing as most people with ATI cards want to use that driver however unlike Ubuntu Fedora's focus is not on Proprietary driver support instead it is on free software and the subsequent drivers made by the community like the radeon driver.

However there are a hand full of people in the community that took the time to figure out how to make it work with Fedora 10 and those people need to be given credit where due.

I use Fedora yes but honestly I am sticking to Fedora 9 until they work out a way for a more seamless install of fglrx.

Ubuntu on the other hand does not have these issues because their developers are willing to code around issues like this and simply give an "your installing a driver not supported by the community" warning.

Bottom line is the software packageing principles between both Distros is different. Ubuntu will allways cater to just out right out of the box usage thus making it great for the first time Linux User. Fedora is more focused on finding open source replacements for  proprietary drivers/software. This makes Fedora more of a power user distro. Both have the same functionality but Fedora does require slightly more tweaking at times thus the average first time user may have issues.

I use both as said because I am not a distro fanboy I love any and every replacement to windows Mac OS included

---

