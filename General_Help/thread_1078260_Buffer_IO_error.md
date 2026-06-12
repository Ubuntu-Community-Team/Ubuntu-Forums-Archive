---
title: "Buffer I/O error"
date: 2009-02-23
forum: General Help
---

### Post by KilledXDestiny on 2009-02-23
I just finished putting together my new system (minus HDD which hasn't arrived yet) 

I wanted to test out how everything worked in Ubuntu using the Live CD: the disc loads, but after the kernel loads the actual Ubuntu loading screen stays up for ages before going black and brings up the message *"Buffer I/O error on device fd0, logical block 0"* which repeats down the screen.

If it's at all helpful here are my full specs.

CPU: Intel Core2 Quad Q8200
Motherboard: Gigabyte GA-EP45-UD3R
PSU: Corsair HX-620
Graphics Card: Galaxy GeForce 9800GT 512MB
Wireless Network Card: D-Link DWA-556 Xtreme N Wireless
Optical Drive: Samsung SH-S223F SATA DVDRW
CPU Cooling: OCZ Vendetta 2
RAM: OCZ PC2-8500 Reaper HPC (4GB, DDR2)

The discs itself is fine; it has passed integrity tests and has been used to install on the laptop I'm currently using.

Any help would be greatly appreciated. 
Thanks.

---

### Post by geirha on 2009-02-23
fd0 is the (first) floppy device. Does your new system have a floppy drive? Doesn't make sense that it fails because of a floppy drive though :/

---

### Post by KilledXDestiny on 2009-02-23
Odd indeed, nope no floppy. Just a DVDRW until I get my HDD.

---

### Post by geirha on 2009-02-23
Try booting it again, and at the boot menu hit F6 (I think) to edit the kernel line. Add the word "nofloppy" at the end. See if that helps.

---

### Post by plucky on 2009-02-23
According to this [link](http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ProductID=2921) your motherboard has a connector for a floppy drive,so you could possibly disable the floppy in the bios if the "nofloppy" option doesn't work.


Good Luck

---

### Post by KilledXDestiny on 2009-02-23
Tried editing the kernel line, no good. Same thing kept happening.
I also tried changing some settings in BIOS (this is my first build so I'm not too adept) I found The "Floppy 3 Mode Support" option disabled and a listing for an "A" drive, I changed the "A" drive settings to none (Hope that makes sense) and ended up at a Command prompt: "BusyBox v1.1.3" 

Tried startx but it said the command wasn't found. :(

---

### Post by geirha on 2009-02-24
When it drops you in a busybox shell, is there any messages before that, errors or warnings in particular? What happens if you type exit?

---

