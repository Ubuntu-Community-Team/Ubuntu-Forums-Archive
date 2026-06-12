---
title: "Boot multiple Ubuntu LiveCDs on a usb stick"
date: 2009-06-08
forum: General Help
---

### Post by 6x9=42 on 2009-06-08
I was setting up a multiboot usb stick to boot system rescue cd, clonezilla, etc as well as live cds of several Linux distros, but I encountered problems when trying to put Ubuntu Jaunty and Linux Mint (based on Ubuntu) live cds on the same usb stick. In my setup, Ubuntu is on a lower-numbered partition than Linux Mint.

I used the built-in function to setup the Ubuntu live cd partition. I used Unetbootin to setup Linux Mint live cd. Using grub with chainloader command I could boot into Ubuntu live cd just fine, but I couldn't do so with the Linux Mint partition. I then tried loading the kernel and initrd directly from grub, and while it appears to boot, for some strange reason after the Linux Mint splash logo, it boots into Ubuntu... I think it's something to do with the boot=casper kernel option.

Does anyone know why booting the Linux Mint partition would seek out the Ubuntu partition instead, and how I can fix it? I think it would be nice to be able to put multiple live cds of Ubuntu-based distros on the same usb stick, but now it looks like I have to put them on separate usb sticks?

btw, I found another post here mentioning a similar experience, but there were no answers.

---

### Post by 6x9=42 on 2009-06-21
*bump* 20 views and no one knows? Is this an issue for the casper developers, or something else?

---

