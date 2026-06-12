---
title: "Second Ubuntu Down - What the heck!"
date: 2009-04-17
forum: General Help
---

### Post by craigerts on 2009-04-17
okay - I posted a thread that my sons Ubuntu was down - now so is my daughters... it gets stuck on "Operating System Not Found"

please help guys...

---

### Post by craigerts on 2009-04-17
by the way:
Dell Inspiron Ubuntu 7.4

---

### Post by Mike_IronFist on 2009-04-17
> **craigerts said:**
> okay - I posted a thread that my sons Ubuntu was down - now so is my daughters... it gets stuck on "Operating System Not Found"

please help guys...

Please be a lot more specific. This sounds like a problem with GRUB (the bootloader that helps your computer start Ubuntu), but it would be easier for us to help you if you let us know what might have been done before Ubuntu "went down".

Did you update? Did you download a system-changing program?

If you can provide any information on what happened before something caused Ubuntu to be hidden from the GRUB bootloader, (as in getting the "Operating System Not Found" issue) I'm sure that the community can help.

---

### Post by Wiebelhaus on 2009-04-17
Os not found is typical of hard drive failure.

---

### Post by James_Lochhead on 2009-04-17
Yea this sounds like a GRUB problem. Read the Community Documentation in my sig about restoring GRUB.

If that does not work another problem I have encountered is with the boot order. Make sure the hard disk with GRUB on is the first one to boot. If it is not you will get this error.

If you have not been touching anything yourself one of your kids might have fiddled with the BIOS while doing a tutorial or something.

---

### Post by rushmobius on 2009-04-17
If you get the error before seeing the Grub menu, verify it isn't trying to boot from the CD/DVD by removing the CD if it is in the drive.

But as Mike_IronFist stated, try to provide as much detail as possible.

The error 'operating system not found' usually occurs when the first device it attempts to boot from doesn't have a proper boot loader installed such as Grub or the Windows boot loader.

---

### Post by James_Lochhead on 2009-04-17
> **sx66gns said:**
> Os not found is typical of hard drive failure.

Strange for 2 hard drives to be failing right at the same time though.

---

### Post by diwas on 2009-04-17
Fill in more details please.

EDIT: Oh, I am sorry for this post. By the way, do you have two hard drives and u changed the Jumper?

---

### Post by Mike_IronFist on 2009-04-17
> **sx66gns said:**
> Os not found is typical of hard drive failure.

Please don't say that, you'll scare people jumping to that conclusion. It might be true in a few cases, but if it happened on two different machines (as craigerts seems to indicate) it certainly isn't a hard drive failure.

---

### Post by CatKiller on 2009-04-18
OS not found means that the device that the computer is set from doesn't have a next stage for the BIOS to load. Either you're booting from the wrong device or something is wrong with your hard drive configuration.

---

### Post by craigerts on 2009-04-18
okay these are Dell Mini's "Inspiron" They are running ubuntu 7.04.

My daughters machine simply displays the Dell inpiron logo - the "loading bar or indicator" reaches just over half way and freezes... if I push "0" for boot options... nothing happens. Then it finally goes to the "Boot Menu" - If I do diagnostics it states

PXE-E61 Media test failure
Operating System not found

and it does this over and over again

any help offered is REALLY appreciated

the machines are about three months old

---

### Post by juancarlospaco on 2009-04-18
Install Ubuntu 9.04

---

### Post by craigerts on 2009-04-18
CLARIFICATION - the OS is 8.04 I apologize

I have no idea how to install a new OS on these things - there is no disk drive 

I own a 1 gig jump drive... as a list of possible assets

---

### Post by gillmt on 2009-04-18
Has anyone left a USB key plugged in or a CD?

---

### Post by craigerts on 2009-04-18
no. They are free from that. They dont have CD drives anyway... and no USB is plugged in. They have a pic card slot and that is empty too

---

### Post by CatKiller on 2009-04-18
> **craigerts said:**
> 
PXE-E61 Media test failure
Operating System not found

This means that it is trying to boot from the network, and can't. Check your BIOS settings.

---

### Post by Wiebelhaus on 2009-04-18
Mentioning that they have solid state hard drives would change things drastically.

Elementary solution , you haven't configured the initial boot device properly.

---

