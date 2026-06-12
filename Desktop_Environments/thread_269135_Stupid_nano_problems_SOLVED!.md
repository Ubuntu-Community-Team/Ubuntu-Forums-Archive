---
title: "Stupid nano problems: SOLVED!"
date: 2006-10-01
forum: Desktop Environments
---

### Post by brucevangeorge on 2006-10-01
Here is what I did to get my nano working properly. The iPod HOWTO did not work for me.

**1.** Installing Ubuntu using alternate CD. < This has the partition manager on it. The Live-CD may not work with this method.
**2.** While installing through alternate, make sure the iPod is connected so that it shows up in the partition manager. (it should be under sda,sdb,sdc)
**3.** Format the partition and install the system. DO NOT FORMAT THE IPOD. Only the partition that you want to install the system on. Leave the pod alone. If you did format it, reset the damn thing by formatting it again, except on a windows system. Then start over.
**4.** Install the system fully with the pod connected.
**5.** Install banshee or amarok.
**6.** Ipod should now work without any mounting errors, locking up... or any of that.


**_NOTES:_**


**1.** When I installed I did Ubunti minimal install and then installed only the GUI (aka Gnome, KDE). If it doesn't work, try that. More crap than needed might be installed in the system.. could conflict with the iPod. This is just speculation. Not tested since I don't have a problem with my iPod anymore!

**2.** Amarok is better than Banshee. If Banshee does not work, Amarok should.

**3.** Optional components if your ipod is not detected in banshee or amarok: libipoddevice0, ipodslave & all their dependencies.

**4.** When transferring music to your ipod, it should be in the same state as when you installed the system.

eg.  If the ipod was the only USB device connected while you installed Ubuntu... make sure it's the only USB device connected while transferring. I had a problem with this. I put a memory stick into my computer while the iPod was connected. Everything was fine until I started to transfer music through Amarok. It crashed in the middle of the transfer.

Typed command "dmesg" in the terminal and a whole bunch of FAT read/write errors came up. Then I restarted and connected ONLY the iPod. Worked like a charm.



_Aside:_

This entire process took me about 2 weeks of trial and error and reinstalling over and over. If anyone can tell me why this works, that would be great.

Also, if anyone did these steps (or a variation of) and it worked.. post here and I can put this in the HOWTO forum as a last resort for iPod owners.

---

