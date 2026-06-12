---
title: "hotplug freezing and kernel 2.6.14"
date: 2005-11-14
forum: Desktop Environments
---

### Post by Heretic09 on 2005-11-14
Anyone know if compiling a vanilla 2.6.14 kernel has solved the hotplug freezing problem that has plagued a lot of laptops?

---

### Post by nmizar on 2005-11-28
Hi,

yesternite, I tried to install **Breezy** on my brand new _Fujitsu Amilo 1451_.  After the reboot which goes on in the middle of the configuration process, the system got frozen while "*starting hotplug subsystem*". My workaround has been a) installing **Hoary** and [FONT="Courier New"]apt-get dist-upgrade[/FONT] to Breezy (changing 'hoary' by 'breezy' on /etc/apt/sources.list). Hoary worked OK but, once upgraded, the hotplug stuff occurred again!. If also noticed that if that step is skipped (Ctrl-C at the appropriate time) the system (usually) goes up OK. I haven't found any relevant (TTBOMK) informatio in [FONT="Courier New"]dmesg[/FONT].

Any ideas would be (enormously) welcome,

Nacho

P.S. I think it's something to do w/the sound card, though I dunno how to fix it

---

### Post by nmizar on 2005-11-28
Hi, again!

well, it's not just 'hotplug', which freezes my breezy; same with PCMCIA,...

The only way to start the system is chosing (grup startup menu) 2.6.10-5 instead of 2.6.12-10. Looks like my dist-upgrade added the newer kernel image and this one ain't working.

Any ideas?

Cheers,

                Nacho

---

### Post by wrtrdood on 2005-11-28
[QUOTE=Heretic09]Anyone know if compiling a vanilla 2.6.14 kernel has solved the hotplug freezing problem that has plagued a lot of laptops?[/QUOTE]

It's probably not "freezing" just taking forever.  Did for me and, yes, an updated kernel makes a significant difference.  Follow the the HOWTO posted here: [http://ubuntuforums.org/showthread.php?t=84174&highlight=2.6.14](http://ubuntuforums.org/showthread.php?t=84174&highlight=2.6.14)

I did and it changed my boot time from over seven minutes to well under three and though there's a pause at hotplug, it's nothing like before.

---

### Post by Heretic09 on 2005-11-28
I left my laptop sitting at the "starting hotplug" step and it took a long time and then it shut itself off. If upgrading to a new kernel works i'm all for it. I just don't want to put a lot of effort into it and then have the same problem on the next reboot.

The weird thing is it doesn't do it all the time. Sometimes it boots up fine and the hotplug step takes it only a couple of seconds other times (most of the time) it just sits there. about 1 out of 4 attempts boot up fine.

---

### Post by TTL on 2006-01-01
I have the same problem and discovered the following:
Hotplug works always perfectly when ** no ** USB device is connected.
If I connect a USB device I get the same behavior as you reported.
I have tested it with my USB mouse, MMC cardreader, multicardreader, MP3 player and camera its always the same. Moreover I discovered that when I boot with the noapic option my PC stops booting much before the "hotplug service" when a USB device is connected complaining that some modules could mot be loaded. Again without a USB device booting with noapic works well.

Hope someone could help
TTL

---

