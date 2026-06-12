---
title: "Ubuntu Live USB | Add Nvidia drivers"
date: 2013-02-01
forum: Desktop Environments
---

### Post by niv3d on 2013-02-01
Hello all! I am brand new to the forums and am having the typical Nvidia driver issue's. I have a Nvidia GT 630 and when booting from a live CD or USB I am getting a blank screen. I can resolve this buy editing the boot with nomodeset. However the nomodeset drivers aren't very good and id rather not have to do this at every boot. I have installed Ubuntu prior to this and am able to activate the Nvidia proprietary drivers within Ubuntu installed and not running live and everything works fine. However my plan is to run Ubuntu on a live USB 3.0 and I was wondering if there is a way to somehow edit the .iso to have the Nvidia Proprietary drivers or the Nvidia drivers needed from their site for when I run the live USB.

Thanks for any input! I have searched this topic over and over and cannot find a direct solution.

Devin

---

### Post by bogan on 2013-02-01
Hi!, **niv3d**,

If you are going to routinely run from a USB Ram stick, or external SSD/HDD then you do not want it to be a Live/Usb but a normal install.

Do the install without proprietary drivers, then boot from it [ with nomodset entered using edit mode in the Grub menu, if needed at first boot ] then update and make sure 'linux-headers-generic' is installed, before installing the video driver you want, if Nouveau is not sufficient.

You CAN squeeze a full Ubuntu 12.10 onto a 4Gb stick, but 8Gb is better, more if you are going to install a lot of programs.

But be prepared for some things to be slow, especially if your PC is not modern.

In 12.10, running Software Updater, the 'Loading Software List' process takes about 4 secs on the HDD, and nearer 55 secs on the USB.

Loading 12.10, from the same USB, on a 7 year old PC, takes 1min 15 secs compared with 35 secs on a 3 year old one, which is almost the same as from the HDD. [That is timing from Grub Menu to Login prompt.]

Chao!, **bogan**.

---

### Post by niv3d on 2013-02-01
> **bogan said:**
> Hi!, **niv3d**,

If you are going to routinely run from a USB Ram stick, or external SSD/HDD then you do not want it to be a Live/Usb but a normal install.

Do the install without proprietary drivers, then boot from it [ with nomodset entered using edit mode in the Grub menu, if needed at first boot ] then update and make sure 'linux-headers-generic' is installed, before installing the video driver you want, if Nouveau is not sufficient.

You CAN squeeze a full Ubuntu 12.10 onto a 4Gb stick, but 8Gb is better, more if you are going to install a lot of programs.

But be prepared for some things to be slow, especially if your PC is not modern.

In 12.10, running Software Updater, the 'Loading Software List' process takes about 4 secs on the HDD, and nearer 55 secs on the USB.

Loading 12.10, from the same USB, on a 7 year old PC, takes 1min 15 secs compared with 35 secs on a 3 year old one, which is almost the same as from the HDD. [That is timing from Grub Menu to Login prompt.]

Chao!, **bogan**.


Ahh ok that makes sense! Thank you very much for your reply sir! I DO have 2 ssds on my machine as well as an HDD would it be wise of me to just install Linux rather than running it live? One ssd has windows 8 on it and I have heard what a pain it can be to install Linux on the same system as windows 8. Although they would be on separate drives...

---

### Post by bogan on 2013-02-01
Hi!, **niv3d**,

Unless you want to be able to transfer the USB installation to other computers, I would be inclined to put ubuntu on the other SSD from that with Windows on it.

Then set Bios so the Ubuntu SSD has priority, and you can choose from the Grub menu which to actually boot from. If needed you can still force a Windows boot from the Bios boot menu.

Chao!, **bogan**.

---

