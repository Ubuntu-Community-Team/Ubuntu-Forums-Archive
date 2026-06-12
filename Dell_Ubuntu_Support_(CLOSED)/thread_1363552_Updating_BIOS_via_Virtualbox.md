---
title: "Updating BIOS via Virtualbox?"
date: 2009-12-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by CanadianBac0n77 on 2009-12-24
Does anyone know if its even possible to update your BIOS in Virtualbox???

I Have a Dell Latitude D600, Running Karmic. The BIOS I have is A14, the newest one is A16. So I was wondering if i could virtuallize XP and update my BIOS that way....?

I figured I should ask before I possible "brick" my laptop....

---

### Post by Morbius1 on 2009-12-24
I don't think so unless you wanted to update the virtual BIOS .;-)

I don't have a dell but have you looked at this:
[http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate](http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate)

---

### Post by Zoot7 on 2009-12-24
I don't see that working TBH. I'd imagine the restrictions imposed by using Virtualbox on the virtualized Os would impede it to do the needful when it comes to flashing the BIOS.

A bootable DOS disk is what I've used in the past to update my laptops BIOS.

---

### Post by martikj2 on 2010-04-22
Granted, YMMV here but on my old 1420n I was able to update the BIOS within Linux. Dell provides tools and instructions to do so here: [http://linux.dell.com/wiki/index.php/Repository/firmware](http://linux.dell.com/wiki/index.php/Repository/firmware)

Cheers

---

### Post by reiki on 2010-04-23
The VM doesn't have access necessary to update BIOS.  This is why I left a small partition on my ZinoHD with the factory-installed OS on it. It's just easier.

---

