---
title: "hfs under i386 ubuntu (not ppc nor macintel)"
date: 2006-08-30
forum: Desktop Environments
---

### Post by liamk101 on 2006-08-30
Hi,

I would like to know if it is possible to format two usb disks with this filesystem under a pc running ubuntu. My boss is going to buy a macbook and needs to backup all the information from his pc into these usb disks.

---

### Post by s_groening on 2006-08-31
I understand that you need to backup files from an Ubuntu installation to a USB disk and then transfer those files to the Mac Book afterwards.

This is most easily achieved if you take the reverse approach and do the formatting of the drive(s) on the Mac Book after it's been setup.

It may be necessary to format the disk by actually 'partition' the disk. In 'Disk Utility', click on the drive name (e.g. 'TOSHIBA MK6022GAX Media') and click 'Partition' on your right hand set of panes. Simply create a single partition, clicking on the 'Options...' button to choose the 'Apple Partition Scheme' which is native to Power PC Macs and suitable for external disks and also suitable for e.g. Ubuntu to play with...

Choose 'HFS+ (Journaled)' as your filesystem of choice and you're almost ready to attach it to the PC running Ubuntu.

Open Synaptics packet manager on Ubuntu and install hfsplus utils (try searching for 'hfs' with both universe and multiverse repositories enabled, it should bring you in luck!) in order to let the disk mount on Ubuntu.

That ought to be it! enjoy ;)

---

