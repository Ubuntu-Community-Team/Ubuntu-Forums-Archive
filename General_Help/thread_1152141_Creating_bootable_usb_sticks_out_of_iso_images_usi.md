---
title: "Creating bootable usb sticks out of iso images using 'dd'"
date: 2009-05-07
forum: General Help
---

### Post by nik_gr on 2009-05-07
Hello iam trying to create three casesQ

a) a bootable usb flash disk out of a win7 .iso image file with the latest build

i tried this already "dd if=./nt5boot.bin of=/dev/sdc"

and then copy the .win7 iso files to the usb stick but unfortunately it give me error saying

CDBOOT: Cannot Boot from cd

b) a bootable usb flash disk out of a floppy image file so i can try to update my mobo bios

"dd if=./odin1440.img of=/dev/sdc"

unfortunately when i try to boot from usb stick it says the it cant boot

c) restore win7's boot record that is broken in my /dev/sdb

"dd if=./nt5boot.bin of=/dev/sdb" but either this wont work

I have been told that all these the above can be accomplished by using 'dd' command
but something i seem to be missing or not doing correctly. Can you help me please?

Thank you very much, caus ethis is troubling me for days.

---

### Post by t0p on 2009-05-07
I don't know about dd.  But I can recommend that, if you want to create bootable usb sticks, you should use **UNetbootin**.  It's available through apt-get/synaptic, I believe.

---

### Post by nik_gr on 2009-05-07
> **t0p said:**
> I don't know about dd.  But I can recommend that, if you want to create bootable usb sticks, you should use **UNetbootin**.  It's available through apt-get/synaptic, I believe.

UNetbootin can only create bootable usb ssticks out of linux images or downlaod them fitst, not win7 iso images or floppy images.

---

### Post by boutch55555 on 2009-06-03
from that here : [http://www.blogsdna.com/2016/how-to-install-windows-7-from-usb-drive-without-windows-7-iso-dvd.htm](http://www.blogsdna.com/2016/how-to-install-windows-7-from-usb-drive-without-windows-7-iso-dvd.htm)
seems like you need to toggle the boot flag (witch can be done with gparted) a specify the ID of the key to update a file somewhere... are you sure you can't find a windows box to copy that windows image ??

---

