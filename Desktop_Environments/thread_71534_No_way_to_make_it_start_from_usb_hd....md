---
title: "No way to make it start from usb hd..."
date: 2005-10-03
forum: Desktop Environments
---

### Post by alex.zeta on 2005-10-03
:( 
I'm to sure i'm doing it perfectly, but with lilo I obtain a very slow sequence of dots as last 5 minutes before start booting, tried grub and it starts (before any other menu) with anoter sequence: L 99 99 99 99 99 99 99... and so on.

I thkink that is a lilo error message.. as if it's still present on the mbr..

Is there any way to be sure that grub is correctly installed on the mbr of the usb unit? I can't boot from that device, but still boot with the primary master..

Hope to be enough clear..and available to submit further details..
Thank you to everybody.
Alex - Italy

---

### Post by KingBahamut on 2005-10-03
Thats a Grub error I suspect. Did you install Grub on the mbr of the usb device?

---

### Post by alex.zeta on 2005-10-04
I -should- have done it, using the automatic (not expert) installation of the ubuntu cd.

The only thing I've done manually was to make an initrd.img file with usb modules, as described here: [http://ubuntuforums.org/showpost.php?p=118293&postcount=2](http://ubuntuforums.org/showpost.php?p=118293&postcount=2)

Thanks..
Alex

---

