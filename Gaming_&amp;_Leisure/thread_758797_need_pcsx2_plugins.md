---
title: "need pcsx2 plugins"
date: 2008-04-18
forum: Gaming &amp; Leisure
---

### Post by etusha on 2008-04-18
need plugins for pcsx2 v0.9.4 
i have ubuntu 7.10 drapper aspire 5630

---

### Post by Besyanteo on 2008-11-04
Hey, I'm having a similar (kinda?) problem. I noticed that the plugins detailed on the [PCSX2 website]("http://www.pcsx2.net/downloads.php?p=plgn") largely don't detail linux versions of their plugins, and I went to [NGEmu]("http://www.ngemu.com/ps2/pcsx2.php?action=plugins") to find some, as I used to for ePCSXe back when I ran Win2k; I was delighted to see that they had some, until I downloaded and placed them in my plugins file. Then I got this error:

```
***@***:~/Desktop/pcsx2$ pcsx2

plugins/libGSsoftx.so: wrong ELF class: ELFCLASS32
plugins/libCDVDlinuz.so: wrong ELF class: ELFCLASS32
plugins/libspu2PeopsOSS.so.1.0.2: wrong ELF class: ELFCLASS32
plugins/libGSsoftx.so: wrong ELF class: ELFCLASS32
plugins/libCDVDlinuz.so: wrong ELF class: ELFCLASS32
plugins/libspu2PeopsOSS.so.1.0.2: wrong ELF class: ELFCLASS32
```

I run Ubuntu 8.10 on an AMD64 processor, and I assume it's telling me that my plugins are all 32 bit. So... Does anyone know where I could find some 64 bit plugins, or if I'm wrong can anyone tell me what IS my issue?

(ZeroPAD 0.2 from the PCSX2 site seems to build and work just fine, as far as the configuration section of the program is concerned.)

---

### Post by Besyanteo on 2008-11-04
Update! Or something, I'm not familiar with the repost etiquette here yet. Anyway!

The issue was resolved by reinstalling using the SVN from the terminal ( "svn co [https://pcsx2.svn.sourceforge.net/svnroot/pcsx2](https://pcsx2.svn.sourceforge.net/svnroot/pcsx2) pcsx2" ); The package came with everything but the bios, and I can handle that bit. Hope this helps out for anyone else having trouble!

---

### Post by bapoumba on 2008-11-05
Moved to Gaming & Leisure.

---

