---
title: "How to install windows 7 on Ubuntu 11.10 [Dell Xps 15]"
date: 2011-12-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by BriNCz on 2011-12-17
So, my title pretty much says it all. I have no clue on how to install Windows 7 over Ubuntu, I only have an installation disc and it won't load it. Do I need to install a ISO mounter and run it that way or is there some other way i'm supposed to do this?

---

### Post by 73ckn797 on 2011-12-17
Do you want to be able to run Windows 7 and Ubuntu? You can install Windows in Ubuntu using VirtualBox, found in the repositories. From that you can install Windows, normally within VirtualBox. Look here: [https://www.virtualbox.org/](https://www.virtualbox.org/) and here: [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

You can also install Windows to another hard drive or create a separate partition to install Window on and dual boot. The difference is that VirtualBox allows you to run & use Windows while still in Ubuntu.

---

### Post by BriNCz on 2011-12-18
No, I want to do a complete install over ubuntu and make it my main OS. I've been having problems trying to get ubuntu to load the disc and idk how to make it boot from the Windows 7 USB installer I just made.

---

### Post by 2F4U on 2011-12-18
Can't you boot the Windows installation disk? The Windows install should then be able to delete the existing partitions and install.

---

### Post by BriNCz on 2011-12-18
i'm not entirely sure how to boot from usb or cd in ubuntu. If I press f12 a screen comes up and only shows memory tests, the current version of ubuntu, or the previous version of ubuntu. F2 doesn't do anything either and i'm new with the command line thing so i don't really know my way around it.

---

### Post by 73ckn797 on 2011-12-18
> **BriNCz said:**
> i'm not entirely sure how to boot from usb or cd in ubuntu. If I press f12 a screen comes up and only shows memory tests, the current version of ubuntu, or the previous version of ubuntu. F2 doesn't do anything either and i'm new with the command line thing so i don't really know my way around it.

I am confused by you saying you can't boot from a USB or CD in Ubuntu. Is there not an option when rebooting the computer, such as F9, F10 or F12 during the boot up process, before you reach any OS options, to allow you to select a different boot source, whether that being a CD drive, USB or Hard drive?

---

### Post by BriNCz on 2011-12-18
> **73ckn797 said:**
> I am confused by you saying you can't boot from a USB or CD in Ubuntu. Is there not an option when rebooting the computer, such as F9, F10 or F12 during the boot up process, before you reach any OS options, to allow you to select a different boot source, whether that being a CD drive, USB or Hard drive?


Yes, but it doesn't give me the option to boot from a different device other than what's already installed on to the laptop. It only gives me 4 different things to choose from whenever I press f12 (previously mentioned in a reply) and f2 doesn't do anything.

---

### Post by 73ckn797 on 2011-12-18
> **BriNCz said:**
> Yes, but it doesn't give me the option to boot from a different device other than what's already installed on to the laptop. It only gives me 4 different things to choose from whenever I press f12 (previously mentioned in a reply) and f2 doesn't do anything.
Go to the computer BIOS, accessible when first booting/turning on the computer. You should be able to change the device boot order to USB device, CD/DVD or Hard Drive. That can be selected during the BIOS post screen.

---

### Post by Atagad on 2012-04-18
Hey, I have the problem on the same computer for a machine im working on for a customer.
iv'e tried re-organizing the boot order so that the dvd drive boots first, but im still getting the 4 options: memtest, memtest, ubuntu and ubuntu generic. any advice? :/

is it possible to find a 3rd party software that would allow me to mount/use .iso?
if so, where do i find them, how do i install them?

---

### Post by lisanels47 on 2012-04-18
I've never had a problem with a windows install CD/DVD wiping out other operating systems... Most of the time it nearly impossible to keep it from wiping out your other operating systems.  

If you can't boot from the CD/DVD, then you either have a bad CD/DVD drive, or your boot cmos setup is not set to boot from the CD/DVD drive before the hard drive.

---

