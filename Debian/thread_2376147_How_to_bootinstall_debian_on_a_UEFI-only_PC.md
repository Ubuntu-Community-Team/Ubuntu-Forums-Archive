---
title: "How to boot/install debian on a UEFI-only PC?"
date: 2017-10-30
forum: Debian
---

### Post by mchammer98 on 2017-10-30
I downloaded an image of debian 9.2.1 amd64 to a usb drive and am trying to boot debian from it in the BIOS menu.  However, my computer is a UEFI-only Lenovo Ideapad 100S with Windows 10.  

I have disabled Secureboot, and when I enter the boot menu there is no option to boot from usb.  I am able to boot TAILS from a different usb so the usb is not the issue.  Is there any way for me to boot and install debian os on my computer?  Are there any changes I can make to the file to allow it to boot on UEFI (I have no option to change to legacy boot)?

Thanks for the help

Edit: I used rufus to burn the iso image to the usb

---

### Post by RobGoss on 2017-10-30
>  I downloaded an image of debian 9.2.1 amd64 to a usb drive and am trying to boot debian from it in the BIOS menu. However, my computer is a UEFI-only Lenovo Ideapad 100S with Windows 10.  

You cannot just download the Debian ISO to a USB thumb drive, it needs to be burned using one of the appropriate tools. Try using [Rufus ]("https://rufus.akeo.ie/")to create the bootable USB. I don't know Lenovo that well but from what I have seen here on the forums Ubuntu runs fairly well and should not be to hard to get installed

---

### Post by QIII on 2017-10-30
Moved to Debian

---

### Post by mchammer98 on 2017-10-30
I used rufus to burn the image and create a bootable usb

---

### Post by RobGoss on 2017-10-31
Are you able to access the BIO's and set the USB as first boot?

---

### Post by oldfred on 2017-10-31
While a 64 bit system, it is configured with 32 bit UEFI.
Back when they did this Linux did not have 32 bit UEFI, so they wanted a Windows only system like an Apple iPad.
But now there is 32 bit UEFI. Older threads discuss compliling your own, but you just need to download bootia32.efi and use it rather than the 64 bit version bootx64.efi to boot installer. And then use 32 bit UEFI to boot. 

 LENOVO Ideapad 100S Laptop  32 bit UEFI bootia32.efi
[https://ubuntuforums.org/showthread.php?t=2350606](https://ubuntuforums.org/showthread.php?t=2350606) 

      
 Lenovo 110s  Experience Installing and Using Linux on my Lenovo 110s UEFI settings better support than 100
[URL="https://ubuntuforums.org/showthread.php?t=2350394"]https://ubuntuforums.org/showthread.php?t=2350394

[/URL]
 Trying to install Ubuntu on an Acer one 10 (S1002)  32 bit
[http://ubuntuforums.org/showthread.php?t=2305272](http://ubuntuforums.org/showthread.php?t=2305272)
Instructions to install Ubuntu 16.04 on ASUS EeeBook X205TA - Atom Bay Trail 32 bit UEFI
[https://github.com/lopaka/instructions/blob/master/ubuntu-16.04-install-asus-x205ta.md](https://github.com/lopaka/instructions/blob/master/ubuntu-16.04-install-asus-x205ta.md)
[https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md](https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md)
Linux 3.15 Kernel Gains EFI Mixed Mode Support
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI) 


[URL="https://ubuntuforums.org/showthread.php?t=2350394"]
[/URL]

---

