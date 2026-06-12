---
title: "Wont boot from USB"
date: 2009-01-04
forum: General Help
---

### Post by Aizawa on 2009-01-04
I have tried to boot many distributions of Linux from a USB stick. None have worked. The one I just tried was slackware 12.2, which didn't work. I installed it with Unetbootin and all was well, no errors...

It just wont boot. I have it as 1st boot priority, of course. This may be a really silly question, but does it matter what file system it is? I think it's vfat right now...

---

### Post by HermanAB on 2009-01-04
Did you enable boot from USB in the BIOS?

Cheers,

Herman

---

### Post by Aizawa on 2009-01-04
Uhm. Well, I can put it on my boot priority list, so it should be enabled, right?

---

### Post by Jose Catre-Vandis on 2009-01-04
Pop over to [www.pendrivelinux.com](www.pendrivelinux.com). They provide boot cds for usb sticks for various distributions plus loads of info if you are having trouble getting your PC to boot from usb from within the bios

---

### Post by Aizawa on 2009-01-04
Well this is supposed to work, and I can boot from USB sticks.. My Motherboard is pretty top of the line, too...

---

### Post by mdurham on 2009-01-04
Aizawa, all you say is that it doesn't work. What EXACTLY happens when you try to boot from USB?

---

### Post by semi_fiction on 2009-01-04
When your computer is in POST, does it have an option like "Press F12 for boot menu"?
If it does, go to the boot menu and select your USB device.

Also, make sure that in your BIOS, USB emulation is set to "all", not just  "keyboard ans mouse only."

---

### Post by albinootje on 2009-01-04
> **Aizawa said:**
>  It just wont boot. I have it as 1st boot priority, of course. This may be a really silly question, but does it matter what file system it is? I think it's vfat right now...

Unetbooting needs vfat afair.

Did you manage to boot anything else from that usb-stick on that machine before ?
My two older usb-sticks refused booting from my Acer Aspire One.
Only a newer and bigger usb-stick did boot successfully (FreeDOS, wattOS, Ubuntu).

---

### Post by Aizawa on 2009-04-25
I've tinkered around quite a lot the last months, and I finally realized what I had to do to make it work. It was really simple, and I thought I might as well post it here.

Quite simply, I had to choose it has a hard drive. It was pretty weird, but might have something to do with the size of it (8GB.. Not much, but wth)..

Anyway, just to clarify, I do have a removable device option in my boot priority, but that doesn't do the trick. When choosing my hard drive in the BIOS I instead pick the USB stick and it boots perfectly. Sorry for the necro, but it might help someone.

---

