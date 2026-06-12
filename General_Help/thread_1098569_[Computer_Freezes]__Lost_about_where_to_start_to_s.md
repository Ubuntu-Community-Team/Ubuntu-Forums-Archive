---
title: "[Computer Freezes]  Lost about where to start to solve it"
date: 2009-03-17
forum: General Help
---

### Post by Nivoruna on 2009-03-17
I'm an under week Ubuntu newbie, after messing around for a few days [installing the new nVidia drivers, configuring pulseaudio etc following forum guides] I found myself freezing my computer every so often so I made a clean install of Ubuntu.

Now, just after reinstalling and upgrading using Update Manager I'm still having complete freezes every so often. I'm not sure what causes them, [the few last times time I was using transmission/sufing on the net and watching a movie]. Checking var/logs doesn't show anything at the time of the freezes the only message comes from /var/log/messages and it says -MARK-.

I did try to look at various forum post to see if there where similar problems but I found so many different reasons to freezes that I'm totally lost about where to start to solve mine.

The lspci shows:
> 00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:01.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
04:00.0 VGA compatible controller: nVidia Corporation GeForce 9500 GT (rev a1)
I'm using the 177.82 drivers and 2.6.27-11 kernel

Any help would be appreciated.

---

### Post by stanz on 2009-03-17
Soo, if you get to do another fresh install..
I wouldn't use update manager for awhile~ thats just me...
I'd update or make changes--slowly...one step at a time,
with time inbetween--using things awhile--to make sure its all good.
[U][B]
nVidia drivers[/B][/U] : be careful of those. Which ones ya using?
Did ya surf around here to check on others progress?

[Multimedia & Video]("http://ubuntuforums.org/forumdisplay.php?f=334") have 2 good sticky's to start with, and help
with watching movies and what ya might need installed to do that.

Let us know your progress !

---

### Post by Nivoruna on 2009-03-18
Thanks for posting, I'm using the recommended 177.82 drivers. 

Now the weird thing is that since I posted here I didn't have a single freeze, even though I have been doing the same stuff to see if I could narrow the reason of freezes. But I guess it's still to early to tell if all it's OK.

Well I did make a change, I realized that Ubuntu and XP were seeing only 3GB of ram and not the 4GB, so I went to the 64bit Ubuntu forum and found how I could change that, after enabling memory mapping it recognizes the full ram. No idea if it's related.

---

