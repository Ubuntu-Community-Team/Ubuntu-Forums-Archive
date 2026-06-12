---
title: "Boot ubuntu ISO from HDD?"
date: 2009-05-21
forum: General Help
---

### Post by b@sh_n3rd on 2009-05-21
Hi, i was wondering..If I download an Ubuntu ISO, LiveCD or Alternate CD, is it possible to boot a PC with that from the hdd? coz I've a PC that doesn't have an operational CD-ROM drive and I have to keep shifting my cdrom drive to this PC whenever I want to install something...I know it's possible to update a system with the Alternate CD ISO from the HDD...I mean, bootup...

---

### Post by snowpine on 2009-05-21
Yes; the program you want to use is called Unetbootin: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by b@sh_n3rd on 2009-05-21
Hi, thanks for your reply...I'm gonna try Unetbootin later on. Thanks :D

---

### Post by b@sh_n3rd on 2009-05-24
OK, I just thought I'll try Gentoo on a certain PC.. I got Unetbootin and tried to make an HDD bootable. I got a LiveCD ISO image for this. The HDD partition I want to use is /dev/sdb1. The only way I see of setting up the image on this drive is by selecting "Show All Drives", I used this method and setup the ISO on the HDD twice, but without any success. When booting from that partition, GRUB replies, "Missing Operating System" and then boots from my local Jaunty installation. On unetbootin, If I select "Hard Disk" under "Type:", I can only select "/"...How can I select sdb1 and set it up like a LiveCD? Thanks...

---

