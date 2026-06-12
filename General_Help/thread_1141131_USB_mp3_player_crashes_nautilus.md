---
title: "USB mp3 player crashes nautilus"
date: 2009-04-28
forum: General Help
---

### Post by cmost on 2009-04-28
HI guys! Just installed Jaunty Jackelope (amd64 variant) after using Debian Testing/Sid for awhile and here's a show stopping bug I've encountered. I have a 4 GB iVO-Sound m220 MP3 player that acts like a USB mass storage device in Linux. Typically, I plug it in, drag and drop songs, eject and go do my workout. In Ubuntu, however, plugging this device in crashes Nautilus to the max (all desktop icons and any open windows disappear.) Any attempt to try and restart nautilus by typing 'nautilus' in gnome-terminal emits the following error:

cmost@cmost-ubuntu64:~$ nautilus
Initializing nautilus-open-terminal extension
Segmentation fault
cmost@cmost-ubuntu64:~$

If I unplug the device, nautilus restarts fine.

Here is the relevant output of dmesg
.
.
.
[ 1861.373247] sd 5:0:0:0: [sde] 8010752 512-byte hardware sectors: (4.10 GB/3.81 GiB)
[ 1861.374115] sd 5:0:0:0: [sde] Write Protect is off
[ 1861.374121] sd 5:0:0:0: [sde] Mode Sense: 00 00 00 00
[ 1861.374125] sd 5:0:0:0: [sde] Assuming drive cache: write through
[ 1861.375358] sd 5:0:0:0: [sde] 8010752 512-byte hardware sectors: (4.10 GB/3.81 GiB)
[ 1861.399946] sd 5:0:0:0: [sde] Write Protect is off
[ 1861.399957] sd 5:0:0:0: [sde] Mode Sense: 00 00 00 00
[ 1861.399962] sd 5:0:0:0: [sde] Assuming drive cache: write through
[ 1861.399973] sde:
[ 1861.427869] sd 5:0:0:0: [sde] Attached SCSI removable disk
[ 1861.428062] sd 5:0:0:0: Attached scsi generic sg6 type 0
[ 1861.434504] sr2: scsi-1 drive
[ 1861.434734] sr 5:0:0:1: Attached scsi CD-ROM sr2
[ 1861.434869] sr 5:0:0:1: Attached scsi generic sg7 type 5
[ 1861.669223] usb 1-2.1: reset high speed USB device using ehci_hcd and address 6
[ 1867.051308] nautilus[26017]: segfault at 316300c ip 00007f853bbb3409 sp 00007f853b57ccb0 error 4 in libbrasero-media.so.0.1.1[7f853bba1000+21000]
[ 1873.937228] usb 1-2.1: reset high speed USB device using ehci_hcd and address 6
[ 1874.052228] nautilus[26202]: segfault at 1824000 ip 00007f759b6265a1 sp 00007f759b612cb0 error 4 in libbrasero-media.so.0.1.1[7f759b614000+21000]
cmost@cmost-ubuntu64:~$

Any help on sorting this problem out? I'd really like to use my MP3 player! Since a lot of people have these, Ubuntu's inability to use them properly is a show stopper in my opinion.

---

### Post by kpkeerthi on 2009-04-28
Perhaps not a fix for your problem. As a workaround, you could try using [thunar]("http://thunar.xfce.org/index.html") to drag and drop files to your player. Its very light and should not pull a lot of dependencies.

To install:
```
sudo apt-get update && sudo apt-get install thunar
```

To open: Press ALT + F2 and enter **thunar**. I should also be in the menu somewhere but don't remember at the moment.

And for the nautilus, I suggest you report a bug in launchpad.

---

### Post by cmost on 2009-04-28
I did a search in launchpad and someone has already reported this as a bug.  I really hope it gets fixed.  As to your suggestion of using Thunar, I'll try that.  Alternately, what do you think about trying to hardwire the media player to a fixed mount point in /media using /etc/fstab?  Maybe it's worth a shot.

---

### Post by jts0803odon on 2009-05-07
Any luck with fstab? I tried it, but Nautilus still crashes with any storage device in usb. Wireless devices (mouse) work fine, though. Apport hasn't been able to submit to launchpad yet (unrelated, temporary issue) so I'm just looking around for other answers. Thanks for posting on this. 

I should note, though, that Nautilus will run after a crash, and draws the desktop even after the iPod or flash drive is removed, in my case, during the same session.

---

