---
title: "Cannot boot from any other live cd Dell Dimension 8300"
date: 2008-09-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by xxloverxx on 2008-09-28
So, I installed Hardy Heron and since I use that PC for distro hopping, I tried to put a Sabayon live cd in there - Kubuntu completely ignored it and booted off the hard drive...same happened with other live cds, the only live cd I could boot off was the Ubuntu.

I then took out the HDD, reformatted it under Mac OS X Leopard 10.5.5, dragged and dropped Puppy Linux live cd files into it, and it wouldn't boot up...it gives me a "Keyboard Failure" error at startup and requires that I press F1 to retry rebooting or F2 to enter BIOS...problem being the keyboard isn't even recognised?

It was all fine until I formatted the HDD.  All fine save the fact that I couldnt' do another distro?

---

### Post by Partyboi2 on 2008-09-29
Have you tried loading the bios defaults and seeing if that works?

---

### Post by xxloverxx on 2008-09-29
I've tried all possible combinations in BIOS

I ended up installing Puppy Linux to that HDD via VMWare on OS X, then tried to boot it up.  Now, when it boots, it says it can't find puppy_400.sfs file and drops back to ramdisk-console...

---

### Post by oliverthered on 2010-03-27
I've got similar problems.

Something seems to be very odd about the Dell Dimension 8300.

Basically if I have a usb stick with kubuntu 9.10 on it and no hard drives I can boot off a Kubuntu 9.10 live cd.

If I try to boot of the usb stick, it has problems finding a device or mounting /proc/loop and possibly some other stuff.

nething else but kubuntu 9.10 on the usb stick and won't pass the boot screen.

neother live cd and it won't get past the boot screen

When i leave it for ages I eventually get an error about not being able to find the boot image (or something like that)


What seems to be happening is that the devices seem to be getting mucked around, but only when the boot loader (casper i think) loads the first boot image, because after that boot images is loaded everything get's pulled off the CD rom again.

All I could think was happening is that the boot loader pulled the boot image off of the usb stick cos the devices got 'swaped' or something and then once the image was loaded the devices got detected as expected and everything came off the cdrom again.

This may possibly be a problem with the bootloader? I'm going to try a load of different options and possibly seeing if I can change the location of the chained boot image that the boot loader loads.

---

