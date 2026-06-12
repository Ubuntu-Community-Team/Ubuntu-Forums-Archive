---
title: "Google Earth 6.2 crashes in Xubuntu 12.04"
date: 2012-05-14
forum: Desktop Environments
---

### Post by scubscub on 2012-05-14
Hello, I just installed Google Earth 6.2 in my new Xubuntu 12.4 and it crashes as soon as I start to zoom in.

It used to work fine on my Lubuntu 11.10 before I upgraded.

I'm guessing the problem could be that I downloaded the 64 bit version -- I have a 64 bit computer but maybe there is some lost dependency -- I would remove this version of google earth and try the 32 bit, but I can't find out how to remove programs????

(the Software center does not list it anywhere as "installed" though I used that program (ubuntu software center) to unpack and install the deb file...)

---

### Post by rai4shu2 on 2012-05-14
Not sure what the problem is. Works fine here.

```
$ apt-cache policy google-earth-stable
google-earth-stable:
  Installed: 6.2.2.6613-r0
  Candidate: 6.2.2.6613-r0
  Version table:
 *** 6.2.2.6613-r0 0
        100 /var/lib/dpkg/status
$ uname -a
Linux genma-MS-7309 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by wilee-nilee on 2012-05-14
Have you installed some of the stuff mentioned here.

[http://www.cesareriva.com/archives/788](http://www.cesareriva.com/archives/788)

the lsb goes in every release running google earth.

---

### Post by scubscub on 2012-05-15
For some reason it seems that Ubuntu Software Center was not correctly installing the deb file from Google earth's download site.  Failed with both 64 and 32 bit versions -- zooming in, at some point the screen freezes, and a hard restart is the only way out.

I was able to uninstall with synaptic and ran the deb file again using GDebi, now it seems to be working fine.

---

### Post by BlinkinCat on 2012-05-18
Hi all,

For any other xubuntu users considering Google Earth then perhaps you may consider updating to xfce 4.10 as explained here -
[http://ubuntuforums.org/showpost.php?p=11947088&postcount=17](http://ubuntuforums.org/showpost.php?p=11947088&postcount=17)

I had no trouble downloading via the Software Center as explained here -
[http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html)

And here - [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

Of course I am not sure, but perhaps version 4.10 provides greater stability.

They are early days yet, but I was absolutely blown away with the result so far.

Cheers - :p

Edit : After 1 - 2 hours of browsing Google Earth I have had absolutely no problems. Some of the shots may be a little old, but I found it quite fun to visit some of my old haunts. There then remains the prospect of exploring the world.

---

### Post by scubscub on 2012-05-21
Oops, I marked this as solved -- if only!

But no...

So it worked once... I tried again and got the same fail, once you start to zoom in towards the earth the entire system freezes, with only a hard restart possible.

Because I had other instability issues I went for a clean install of Xubuntu 12.4. Then following BlinkinCat's advice, I upgraded to xfce 4.10, then made sure that lsb-core was installed (per BlinkinCat's last link).

Since then I've tried installing with both gDebi and USC, both to no avai.  Essentially I start zooming in and everything freezes, needing a hard restart.  Any ideas?

Could it be a hardware issue?  I have a Dell Inspiron N4110.  Guys, this worked in (Lubuntu) 11.10...

---

### Post by BlinkinCat on 2012-05-21
> **scubscub said:**
> Oops, I marked this as solved -- if only!

Hi,

Go to thread tools at top of page and select "mark this thread as unsolved" - :)

---

### Post by BlinkinCat on 2012-05-21
> **scubscub said:**
> Oops, I marked this as solved -- if only!

But no...

So it worked once... I tried again and got the same fail, once you start to zoom in towards the earth the entire system freezes, with only a hard restart possible.

Because I had other instability issues I went for a clean install of Xubuntu 12.4. Then following BlinkinCat's advice, I upgraded to xfce 4.10, then made sure that lsb-core was installed (per BlinkinCat's last link).

Since then I've tried installing with both gDebi and USC, both to no avai.  Essentially I start zooming in and everything freezes, needing a hard restart.  Any ideas?

Could it be a hardware issue?  I have a Dell Inspiron N4110.  Guys, this worked in (Lubuntu) 11.10...

I eventually had about four crashes (not in google earth) and as version 4.10 prevents reporting bugs I decided to go back to original 12.04 install. I can't say if crashes were due to 4.10 for sure (I think not in my case) but in any case I reinstalled google earth on new installation and all has been working smoothly. I'm sorry I can't shed any light on your problem. - :(

p.s. I assume you have 3D Buildings checked or don't you get down that far ?

---

### Post by scubscub on 2012-05-22
Well, since I've had the same error in both xfce 4.8 and 4.10, I suppose it is premature to dial it back...

I'm wondering about the window manager, if not the hardware acceleration.

What I should have said, for clarity, is not that Google Earth crashes but that it "freezes"...

Anyway, the one time was successful and marked this prematurely as "solved", I made it to street view, but since then I don't get anywhere near that, just a few zooms in towards the continents, then freezola...

---

### Post by rai4shu2 on 2012-05-22
Might be related to your video hardware and/or drivers. I have Xubuntu here, and I don't get any freezing or any other issue for that matter.

---

### Post by sparklyprgs on 2012-05-23
> **scubscub said:**
> Because I had other instability issues I went for a clean install of Xubuntu 12.4. Then following BlinkinCat's advice, I upgraded to xfce 4.10, then made sure that lsb-core was installed (per BlinkinCat's last link).

Since then I've tried installing with both gDebi and USC, both to no avai.  Essentially I start zooming in and everything freezes, needing a hard restart.  Any ideas?

Could it be a hardware issue?  I have a Dell Inspiron N4110.  Guys, this worked in (Lubuntu) 11.10...

I also had similar problem. Run Google Earth, search for something, automatically starts zooming in, it crashes (but not full freeze, just GE disappears).

I'm still not sure what the root cause of the problem was but heres what has made it more stable for my system. Do you use two screen at all? Or maybe even the laptop screen in tandem with external?

I run dual external screens, off a docked laptop that has DVI and VGA out. With the DVI and VGA plugged in **during boot** xubuntu very often won't boot properly (keeps rebooting over and over by itself). However when it does finally boot, most things are OK, but for example GE would fail like above, and maybe some other issues that I didn't identify. But if I boot *without* the DVI attached and only VGA attached, xubuntu boots everytime! Then once logged in I plug in the DVI, and use xrandr to activate dual screen mode - system runs stable, GE runs fine. No crashing. Really weird problem but this tweak worked for me!

PS : The Live CD also had the booting problem when both DVI and VGA were attached.

---

### Post by scubscub on 2012-05-23
Hmmm.  I use only my laptop monitor.  I have been having trouble with a USB mouse though, which causes a similar freezing of the screen, until I unplug the mouse.

---

### Post by scubscub on 2012-05-23
I'll start this thread over in Dell Support, and see what happens there.

---

### Post by scubscub on 2012-05-23
Well, I tried moving this thread to Dell Ubuntu Support, but it got "closed" because it's a duplicate of this one....

---

### Post by rai4shu2 on 2012-05-24
Well, let's see if we can't figure this out...

Do you have the AMD Radeon 6470M or are you using Intel video? If you're using AMD, then are you using the Catalyst driver or the open source driver?

---

### Post by scubscub on 2012-05-24
Thanks.  This is the basic Intel I believe, with nothing but what came on the install disc.  Here's what hwinfo says about it:

14: PCI 02.0: 0300 VGA compatible controller (VGA)
  [Created at pci.318]
  Unique ID: _Znp.8ViaXxRHh79
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: graphics card
  Model: "Intel VGA compatible controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x0116 
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x04d7 
  Revision: 0x09
  Driver: "i915"
  Driver Modules: "drm"
  Memory Range: 0xd0000000-0xd03fffff (rw,non-prefetchable)
  Memory Range: 0xc0000000-0xcfffffff (ro,non-prefetchable)
  I/O Ports: 0x4000-0x403f (rw)
  IRQ: 49 (1503803 events)
  Module Alias: "pci:v00008086d00000116sv00001028sd000004D7bc03sc00i00"
  Driver Info #0:
    Driver Status: i915 is active
    Driver Activation Cmd: "modprobe i915"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

---

### Post by scubscub on 2012-05-25
I installed ubuntu-desktop and restarted in that, to see if it would make any difference.  No dice.

(which is actually kind of a relief -- two minutes of dealing with Unity was more than I could handle...)

---

### Post by scubscub on 2012-05-25
Well, it turns out this is a known bug with 12.4 and certain systems.  More info here:

[http://productforums.google.com/forum/#!searchin/earth/freeze/earth/vUGP9-6UucM/hSUARdIC4ToJ]("http://productforums.google.com/forum/#!searchin/earth/freeze/earth/vUGP9-6UucM/hSUARdIC4ToJ")

and here:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/975689](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/975689)[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/975689]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/975689")

The solutions seem to be either updating to a newer kernel or running "sudo intel_reg_write 0x2120 0x1206800"...  I'm still debating which of these I want to mess with...

---

### Post by scubscub on 2012-05-25
"sudo intel_reg_write 0x2120 0x1206800" works beautifully, but only until you restart the computer....

---

### Post by lisati on 2012-05-25
> **scubscub said:**
> Well, I tried moving this thread to Dell Ubuntu Support, but it got "closed" because it's a duplicate of this one....

Starting a new thread isn't the same as moving a thread. The forum staff won't mind if you use the report abuse button [IMG]http://ubuntuforums.org/images/rebrand/buttons/report.gif[/IMG] and ask us to take a look, possibly moving the thread. Having said this, I'm not sure if this is a Dell-specific issue.

---

### Post by scubscub on 2012-05-25
Quite right, in fact it's good you didn't let me restart it, since it is not Dell specific, as it turns out.

All a learning experience :)

---

### Post by scubscub on 2012-05-26
Okay, here's the options for anyone with these problems as it currently stands:

1.  Go back to 11.10, it works.

2. use the "intel reg write" command given above, it works temporarily (is there a way to automate this at startup?)

3. there is a patch given on one of the websites listed above, for anyone comfortable with patching their kernel;

4. the correct patch has not yet made it into the kernel updates (as of 3.4 rc5), though presumably it will at some point.

---

### Post by jimmyco2008 on 2012-06-03
Has anyone tried Google Earth with the new Ubuntu 12.10 preview releases?

---

### Post by kennedyjch on 2012-06-09
> **scubscub said:**
> "sudo intel_reg_write 0x2120 0x1206800" works beautifully, but only until you restart the computer....

This worked for me to stop the crashing in stock 32 bit Ubuntu 12.04. Problem solved! Thanks!!!:)

---

### Post by scubscub on 2012-06-09
The problem though is that it is still a temporary fix, that has to be run each time you start the computer, or each time you are going to run Google Earth.  Quite likely, there are other programs that would have this problem as well.  Is there any way to make the change stick?

---

