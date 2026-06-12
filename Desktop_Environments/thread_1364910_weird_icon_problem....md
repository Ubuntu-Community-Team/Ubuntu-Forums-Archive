---
title: "weird icon problem..."
date: 2009-12-26
forum: Desktop Environments
---

### Post by jasonrobert on 2009-12-26
Hi, I have just installed xubuntu 9.10 on my ibm thinkpad 240x laptop which previously ran ubuntu 8.04 (which ran on this laptop with no problems), but I couldnt get wireless internet to work. 

It seems to run all the programs fine (and wireless internet works now as well) but the minimise/maximise/close window icons appear in random places all over the screen when I roll over them. When I move a window over them they dissapear (as if i was erasing them). As I say everything runs ok and at a reasonable speed. Its just these annoying icons, and I was wondering how I could get rid of them?

Oh and i have just noticed that they dont appear properly in their proper places. 

Cheers, Jason.

---

### Post by XubuRoxMySox on 2009-12-26
I have no such issues, but I get the idea from other posts here that screen resolution settings have been a minor thorn in the side of Karmic Xubuntu. I can only suggest two things:

First, make sure your new install is fully updated. Some of the problems have been fixed in recent updates, and

Second, skim through the threads in this section about screen resolution. Several fixes and workarounds are offered that have fixed other seemingly unrelated display issues.

If one of them works, please say so for the benefit of others.

A newbie to Xubuntu,
Robin

---

### Post by itachi1 on 2009-12-26
I installed XUbuntu 9.10 a few days ago, and I have the exact same problem on my Thinkpad 240x.

I have tried a few different things--made sure all upgrades are current, latest revision of x.org core, made an xorg.conf file and pasted the resolutions and timings from

[http://moblog.net/view/203052/xubuntu-on-a-thinkpad-240x](http://moblog.net/view/203052/xubuntu-on-a-thinkpad-240x) 

but nothing has made a difference.  The machine is usable, but the corruption problem is driving me nuts.

My hunch is that it may have to do with the current revision of the siliconmotion x drivers, but I am more than willing to be wrong, and would welcome solution suggestions from any and all parties!

List of bugs:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-siliconmotion](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-siliconmotion)

Possibly related, but badly filed and due to be deleted:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-siliconmotion/+bug/441284](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-siliconmotion/+bug/441284)

Possibly related, but includes freezing and undescribed "artifacts" as well as multiple cursors:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-siliconmotion/+bug/144182](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-siliconmotion/+bug/144182)

I was trying to find a newer revision of the drivers to install or a newer X package for Ubuntu than the one offered through upgrades.  Unstable or experimental?  I couldn't seem to find packages from those branches.

This is really sad to me, because as far as I can tell, it installed great using a Thinkpad 600e without a hard drive, installed to USB hard drive, and only took a few reboots to get everything sorted out.

I may have to head over to CrunchBang to see if it works better on this hardware, but would love to return to XUbuntu with a great underlying current distro on ancient hardware...

As dixiedancer suggests, I'll check out the other topics for screen resolution, but am not really optimistic with that tack.

My "lspci -v"

00:09.0 VGA compatible controller: Silicon Motion, Inc. SM712 LynxEM+ (rev a0)
    Subsystem: IBM Device 01aa
    Flags: bus master, 66MHz, medium devsel, latency 64
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Capabilities: <access denied>

---

### Post by jasonrobert on 2009-12-27
oh yeah, mine is 

00:09.0 VGA compatible controller: Silicon Motion, Inc. SM712 LynxEM+ (rev a0)
    Subsystem: IBM Device 01aa
    Flags: bus master, 66MHz, medium devsel, latency 64
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Capabilities: <access denied>


when I installed, I used one of those cheap usb hard drive case things and installed ubuntu and xubuntu on my pc with the pc hard drive disconnected. I also booted up from the laptop hard drive (with ubuntu now on it) on my pc and it all worked fine. so I put the hard drive back into the thinkpad 240x and this problem happened... but this narrows it down to the problem only being with the display driver...

 I was wondering if this problem is to do with the xfce on xubuntu, as when I had ubuntu 8.04 on this laptop I never had this problem... so I installed lxde and the problem was still there, although it wasnt as bad, and as soon as you moved the mouse the icons disappeared. I may try to install xubuntu 8.04 to see if this problem is still there... 

cheers jason

---

### Post by jasonrobert on 2009-12-27
ok I have fixed it...

I went to applications > settings > xfce 4 settings manager

then in that go to the bottom of the window and select window manager tweaks....

then go to compositor, and enable display compositing.

worked for me anyway..

good luck!

EDIT: I have also realised that when I take the power lead off, the whole laptop goes very slow. I assume its something to do with the power saving, and the fact that the battery monitor doesnt read the correct percentage; it reads 50 %% all the time.

---

### Post by itachi1 on 2009-12-27
Sonafagun,  by Jove, that did it!   Mark this one "solved!"   I kept all the settings to "opaque" in the hopes that the effect won't slow the display down, but all the redraws and renderings are perfect.  As new versions of xfce come out, I might try turning it off to see if the bug is fixed, but the box is very usable now.

I haven't taken it off AC power yet, but I'll play with that in a bit.

Thanks for your excellent discovery and tweaking, and hopefully I can contribute something as significant in the future...

Best

---

### Post by mathuna on 2009-12-27
Flashing icons have nothing to do with the battery. You have a corrupted OS. If the laptop screen was flashing on and off you would suspect a hardware / electrical problem. If the icons are flashing on and off, and you can see a solid background (the desktop) then you have a serious problem with the OS. When you get weird behavior like this, a virus/malware/rootkit could be present or a corrupted registry. The easiest way to fix is migrate the data to a external hard drive, reload the OS from the disk you got with your system(or the rescue partition on your computer [hit F11 or F8 usually]), update the newly installed OS, scan the data on the external hard drive for viruses/malware with AV software (AVG free works great), and then move your data back on to your computer.
Hope that helps.
====================================
[yoostar](http://www.newsday.com/business/review-yoostar-is-a-movie-studio-in-a-box-1.1401673)
[wildlife paintings](http://www.davidshepherd.com)

---

### Post by mister_playboy on 2009-12-29
Corrupted registry?  AVG anti-virus?

You do know you're in the Ubuntu forums, right...? ;)

---

