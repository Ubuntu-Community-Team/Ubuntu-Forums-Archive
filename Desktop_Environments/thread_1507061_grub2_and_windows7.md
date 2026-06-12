---
title: "grub2 and windows7"
date: 2010-06-11
forum: Desktop Environments
---

### Post by eyelessfade on 2010-06-11
For some reason my hard drive names have been shuffled, ubuntu don't care, but chainloader +1 is now totaly wrong and grub-update can't spot the error.

hard drive on sata0 is windows with bootloader
hard drive on sata1 is linux with grub

unfortunately sata0 is now sde and sata1 is sdf.
In grub.cfg it is now:
```
menuentry "Windows 7 (loader) (on /dev/sde1)" {
        insmod ntfs
        set root='(hd4,1)'
        search --no-floppy --fs-uuid --set ea061f2c061ef971
        chainloader +1
}
```
but it should be (hd0,1). Anyone know how to fix this so update-grub sets this correctly ?

---

### Post by eyelessfade on 2010-06-11
also I don't seem to have a /boot/grub/device.map

---

### Post by eyelessfade on 2010-06-11
anyone?

---

### Post by oldfred on 2010-06-11
Do you have a bunch of flash drives plugged in and they became first?

Do see entire boot:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and click on # in edit panel(code tags) to make it easier to read when you post the results.txt.

---

### Post by eyelessfade on 2010-06-11
sda-sdd is a raid on a pci card. After updating to lucid this came first for some reason.

I have done a workaround with grub.d/40-custom, not pretty but it works

---

