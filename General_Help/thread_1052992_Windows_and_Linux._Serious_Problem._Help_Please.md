---
title: "Windows and Linux. Serious Problem. Help Please?"
date: 2009-01-28
forum: General Help
---

### Post by flinstonex on 2009-01-28
Ok so. I've made my descision that i want to fully transfer over to ubuntu 8.04.1 (or something like that).

Now here is the problem.
I am dualbooting Vista and Ubuntu. Vista was installed first. The new bootloader took over. Thats fine. But the problem is, I can NOT boot from a CD anymore. Like, i pop the cd in, and then i restart my pc. Then i see my Asus M2N32-SLI Premium screen, where I have the option to enter bios. Then i get a black screen with a flashing white underscore, hoping for a message to click any key. But none. I get the bootloader.

Now I noticed that i can have a command line in the bootloader, so maybe I could get onto the cd that way. I have no knowledge of ubuntu 'codes' but i tried boot /media/cdrom0 from the command line in the loader and it says kernel must be enabled first or something similar to that.

I checked my BOIS and it says that the first Boot is from CD, second is from Removable, third is from HardDrive, and 4th is disabled.

I Really need to get any CD to boot (ie Windows CD, or ubuntu live cd). I have no idea what to do.

Can anyone tell me what I can do?

---

### Post by &#32 Greg on 2009-01-28
On the Asus screen, try pressing F12 and see if that brings you into your 'boot from' options.

Also, are you sure your CD reader is still working?

---

### Post by oldos2er on 2009-01-28
Have you tried any different CDs?

---

### Post by Feivel on 2009-01-28
Booting into a CD is not anything concerning the OS. It is the BIOS of the computer that selects boot devices.

---

### Post by flinstonex on 2009-01-28
> **  Greg said:**
> On the Asus screen, try pressing F12 and see if that brings you into your 'boot from' options.

Also, are you sure your CD reader is still working?

Well, i am burning CD's and then popping them back in to see if they auto run and so on, and they do, so i dont think it is the DVD Drive.

I will give the f12 a try.

Also, should i try disabling changing all the boot sequences to CDrom?

---

### Post by mb_webguy on 2009-01-28
Normally, if your BIOS is set to allow booting from the CD drive, then the CD drive precedes the hard drive in the boot order.  However, you should be able to open a temporary boot menu at the POST screen (the first one you see when you boot the computer, when the BIOS is loading) to select the device from which to boot.

Of course, all of this assumes that you have the CD drive enabled as a boot option in your BIOS.

---

### Post by npatel31 on 2009-01-28
Have you checked if your CD is bootable ?  One thing that tells me your computer is looking for boot cd is the fact that it is giving you blank screen with underscore.

You may want to restore your BIOS to default, and then change the boot order once again.

---

### Post by flinstonex on 2009-01-28
Heh, i got it working. I dont know why, but it just wouldnt do anything with my ubuntu live cd.

I popped in the windows cd, and it did work, so i deleted the Grub loader (or whatever its called). Now im going to delete ubuntu, and then have a fresh install if it.

Thanks for the help guys!

---

