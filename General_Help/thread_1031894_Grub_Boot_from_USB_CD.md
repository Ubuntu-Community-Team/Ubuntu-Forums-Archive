---
title: "Grub Boot from USB CD"
date: 2009-01-05
forum: General Help
---

### Post by Trzone on 2009-01-05
I took the USB810.iso image and copied the vmlinuz and initrd.gz file, renamed them as usb.vmlinuz and usb.initrd.gz all copied to the /boot which is located on the third partition according to gparted
But i get an initramfs error
the cd worked, but to the extent of my knowledge, this should work as well.
It gives me the error message about 3 mins into the loading stage
any suggestions?
my Grub entry is below
thanks!

title Ubuntu 8.10 Usb
root (hd0,4)
kernel /usb.vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper noprompt cdrom-detect/try-usb=true persistent quiet splash
initrd /usb.initrd.gz
boot

---

### Post by Tim Sharitt on 2009-01-06
I think this may help you: [https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

I have not used the Live CD method, but I have used the Alternate CD method a few times and it seems to work very well.

---

