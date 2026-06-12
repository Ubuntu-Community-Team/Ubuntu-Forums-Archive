---
title: "Exception in dosemu"
date: 2006-01-05
forum: General Help
---

### Post by cristianommxp on 2006-01-05
Hi, 

on my first time using Breezy, I tried to install "dosemu" package:

$ sudo aptitude install dosemu

The dosemu package was installed 100% ok, but when I'm starting dosemu, an excetion is caused:

=============================================
FreeDOS kernel version 1.1.28 (Build 2028) [Dec 09 2002 21:55:55]
Kernel compatibility 7.10 - WATCOMC - FAT32 support

(C) Copyright 1995-2002 Pasquale J. Villani and The FreeDOS Project.
All Rights Reserved. This is free software and comes with ABSOLUTELY NO
WARRANTY; you can redistribute it and/or modify it under the terms of the
GNU General Public License as published by the Free Software Foundation;
either version 2, or (at your option) any later version.
C: HD1 Pri:1 CHS=    0-1-1 start =     0MB,size =  392
Kernel: allocated 41 Diskbuffers = 21812 Bytes in HMA
[dosemu EMS 4.0 driver installed]
ERROR: cpu exception in dosemu code outside of VM86()!
trapno: 0x0e  errorcode: 0x00000004  cr2: 0x468a5b2d
eip: 0x468a5b2d  esp: 0xbfa9ffc5  eflags: 0x00010286
cs: 0x0073  ds: 0x007b  es: 0x007b  ss: 0x007b
Page fault: read instruction to linear address: 0x468a5b2d
CPU was in user mode
Exception was caused by non-available page
/usr/bin/dosemu: line 218: 15477 Falha de segmentação  $SUDO $BINARY $XFLAG 
=============================================

So, what's the solution to this?

---

### Post by supergrapeman on 2006-01-12
> **cristianommxp]Hi, 

on my first time using Breezy, I tried to install "dosemu" package:

$ sudo aptitude install dosemu

The dosemu package was installed 100% ok, but when I'm starting dosemu, an excetion is caused:

=============================================
FreeDOS kernel version 1.1.28 (Build 2028) [Dec 09 2002 21:55:55]
Kernel compatibility 7.10 - WATCOMC - FAT32 support

(C) Copyright 1995-2002 Pasquale J. Villani and The FreeDOS Project.
All Rights Reserved. This is free software and comes with ABSOLUTELY NO
WARRANTY said:**
> 
ERROR: cpu exception in dosemu code outside of VM86()!
trapno: 0x0e  errorcode: 0x00000004  cr2: 0x468a5b2d
eip: 0x468a5b2d  esp: 0xbfa9ffc5  eflags: 0x00010286
cs: 0x0073  ds: 0x007b  es: 0x007b  ss: 0x007b
Page fault: read instruction to linear address: 0x468a5b2d
CPU was in user mode
Exception was caused by non-available page
/usr/bin/dosemu: line 218: 15477 Falha de segmentação  $SUDO $BINARY $XFLAG 
=============================================

So, what's the solution to this?


I get exactly the same error. Is dosemu broken under breezy?

---

### Post by supergrapeman on 2006-01-12
[QUOTE=supergrapeman]I get exactly the same error. Is dosemu broken under breezy?[/QUOTE]

Aha. solution is here: [http://ubuntuforums.org/archive/index.php/t-84718.html](http://ubuntuforums.org/archive/index.php/t-84718.html) 

copied from there..

To correct this, as superuser, type:
echo 0 > /proc/sys/kernel/randomize_va_space

that fixed it for me :)

---

