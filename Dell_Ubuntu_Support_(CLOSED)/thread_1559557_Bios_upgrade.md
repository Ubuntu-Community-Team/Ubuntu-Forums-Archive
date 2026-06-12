---
title: "Bios upgrade"
date: 2010-08-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by spiky001 on 2010-08-23
Hi I would like to upgrade the bios on my inspiron 8200, I think the bios is A06 at the moment I see the latest is A11 can i download it then burn to cd and boot from that although they say floppy

---

### Post by mikewhatever on 2010-08-24
No, you don't need to burn the BIOS file to the cd by itself. The way to do it is get a bootable free dos cd/usb and DOS version of the BIOS. You can then run the BIOS file from DOS, and hopefully, everything goes as planned.

---

### Post by spiky001 on 2010-08-24
Sorry can you explain free dos cd/usb,
Dose that mean I have to use windows to load it

---

### Post by mikewhatever on 2010-08-24
Yes, Windows, if you have it installed, or free dos. All files on the BIOS download page for your computer are Windows/dos executables .exe. Apparently, Dell doesn't provide anything Linux based for your model.

---

### Post by Chris1274 on 2010-08-24
> **mikewhatever said:**
> Yes, Windows, if you have it installed, or free dos. All files on the BIOS download page for your computer are Windows/dos executables .exe. Apparently, Dell doesn't provide anything Linux based for your model.

They don't even do so for models that come pre-installed with Ubuntu. When I went to update the BIOS on my Latitude 2100, I selected Ubuntu from the pulldown menu and only got a useless .exe file.

---

### Post by spiky001 on 2010-08-24
thks for help Mike yo also said free dos cd/usb where do I get this? Also I have another prob might be connected to bios, how can I tell if usb2 is working? or should bios upgrade solve this?

---

### Post by mikewhatever on 2010-08-24
If your computer can boot from usb, use Unetbootin to get freedos and install it to the usb stick. When done, copy the BIOS executable to that USB, boot from it, and run the executable.
There is also a [MANUAL WAY]("http://sourceforge.net/apps/mediawiki/freedos/index.php?title=USB") of doing it.
If the computer can't boot from USB, you can get a [freedos iso image]("http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/1.0/fdfullcd.iso") for burning to cd. Use isomaster from the repositories to add the BIOS executable to the freedos iso before burning.
As for USB2, can you copy files over USB faster then 2MBps? If so, you have usb2 working.

---

### Post by spiky001 on 2010-08-25
Hi ok not qite done bios upgrade yet, but getting back to usb 2 it shows in the log as it is connected as usb only

usb using **"uhci_hcd"** .  Any ideas how I can fix this?

---

