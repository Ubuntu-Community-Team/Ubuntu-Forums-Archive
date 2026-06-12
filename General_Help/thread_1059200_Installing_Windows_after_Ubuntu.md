---
title: "Installing Windows after Ubuntu"
date: 2009-02-03
forum: General Help
---

### Post by BeLiSo on 2009-02-03
I have a laptop with Ubuntu on it. But I have some software for an Anatomy and Physiology class I can't seem to run through Wine or through a virtual XP install in VirtualBox.

I have my Windows install CD (non-OEM), and I'm hoping to install Windows on a small partition for mainly this purpose. If I put in my Ubuntu LiveCD and move my Ubuntu and swap paritions (now currently sda1 and sda2 respectively), and create an NTFS partition for Windows XP at the beginning of the drive (I'm assuming this would be sda3 despite its location), would I be able to install XP to this partition without overwriting Ubuntu? 

I know I would have to edit my Ubuntu fstab and GRUB menu and reinstall GRUB. This is not a problem. I just need to know if the above method would work.

Thanks!

---

### Post by mb_webguy on 2009-02-03
You're going to need a 12 or 15GB partition for XP.  *If* you can shrink your Ubuntu partition by that much, then go for it.  And this assumes that your Ubuntu partition is at the beginning of the drive.  However, I think you're probably going to end up having to reinstall Ubuntu.  Whatever you do, make sure you back up everything first, especially your /home directory.

---

### Post by Freezing Hot on 2009-02-03
Get one of those 32 or 64 gig USB drives and install Windows to that. Then go into your BIOS and switch the boot order so a USB drive boots before your HDD. Once you've done that, only plug in your USB drive when you need windows.

That's what I did with Ubuntu when I used my HDD solely for storage, I imagine it would work in your case.

---

