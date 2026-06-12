---
title: "Can't boot from LiveUSB"
date: 2009-05-30
forum: General Help
---

### Post by b@sh_n3rd on 2009-05-30
Hi, I've downloaded an ISO image of "**nUbuntu**" as a matter of curiosity, and tried to experiment with it's LiveCD. I'm having trouble booting my PC from a LiveUSB created by Ubuntu's **USB Creator** application with the ISO image. I tried to do this with a program called **UNetBootin** too, but without success. My PC *can* boot with a usb stick, and I've done it before. I select it from the list but it shows a blanks screen, then boots from my hdd on my existing Jaunty installation..any help? Thanks...

---

### Post by pastalavista on 2009-05-30
Maybe check your BIOS settings to see if USB boot is still enabled before the HDD. If it is, try another USB port or a different flash drive. Did you format the thumb drive before you installed the iso? Will it boot on any other PC? Lots of things can go wrong but I don't know them all... good luck.

---

### Post by aarons6 on 2009-05-30
i tried this on my computer as well it didnt work the first time but i figured it out.

on my pc, the usb drive was showing up as HDD0-USB 
it was actually in the hard drive section of the boot menu, not the external usb drive section..

i think those are reserved for usb floppys and zip drives..

check that out, you might not even be turning on the correct function to boot from the usb stick.
the only other thing i can think of is if you have some boot loader on your hard drive it might be taking over, even if its set to be the next drive on the list in the bios.

might need to disable it, or just add the usb sticks kernel to whatever boot loader your using.

---

### Post by b@sh_n3rd on 2009-05-30
> **pastalavista said:**
> Maybe check your BIOS settings to see if USB boot is still enabled before the HDD. If it is, try another USB port or a different flash drive. Did you format the thumb drive before you installed the iso? Will it boot on any other PC? Lots of things can go wrong but I don't know them all... good luck.

> **aarons6 said:**
> i tried this on my computer as well it didnt work the first time but i figured it out.

on my pc, the usb drive was showing up as HDD0-USB 
it was actually in the hard drive section of the boot menu, not the external usb drive section..

i think those are reserved for usb floppys and zip drives..

check that out, you might not even be turning on the correct function to boot from the usb stick.
the only other thing i can think of is if you have some boot loader on your hard drive it might be taking over, even if its set to be the next drive on the list in the bios.

might need to disable it, or just add the usb sticks kernel to whatever boot loader your using.

Hi guys, thanks for your replies. Yeah, I formatted the drive before adding the ISO onto it and I did enable the USB Drive to boot before everything else. Normally, it should boot without any user input as the USB Drive is at the top of the list. Nevertheless, I even tried manually selecting a boot device from the BIOS boot menu (by hitting F10) and still it skipped the drive. I can boot from CD alright...it's only the Flash Drive I'm having trouble with. I've even tried forcing the BIOS to boot into the USB drive by removing the other selections from the boot list, but that didn't work at the time. How could I add the flash drive to the GRUB bootloader if it's possible? My guess is, the BIOS doesn't seem to be able to find the required files to boot from the Drive. I'll try a seperate USB port. I'm using one port with a USB extension cable :D. BTW, my USB drive is shown on the list by it's model tag, (**JetFlash T54GJFV30**)

**UPDATE:** OK, I tried it but it didn't work as usual. Either it can't find any files, OR my PC is just not interested in pleasing me :D

---

### Post by forestlake on 2009-05-30
just as a matter of curiosity have you tried the Ubuntu Netbook Remix?

---

### Post by b@sh_n3rd on 2009-05-30
> **forestlake said:**
> just as a matter of curiosity have you tried the Ubuntu Netbook Remix?

dude, not to be rude or anything, but this isn't relevant to my question is it? :D In answer to your Q though, no I haven't...I've thought of, but haven't really as it wouldn't seem useful to me unless I've got a netbook. My existing PC fleet and **TiTANIUM** (read sig) is good enough for me anyway :D

Back to the thread;

I tried using the flashdrive on a different USB port and double-checked my boot list just to be sure. No go...:(

---

### Post by zeller on 2009-06-05
I'm having a similar problem, albeit not exactly the same. The difference is that my usb doesn't even show up in my BIOS list. Network Adapter, CD-Rom drive, Floppy, or Hard Disk are my only options?

Is there a way to add USB to the list?

---

### Post by zeller on 2009-06-05
Okay, after a few reboots, the BIOS recognized my USB drive. I changed the boot order but the screen displayed some bizzare symbols and read that it could not boot. I'm thinking that has to do with the information on my USB thumbdrive.

Does the thumb drive need to be formated a certain way or did UNetbootin just mess up with the install to the USB stick?

EDIT: Also, does UNetBootin need an ISO or an IMG file to work properly? I used an ISO but if that's wrong, that may explain it.

---

