---
title: "Dell Mini 12 @ Ubuntu 9.04 LPIA"
date: 2009-05-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mencargo on 2009-05-08
Hi there.

I have tried:
Ubuntu 9.04 Netbook Remix - Slowest behaviour ever!
Ubuntu 9.04 Desktop i386 - Much better but still very slow
Ubuntu 9.04 Desktop lpia - Better, doubled battery life but still slow.

Intel GMA 500 graphics it's a nightmare, I think I'm currently with vesa drivers at 1240x768, which isn't the native resolution, 1280x800.

Besides that, it comes with Braodcom BCM 4312 chipset, a special low-powered chipset that I can't get to work at monitor mode.

In conclusion, I'm not a happy Dell customer.

LPIA is the way every Intel Atom powered Netbook should perform best and 9.04 is the newest Ubuntu version.

Still no support for Poulsbo chipset?
Someone know how to get this wireless working at monitor mode?

---

### Post by mencargo on 2009-05-09
Ok, I just brought an external Realtek RTL8187 and works great at monitor mode, so, although it would be nice to do it with the internal nic, video driver it's all I need to call it resolved.

---

### Post by tyroeternal on 2009-05-12
I just posted in another related thread about how to get video up and working for intrepid.  Jaunty is still to be seen, however.  That post also can direct you to the mega-thread going about the mini 12 and the latest efforts to get it working properly.

[http://ubuntuforums.org/showpost.php?p=7265935&postcount=11](http://ubuntuforums.org/showpost.php?p=7265935&postcount=11)

---

### Post by mencargo on 2009-05-12
Ok then, I'm on my way dowloading the usb cdimage file from:

[http://cdimage.ubuntu.com/releases/8.10/release/ubuntu-8.10-umpc-i386.img](http://cdimage.ubuntu.com/releases/8.10/release/ubuntu-8.10-umpc-i386.img)

Why can we install the files from [the wiki]("http://gma500.wiki-site.com/") at Jaunty?

Can this be ported? What's the problem with Jaunty LPIA supporting this?

---

### Post by mencargo on 2009-05-12
Well UMPC version didn't work, I'm dowloading LPIA 8.10 right now, or show I download i386?

---

### Post by tyroeternal on 2009-05-13
Installing intrepid drops you to a command line and then you will have to use an ethernet connection (unless you know how to use wireless on the command line) to update and add repos.  The reason that the files form the wiki cannot be used with jaunty is because they do not work with the newer kernel.

There seem to be two new developments over the course of the past day or so:

#1  An update (I think a kernel update) has gone through with Intrepid and made the video not work anymore.  ( -rant- After I just got things half-way working for me an upgrade broke it!  This is so frustrating.)  I've not heard any report of progress on getting it working, but it has only been a day or so.

#2  I have yet to test it, but there are reports that a new 2d driver has been pushed out on a ppa (linked in the quote) that will get jaunty video working (if only in a basic way so far)!  Here is the quote:

> **matthiasak said:**
> xserver-xorg-video-psb - 0.31.0-0ubuntu1~904um1 

at [https://edge.launchpad.net/~ubuntu-mobile/+archive/ppa?field.name_filter=psb&field.status_filter=published&field.series_filter=any](https://edge.launchpad.net/~ubuntu-mobile/+archive/ppa?field.name_filter=psb&field.status_filter=published&field.series_filter=any)

new xserver 2D drivers just went live! We're almost there! now we need the opengl (3D) and DRI support, and we'll be up to date with ... well... wow.... hard to believe our struggle is almost over...

who wants to toss the ring in the lava :)

I think I'm going to plunge-in, run the update from Intrepid to Jaunty and I will let you guys know how it works in ~24 hours. 

Until tomorrow, ciao

Tonight I am going to be installing Jaunty (again) to test this out.  I can post back and let you know how it goes.  You should definitely follow along with progress on the thread I quoted from above.

---

### Post by mencargo on 2009-05-13
Great!

Just in time because Intrepid LPIA didn't work either!!!
Can't find the kernel for lpia, installation stops and it's just another headache to get it working...

Also downloaded the daily release for UNR 9.10 and it's broke.

Back to Jaunty, luckily I still have the image, that PPA driver is compatible for both LPIA and i386?

I'll report back.

---

### Post by tyroeternal on 2009-05-13
Just a quick note:  I was having problems with my installations just stopping as well.  I found that if I pressed a key and waited for a minute or two, things would start moving again.  Some users have said to use enter, escape, a few others.  Just pick a luckey key!  [mine is caps lock double pressed] :P

Also, there were some issues with intrepid freezing while it was working... and what a short time it was.  Pressing the power button seemed to be the magic bullet for that lockup issue.

Best of luck!

---

### Post by mencargo on 2009-05-13
Report:

I dowloaded the [Ubuntu Jauty Jackalope 9.04 LPIA NetBoot image]("http://ports.ubuntu.com/ubuntu-ports/dists/jaunty/main/installer-lpia/current/images/netboot/mini.iso") (10Mb!)

Boot from USB with [UNETBootIn]("http://unetbootin.sourceforge.net/")

This install downloads your selected software packages files from internet so you need ethernet access, if you prefer predownloading all files, choose the [normal CD image]("http://cdimage.ubuntu.com/ports/releases/9.04/release/ubuntu-9.04-alternate-lpia.iso")

Installed fresh, Ext4 without relatime, then added PPA sources:

/etc/apt/sources.list
```
deb http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu jaunty main
```

Performed a full upgrade and restarted the system, nothing.

Drivers from PPA where installed but I don't know if they are been used, how do I check this?

Other good news, seems that new 2.6.30 kernel will [improve intel graphics performance]("http://beranger.org/v3/wordpress/2009/05/04/jaunty-kernel-2630-fixes-the-intel-video/") (or get them back to normal).
Althought it does not specify Poulsbo chipset, we may have an official solution soon, remember this PPA packages are only 2D.

---

### Post by tyroeternal on 2009-05-13
Well, for starters, the intel graphics performance is in reference to some regressions that were introduced which do not affect the GMA 500 chipset at all.  I'm not sure why that person was surprised, because the issue was relatively widely known to be a problem with code that got into the kernel and is currently being worked on.

Hopefully I can post back in an hour or so about my results with jaunty.

---

### Post by tyroeternal on 2009-05-13
I've got a working Jaunty system!

@ mencargo: are you sure that the xserver-xorg-video-psb package was installed?

```
sudo apt-get install xserver-xorg-video-psb
```

---

### Post by mencargo on 2009-05-14
LOL, I missed that, works perfect! Thanks!

Also checkout this guides to optimize battery and performance:
[http://ubuntuforums.org/showpost.php?p=6418463&postcount=10](http://ubuntuforums.org/showpost.php?p=6418463&postcount=10)
[http://wiki.geteasypeasy.com/How_to:_Reduce_Disk_Writes_to_Prolong_the_Life_of_your_Flash_Drive](http://wiki.geteasypeasy.com/How_to:_Reduce_Disk_Writes_to_Prolong_the_Life_of_your_Flash_Drive)

I'm specially interested at mounting directories as tmpfs, some posts suggest /tmp/ only.
Adding noatime should benefit too.

Currently:
/tmp/ (1Mb)
/bin/ (5.5Mb)
/sbin/(6.6Mb)
/etc/ (8.0Mb)
/lib/ (95Mb)

/sys/ (157Mb)
/var/ (181Mb)

So I would guess tmp, etc and lib should work.
Any expert on this?

Memory load idle: 250Mb

While seeing System Monitor, I noticed this:
CPU load idle:
CPU1 = 40%
CPU2 = 30%

What's up with that?

---

### Post by tyroeternal on 2009-05-14
As far as optimising for a flash drive goes, you do not need to if you have a mini 12... you do not have a flash drive.  Using noatime may give you some small performance gains, but should not be a major issue.

Optimising your kernel would be a good idea if you are interested in getting the best performance out of your system.

Mounting directories like the firefox cache to ram will cut down on the ram available to the rest of your system, but it is not a catch all solution.  Mounting important directories with tmpfs is a BAD idea.  When the system reboots everything in that directory is lost.  This is an acceptable thing for /tmp but not the other directories you mentioned.

---

### Post by mencargo on 2009-05-14
I know mini 12 doesn't have SSD, but it has a 4200rpm hard drive. =(
And about kernel optimization, I installed lpia version, so I guess that's the closest kernel I can get, right?
What can I do to optimize it?

---

### Post by tyroeternal on 2009-05-14
Build a new kernel that has many of the extra items pulled out.  I'm not sure exactly how much further the lpia version can be trimmed, but as an i386 user there is a lot of trimming that can/will be done to my kernel to trim it down.

---

