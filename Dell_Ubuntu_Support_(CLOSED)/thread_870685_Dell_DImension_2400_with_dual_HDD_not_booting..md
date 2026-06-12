---
title: "Dell DImension 2400 with dual HDD not booting."
date: 2008-07-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by palmgeek5394 on 2008-07-26
I cloned my old 40GB drive to my new 80GB Seagate, replaced the 40GB with the 80GB, and put the 40GB where a second CD drive would go. The 80GB master drive has Windows XP on it, and I installed Ubuntu 8.04 on the 40GB slave drive. When I restarted, I got "GRUB error 17", and I had to boot from the Live CD. I couldn't do anything to the 40GB drive from the live CD, so I just shut down and removed the 40GB drive, but it still wouldn't boot. But I can modify the 80GB drive, so what do I need to delete to allow the default bootloader to take over? :confused: If I need to attach either drive to another computer through USB, I have a cable for it (and power supply).
EDIT: And I also have a thread over at DesktopReview.com [here]("http://forum.desktopreview.com/showthread.php?p=2254933#post2254933") and Brighthand [here]("http://forum.brighthand.com/showthread.php?p=1699277#post1699277").

---

### Post by logos34 on 2008-07-26
Try installing grub to the mbr of 80 gb/windows drive (link in my sig).
You 'root' lines in menu,lst should be (hd**1**,x)

---

### Post by palmgeek5394 on 2008-07-26
Well, I used the Super GRUB thing to boot Windows because GRUB wouldn't start Linux. So now I'm thinking I'll just install Ubuntu to a 20GB partition on the 80GB drive and use the 40GB as a backup drive.

---

### Post by logos34 on 2008-07-26
Boot from the live cd and click on your root partition in the side pane of nautilus browser to mount (should do so at '/media/disk/').

cat /media/disk/boot/grub/menu.lst

Post it.  Oh, and also

sudo fdisk -l

---

### Post by palmgeek5394 on 2008-07-27
It didn't exist. And silly me, I installed it onto the 60GB laptop HDD I have connected via a cable to USB... But I just used the Windoze recovery CD to run fixboot and fixmbr, and it works now. I'll be off to install Ubuntu on the right drive now...

---

