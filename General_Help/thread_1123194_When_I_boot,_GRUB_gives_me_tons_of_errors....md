---
title: "When I boot, GRUB gives me tons of errors..."
date: 2009-04-11
forum: General Help
---

### Post by PupSpark on 2009-04-11
I tried uninstalling, but the windows fix thing didn't work. Is there any way to uninstall GRUB without windows? I've gotten errors 15, 17, 18, 21, and 22. The most common are 17 and 21.This was the result of trying to boot from external hard drive, but I still need to uninstall.

---

### Post by PupSpark on 2009-04-13
Excuse the double post, but...

GRUB is supposed to be like the windows boot menu right? Or is it more specific than that? How does one get onto grub? If one is dual booting, would one have to do sometihng to have GRUB load instead of windows boot menu? Whenever I turn my computer on and press F8 I get windows' boot menu. I've tried F1, Backspace and tab.

---

### Post by rage9 on 2009-04-13
Grub is a boot manager, not to be confused with Windows boot manager.  If your trying to duel boot, install windows first, then Linux because Windows doesn't care, and will overwrite anything in the MBR (Master Boot Record).  

As for all those errors, how are you getting them?

---

### Post by PupSpark on 2009-04-13
When I turned it on, it would display after the Dell screen that displays automatically. I did install windows before linux.

So how do I "get" to Grub? You ARE saying it's not to be confused with Windows' boot menu by saying they are in the same genre, correct? Is there a button or sequence of buttons to be pressed?

---

### Post by brunogirin on 2009-04-13
If I understand your setup correctly, you have a box with 2 HDD, Windows installed on the first HDD (hd0) and Linux installed on the second HDD (hd1). Can you confirm?

If this is the case, you should have the Windows boot loader in the Master Boot Record (MBR) of hd0 and GRUB in the MBR of hd1. If this is the case, your system will look at hd0 first, find the Windows boot loader and completely ignore what's on hd1. You then have to explicitly boot on hd1 for it to find GRUB.

I suppose that what you would like to do is for your system to find GRUB first and give you the choice to boot either Windows or Linux. Is that correct?

A good resource on GRUB is [Herman's GRUB page]("http://users.bigpond.net.au/hermanzone/p15.htm"): he has a lot of examples of how to dual boot and good explanations of what GRUB does.

---

### Post by PupSpark on 2009-04-13
Yeah. It doesn't seem to deal with not being able to get into GRUB, or GRUB errors or anything. It seems to be more like a starter's guide. So, naturally I'll be using this after I get it working.

I don't WANT to dual boot, but without it I get the GRUB errors... (But then again, I don't get grub at all WITH windows...)

Should I try uninstalling windows again?

---

### Post by brunogirin on 2009-04-13
> **PupSpark said:**
> I don't WANT to dual boot, but without it I get the GRUB errors... (But then again, I don't get grub at all WITH windows...)

Should I try uninstalling windows again?

Before you uninstall Windows, have you tried to resolve the problem using [Super Grub Disk]("http://www.supergrubdisk.org/")? Otherwise, the only thing I can see is check GRUB errors one by one. Here is [a list of them]("http://www.uruk.org/orig-grub/errors.html"). What errors are you actually seeing?

---

### Post by PupSpark on 2009-04-13
I remember 17, 18, 21... I did check them all, and I might have used super grub disk... yeah, I have. Uninstall windows?

OH, I think I forgot to mention, the HDD that Ubuntu is on is USB. That's important, right?

---

### Post by cariboo on 2009-04-13
As much info as possible makes it easier for us to help you. In your case, grub should be installed on the usb drive, that way when the drive is disconnected you should still be able to boot into windows without any problems. Have a look at this [thread=224351]howto[/thread], it will help you restore grub to the correct drive. Once you have grub setup properly, setup the usb drive as the first boot device, then the hard drive as the second boot device, in the BIOS. That way if the usb drive isn't connected it will boot from the first hard drive.

Jim

---

### Post by brunogirin on 2009-04-13
I'm not 100% sure but the fact it is USB could be important, especially if you see errors 17 and/or 18: those errors seem to imply that your GRUB entries are not pointing to the correct device. If the HDD is a USB one, it could be that its device number changes depending on what other USB devices you have connected.

So I would suggest you boot using a live CD with all your standard USB stuff connected and check that the device numbers in your menu.lst file are consistent with the actual device numbers of your disk: for instance, if GRUB has an entry that says "hd1,0", make sure the partition it refers to is indeed the first partition of the second disk, or in other words "hdb1" or "sdb1" as far as Linux is concerned.

---

### Post by PupSpark on 2009-04-13
Alright, so I will try installing Super Grub Disk again, making sure I install it to the proper drive... Then make sure it boots from the USB device first.

How do I do that? I alter my BIOS to do that, right? And is that another button to be pressed at start up, or do I have to boot into something to alter it?

---

### Post by linuxrollup on 2009-04-13
I found the bootloader in the OS settings, but it might be different to you. When Ubuntu loads, there should be a delay when loading and should say 'press esc for menu' or something similar. Press Esc and you should be able to change the flags. Tell me how you get on.

---

### Post by PupSpark on 2009-04-13
Alright...

But if I don't understand soon, maybe I should put off learning and find an alternative solution,([http://www.pendrivelinux.com/run-ubuntu-from-windows-via-a-portable-usb-hard-drive/](http://www.pendrivelinux.com/run-ubuntu-from-windows-via-a-portable-usb-hard-drive/)).

Yeah... That's what I'll do. Funny thing is, USB was already at first priority.

---

### Post by PupSpark on 2009-04-14
I decided to try out of curiosity , because I decided not to do just an emulation... I set everything in my BIOS (At least... that's what I think I was tampering with. It let me screw with my system time and decide which priority CDs, Hard Drives and removable devices are at. That's the BIOS thinger, right?) to point towards my USB HDD and it's just telling me to reboot and insert bootable media.

Am I doing something wrong? I'm having trouble believing that I haven't missed some sort of vital component in GRUB that I was stupid not to install.

---

