---
title: "installing on a broken PC with XP"
date: 2009-01-29
forum: General Help
---

### Post by Rex Dornan on 2009-01-29
I am trying to install Ubuntu 8.10 on a PC that has Windows XP, but is somehow not working properly.  

The machine can only be booted successfully in basic mode, not normal mode.

When I put the Ubuntu CD in to install, a window comes up showing me the contents of the CD, but there is no automatic install as promised.

---

### Post by Rex Dornan on 2009-01-29
Maybe I should add that I am wondering how I can install despite this.

So how can I?

---

### Post by bumanie on 2009-01-29
I think you have burned the cd incorrectly. You seem to have made a data cd, rather than an image. Any .iso file burned to cd needs to burned as an image. Your burning program should have this option somewhere in the menu's. Try again, this time burning an 'image' of the .iso

---

### Post by Rex Dornan on 2009-01-29
I should also add that the PC is not broken in the sense that it does not work, but that it only turns on in safe mode.

---

### Post by x33a on 2009-01-29
what do you mean by the basic mode?

here's a proper procedure of booting into the live environment:

1. burn the iso at a slow speed.
2. put the disc into your drive and reboot.
3. configure your bios to boot from cd drive first.
4. the disc will load and you'll be provided with different options.
5. choose the installation option.
6. follow the instructions.

you'll have it installed in a few minutes.

---

### Post by bumanie on 2009-01-29
> **Rex Dornan said:**
> I should also add that the PC is not broken in the sense that it does not work, but that it only turns on in safe mode.
That means windows xp is broken - still try to burn the cd as an image and see if it works in safe mode, otherwise burn the .iso as an image at a friends house.

---

### Post by Rex Dornan on 2009-01-29
It seems to be installing successfully -- so far.

Thanks, guys!

---

### Post by Rex Dornan on 2009-01-29
I just received a message saying that the installation step has failed.

It did this a couple of minutes ago, and tried to work through it manually.

Any ideas?

---

### Post by x33a on 2009-01-29
are you using the same disc?

try burning a new disc at slow speeds.

and, if the error still shows up, you might have a bad sector on your hard drive.

---

### Post by Rex Dornan on 2009-01-29
If I have a bad sector on my hard drive, what do I do?  

I am pretty sure that the CD is fine.

---

### Post by Rex Dornan on 2009-01-29
Incidentally, it seems to be stuck at only downloading 6 percent of the software.

I don't know if that is significant.

---

### Post by x33a on 2009-01-29
you mean the installation is stuck at 6%?

to check your hard drive's integrity, you'll have to run chkdsk on windows or get a bootable disc such as hiren's boot disc or systemrescue disc, and use the tools provided to check if your hard drive's fine.

---

### Post by Rex Dornan on 2009-01-29
I abandoned trying to install Ubuntu, and now my computer will not reboot Windows, not even in safe mode.

Now what?

---

### Post by cariboo on 2009-01-29
Get out your Windows installation disk and boot to the recovery console. Once you are at the recovery console and run FIXMBR, my spelling may be off so at the C:\ prompt type help for the correct spelling. Once you have fixed the master boot record, I would suggest you reboot into the recovery console and run chkdsk /r. This command will run check disk on your hard drive and hopefully fix the problem with your with it.

Jim

---

