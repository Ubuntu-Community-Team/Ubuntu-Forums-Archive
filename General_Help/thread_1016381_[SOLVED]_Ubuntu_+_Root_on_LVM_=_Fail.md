---
title: "[SOLVED] Ubuntu + Root on LVM = Fail"
date: 2008-12-19
forum: General Help
---

### Post by Jordanwb on 2008-12-19
After starting up the 64 Bit Desktop CD, I installed LVM so that I could install Ubuntu onto a LVM volume. I set up two LVM volumes, one for root and one for home (both 10G and using ReiserFS), with /boot on a 64M ext3 partition. Now after installing Ubuntu I rebooted. I got the grub screen and selected Ubuntu 8.10. I get the splash screen with the scanning orange bar. Then the screen goes blank. One time I got some text from the initramfs saying it couldn't find /dev/system/root. Any ideas?

It seems that the initrd image doesn't include support for root on LVM.

---

### Post by jerome1232 on 2008-12-19
I've always just installed from the alternate install cd, which allows you to setup lvm during the install process. Everything worked fine with an encrypted lvm root. 

I wouldn't know what to look at to get your current setup working though.

---

### Post by Jordanwb on 2008-12-19
Yeah I could but I see no reason as to why the initrd of the desktop cd cannot find the LVM volumes whereas the Alternate installer does. I wish the Desktop CD included native LVM support, it would take all of an extra Meg.

---

### Post by RealPSL on 2008-12-20
I guess the idea behind leaving that out is the Desktop CD really keeps things ultra simple even if LVM was included it would be unlikely they would change the install to be able to use it. 

Going back to your problem though is there any chance we can see the kernel line from your /boot/grub/menu.lst. It might be as simply as having the right entry in there or a running update-initramfs. The only problem is if the update-initramfs is what is required we may still need the alternate CD to boot recovery to recognize the LVM and run it.

---

### Post by Jordanwb on 2008-12-20
It seems that the Alternate CD and the Desktop CD's kernels aren't the same. My Asus P5QL Pro motherboard has an Atheros chip, whose driver is experimental, the Desktop CD has the module for the chip but the alternate installer does not.

---

### Post by Jordanwb on 2008-12-20
```

default		0
timeout		10

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		ee0fda31-4aa6-4dde-9ac7-2b3f21fefdf8
kernel		/vmlinuz-2.6.27-7-generic root=/dev/mapper/system-root ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ee0fda31-4aa6-4dde-9ac7-2b3f21fefdf8
kernel		/vmlinuz-2.6.27-7-generic root=/dev/mapper/system-root ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ee0fda31-4aa6-4dde-9ac7-2b3f21fefdf8
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

I removed "quiet splash" and the kernel does detect the drives but I don't see anything about scanning for LVM volumes. I suspect that the Desktop's initrd image does not contain code to activate LVM. I remade an initrd image using update-initramfs but that didn't help.

---

### Post by Jordanwb on 2008-12-20
I was so close but so far. After installing in the Desktop CD, I remounted all file systems including /dev and /proc. I chrooted into my install and ran "apt-get install lvm2". It updated the initrd image with LVM support and it works.

---

