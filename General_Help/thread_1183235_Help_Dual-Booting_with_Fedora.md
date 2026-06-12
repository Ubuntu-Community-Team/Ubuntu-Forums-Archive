---
title: "Help Dual-Booting with Fedora"
date: 2009-06-09
forum: General Help
---

### Post by ghindo on 2009-06-09
I'd like to dual boot with Fedora 11, but I'm unsure how to.  My setup at the moment is 64-bit Karmic with ext4 / and /home partitions.  I recently installed GRUB2 as well.  I still have a little hard drive space left over, and I would like to install 64-bit Fedora alongside my Ubuntu installation, sharing the /home partition and using Ubuntu's bootloader.

What would be the best way to do this?  I'm sort of at a loss.  Thanks. :popcorn:

---

### Post by ghindo on 2009-06-10
Bump!

---

### Post by Bigtime_Scrub on 2009-06-11
I found something that might help you. [http://www.go2linux.org/dual-boot-two-linux-distros-debian-and-mandriva]("http://www.go2linux.org/dual-boot-two-linux-distros-debian-and-mandriva")

The key is when you install Fedora you do not format /home. You will have a single single root partition and a common swap partition. This way you can share common files from each distro.

Here is another how to guide that I hope helps. [http://www.iball.id.au/node/26](http://www.iball.id.au/node/26)

It is not Fedora/Ubuntu specific but Linux in general and should work.

---

### Post by ghindo on 2009-06-11
> **Bigtime_Scrub said:**
> I found something that might help you. [http://www.go2linux.org/dual-boot-two-linux-distros-debian-and-mandriva]("http://www.go2linux.org/dual-boot-two-linux-distros-debian-and-mandriva")

The key is when you install Fedora you do not format /home. You will have a single single root partition and a common swap partition. This way you can share common files from each distro.

Here is another how to guide that I hope helps. [http://www.iball.id.au/node/26](http://www.iball.id.au/node/26)

It is not Fedora/Ubuntu specific but Linux in general and should work.Wow, that's a lot more complicated than I would have thought.  Thanks for the links!  It will certainly give me a challenge. :)

---

