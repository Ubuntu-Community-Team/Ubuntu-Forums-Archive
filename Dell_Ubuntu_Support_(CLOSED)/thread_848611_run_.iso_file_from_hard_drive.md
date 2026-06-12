---
title: "run .iso file from hard drive?"
date: 2008-07-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TimDaniels on 2008-07-03
My Dell XPS M1330 laptop's DVD burner is down temporarily, and I would like to use a Dell Gutsy Gibbon 4GB .iso file that has been downloaded to the Vista partition to install Ubuntu as a dual-boot.  Can the .iso file somehow be run from the hard drive instead of first burning it to DVD and then booting the installer from that?

TimDaniels

---

### Post by fackamato on 2008-07-03
> **TimDaniels said:**
> My Dell XPS M1330 laptop's DVD burner is down temporarily, and I would like to use a Dell Gutsy Gibbon 4GB .iso file that has been downloaded to the Vista partition to install Ubuntu as a dual-boot.  Can the .iso file somehow be run from the hard drive instead of first burning it to DVD and then booting the installer from that?

TimDaniels

First, why don't you get the latest version, Hardy Heron?

Download daemon tools, install it, and mount the .iso. You should be able to install Hardy using WUBI that way.

---

### Post by checksum_101 on 2008-07-03
Theres plenty of howto's on running an iso from usb.

I have a bootable hardy iso on my 8gb usb,just remember afterwardsto remove the reference to it in you fstab (the fresh install sets it up as the cdrom)

---

### Post by logos34 on 2008-07-03
> **TimDaniels said:**
> Can the .iso file somehow be run from the hard drive instead of first burning it to DVD and then booting the installer from that?


yep.

[https://wiki.ubuntu.com/Installation/FromWindows](https://wiki.ubuntu.com/Installation/FromWindows)
(->'CD image approach')

---

