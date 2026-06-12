---
title: "Install linux on SD card"
date: 2008-03-01
forum: Dell  Ubuntu Support
---

### Post by james_f_hall on 2008-03-01
Anyone know how to install linux on an SD card for the Dell 1330? Resources or information I can find? Would I need to use the HDD as a bootloader still? I have a 4GB SD card that I would like to install most of the OS too, but mount part of the HDD as /home.

Thanks,

Jim

---

### Post by mrsteveman1 on 2008-03-01
Bad idea for a number of reasons.

Most SD cards aren't fast enough to run an OS from (especially swap, which might ruin the card), but also some of the controller chips laptops use for SD cards are extremely slow, the one in my HP dv1710us actually causes video to skip when the card is being written to, because it uses a LOT of system resources.

Second, most BIOS can't boot from these SD slots anyway, so you would have to boot from a hard drive with grub, and then tell the kernel to root from the SD card (it'll be something like /dev/mmcblk0p1).

A better idea may be to install Linux to a USB stick, a big one, and you can boot directly from the stick. I've done it quite a few times, i have a server that runs entirely from a 2gb fast USB stick (no swap tho).

---

### Post by jpittack on 2008-03-02
Take a look at booting to ram.  Jdong wrote a nice wiki.  [http://wiki.ubuntu.org/BoottoRam]("http://wiki.ubuntu.org/BoottoRam")

That should be it.  I think you might be looking for improved performance.  Something else to consider is DSLinux.  That is designed to run from an SD card, or what they call a frugal install.  Don't worry,its debian based.

---

### Post by james_f_hall on 2008-03-02
Thanks. I found some information at the ideastorm site that helped me. The SD memory I have is 133X (20MB/s) so it's plenty fast for just loading the OS.

---

### Post by jpittack on 2008-03-03
The sd memory might be 133x, but the connection needs to be as well.  I would suggest finding a way to test that.

---

### Post by mrsteveman1 on 2008-03-03
Typically the speeds those cards are rated for are only true in some devices.

Like i said, i have a fairly fast SD card in this laptop, but writing to it literally locks up video if its playing, slows the entire system down etc. I used to run firefox portable off of this SD card but it was incredibly slow and annoying.

The controller in this thing is a Ricoh PCI chip, so perhaps you can check on that and see what you have.

---

