---
title: "bios folder for pcsx"
date: 2015-04-03
forum: Emulators
---

### Post by franchesco on 2015-04-03
hey everyone i have been reading this thread [http://ubuntuforums.org/showthread.php?t=1922327](http://ubuntuforums.org/showthread.php?t=1922327) im having a problem adding the file spch1001.bin to the psx bios folder, pcsx will not let me select it. i have copied the file to the bios folder but am unable to select it. im using Lubuntu 14.10 i think. thanks for reading!
[IMG][IMG]http://i.imgur.com/NZkUCXX.jpg?1[/IMG][/IMG]
[IMG][IMG]http://i.imgur.com/efGlYXe.jpg?1[/IMG][/IMG]

---

### Post by franchesco on 2015-04-03
think i found the problem, i was using the wrong file i was using a zip file called scph1001. sorry for being so thick. all blame it on being new to this

---

### Post by General_Faliure on 2015-04-05
I also see your bios ends with .exe
A bios file can never be an .exe, only .zip

---

### Post by deadflowr on 2015-04-05
> **General_Faliure said:**
> I also see your bios ends with .exe
A bios file can never be an .exe, only .zip
I thought bios files were always .bins.(or at least typically .bins.)
since zips are merely archives.

---

### Post by General_Faliure on 2015-04-07
You are right, they are mostly .bins, but they usually also work when zipped.
They just cannot be .exe's

---

### Post by deadflowr on 2015-04-08
> **General_Faliure said:**
> You are right, they are mostly .bins, but they usually also work when zipped.
They just cannot be .exe's

Not with pcsx.
Only bins work for me.

One would think, though, that .exe file would work to a degree since regular system BIOS files are typically .exe files.

---

### Post by adec2 on 2015-05-03
It is probably hard coded in the emulator to look for a bin which is a dump of the bios file

---

