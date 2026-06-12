---
title: "Dual boot problem"
date: 2008-03-09
forum: Dell  Ubuntu Support
---

### Post by HowHH on 2008-03-09
I was successfully running a dual boot system (Ubuntu 6.06 Win XP) on a beige box computer.  I decided to transfer the hard drive into a Dell Dimension 4500 that I had decommissioned from my office.  Ubuntu boots up fine, but Win XP resets the system during boot-up, even during safe mode. Pop the HD back into the old box and everything is fine.  Here is a copy of my GRUB:

title		Ubuntu, kernel 2.6.15-51-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-51-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-51-386
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows 95/98/Me
root		(hd0,0)
savedefault
makeactive
chainloader	+1


Any pointers as to where to start? Thanks.

---

### Post by sanmeetkanhere on 2008-03-09
try:

root hd(0,0)
makeactive
chainloader /ntldr

that works better sometimes

---

### Post by HowHH on 2008-03-10
Thanks for the response.  I found that the problems was a driver issue for Win XP, setting the IDE ATA/ATAPI controller to a standard dual channel IDE controller with the drive back in the old machine first.  With this plain vanilla driver, Windows can then at least boot up and then recognize the new hardware. I can't take credit for it though, the solution was here: [http://www.tweakxp.com/article37174.aspx]("http://www.tweakxp.com/article37174.aspx")

However, Ubuntu did this without a problem.  Just another reason for liking Ubuntu! ;)

---

