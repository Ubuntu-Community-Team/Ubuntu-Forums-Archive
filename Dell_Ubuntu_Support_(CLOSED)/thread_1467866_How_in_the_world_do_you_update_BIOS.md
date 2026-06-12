---
title: "How in the world do you update BIOS???"
date: 2010-05-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hedgeborn on 2010-05-01
I've got a Dell Latitude 2100, going through the normal Dell tech support is no help because they give you an exe that I cannot run on Linux.

Then, I discovered this:

[http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate](http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate)

Hurrah! I thought, instructions then link you here:

[http://linux.dell.com/repo/firmware/bios-hdrs/](http://linux.dell.com/repo/firmware/bios-hdrs/)

But the "0x02D6" shown by my getSystemId is nowhere to be found. :confused:

There has got to be an easy and practical way to get my 2100 up to the latest
BIOS...without requiring me to install windows ffs!

---

### Post by wilee-nilee on 2010-05-01
Installing a new bios firmware if not done correctly is a good way of having a new doorstop, be very careful. Are you sure you don't already have the latest version?

---

### Post by GregBrannon on 2010-05-01
I didn't read your links, but to answer your question: the typical method for updating the BIOS is to download the BIOS update files and the BIOS updater and put those on a boot disk or CD that will load your computer with a minimal version of the OS you need to run the BIOS updater.  You can find the OS files you need to build the boot disk, usually open source, but Googling "boot disk" or similar.

Yes, you can brick your computer if the BIOS update fails, but I've done it successfully several times over the years.

---

### Post by maximus.bobba on 2010-05-01
hey i have a question.
would updating the BIOS using windows effect ubuntu? it should shoudnt it?:confused:

---

### Post by CJN on 2010-05-01
> **maximus.bobba said:**
> hey i have a question.
would updating the BIOS using windows effect ubuntu? it should shoudnt it?:confused:

Yes it will. To put it in laymans terms BIOS is the first thing that happens when the computer turns on, well before any thoughts as to operating system.

[http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)

Note: It is slowly (oh so slowly) being replaced with the superior EFI system, but if your computer runs BIOS it can't run EFI.

[http://en.wikipedia.org/wiki/Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Extensible_Firmware_Interface)

[COLOR=Red]**ALSO MAKE SURE YOU USE THE EXACTLY MATCHING BIOS UPDATE ONLY, OR YOU WILL NOT BE ABLE TO FIX IT AT ALL IN ANY WAY, YOU CAN'T EVEN TRY BECAUSE NOTHING CAN POSSIBLY HAPPEN WITHOUT A BIOS**[/COLOR]

---

### Post by hedgeborn on 2010-05-01
> **wilee-nilee said:**
> Installing a new bios firmware if not done correctly is a good way of having a new doorstop, be very careful. Are you sure you don't already have the latest version?

I have version A00, latest one is A05 I think. I'm not going to mess with it for now though, Lucid Lynx seems to be running fine with this bios firmware and it seems next to impossible to update the bios unless you're running windows or freeDOS so I'm not going through the trouble at the moment.

---

### Post by reiki on 2010-05-03
BIOS is one of those things where.... if it ain't broke, don't fix it. Unless you need some new feature of the updated BIOS you don't need to change anything.

---

