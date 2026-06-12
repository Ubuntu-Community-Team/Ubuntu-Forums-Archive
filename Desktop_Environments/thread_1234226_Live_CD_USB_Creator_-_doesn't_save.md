---
title: "Live CD USB Creator - doesn't save"
date: 2009-08-07
forum: Desktop Environments
---

### Post by zebraneo on 2009-08-07
I am trying to create a Persistent USB Flash drive - flash drive 8GB, and it's not saving the information. Can someone tell me what I did wrong. I tried using the  Live CD USB Creator, and it doesn't save

default persist
label persist
  menu label ^Run Ubuntu Persistently saving changes back to USB
 kernel /casper/vmlinuz
append noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --

label live
  menu label ^Try Ubuntu without any change to your computer
  kernel /casper/vmlinuz
append noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --

label live-install
  menu label ^Install Ubuntu
  kernel /casper/vmlinuz
append noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash --
label check
  menu label ^Check disc for defects
  kernel /casper/vmlinuz
  append  noprompt boot=casper integrity-check initrd=/casper/initrd.gz quiet splash --
label memtest
  menu label Test ^memory
  kernel /install/mt86plus
label hd
  menu label ^Boot from first hard disk
  localboot 0x80

---

