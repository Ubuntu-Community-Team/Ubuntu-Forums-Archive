---
title: "Booting to USB Hard Drive"
date: 2006-04-30
forum: Desktop Environments
---

### Post by Geffers on 2006-04-30
I've recently started to understand various GRUB boot parameters such as vmlinuz and initrd etc and am now able to boot my hard drive installed ubuntu using a boot floppy.

I'm now becoming adverturous and am wondering about an ubuntu system installed to an external USB HD.

I recall previously installing a mandrake system to a USB drive but the USB drive was not recognised at boot time.

Does the GRUB Boot disk recognise USB (My laptop's BIOS doesn't support USB Boot) or is there an alternative method.

Geffers

---

### Post by ncappel1 on 2006-04-30
is this what you are talking about?
[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)

I hope this thread will help you.

If your bios doesn't support booting to usb, maybe you have to update it. I thought that was a standard thing, booting to usb?

---

### Post by Geffers on 2006-05-01
[QUOTE=ncappel1]is this what you are talking about?
[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)

I hope this thread will help you.

If your bios doesn't support booting to usb, maybe you have to update it. I thought that was a standard thing, booting to usb?[/QUOTE]

Looks like it will though it does look quite complicated :-? 

I have a 7 year old desktop running Win98 and a four year old laptop with XP, neither support booting to USB :( 

Geffers

---

### Post by Ramses de Norre on 2006-05-01
Wouldn't it be possible to install ubuntu on the external and grub on the internal? So that your bios needs to boot from the internal harddisk and grub makes the external boot. Or if you want to be able to take ubuntu out to other machines install grub on a floppy or cd-rom.
Just an idea though :p

---

