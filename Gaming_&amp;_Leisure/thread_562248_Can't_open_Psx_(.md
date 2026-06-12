---
title: "Can't open Psx :("
date: 2007-09-28
forum: Gaming &amp; Leisure
---

### Post by TonkaTruck18 on 2007-09-28
Hi i'm new to Ubuntu and just recently installed PsX emulator and i got the scph bios file but whenever i click on the icon it does not open (i did download the linux version 1.13) and it says i need shared libraries 	
        OpenGL
	ALSA
	GTK
	GTKGLEXT
	libxml2
But i have no idea what that all means, if anyone could help it would be great, thanks!!:)

---

### Post by disturbedite on 2007-09-28
you shouldn't have to worry about opengl, alsa, gtk as those are inherent with the system.  (libxml2 might be too).

search for gtkglext & libxml2 in synaptic and install the appropriate package(s).

---

### Post by TonkaTruck18 on 2008-02-14
o thx for the help! and ron paul rocks!!

---

### Post by acoustibop on 2008-02-14
Presumably you've found it anyway, TonkaTruck18, but the actual package you need is libgtkglext1.

Try [Ultima's Frontend for pSX]("http://psxemulator.proboards54.com/index.cgi?board=news&action=display&thread=1156715263") as well.

---

### Post by spyke180 on 2009-07-25
I can' open pSX either. I made sure I have gtkglext & libxml2, and I have the SCPH1001.BIN in the BIOS folder, but the executable icon doesnt do anything and if I put "./pSX" in the terminal, it says "no such file or directory". I'm running Ubuntu 9.04 64-bit.

---

### Post by Grishka on 2009-07-25
> **spyke180 said:**
> I can' open pSX either. I made sure I have gtkglext & libxml2, and I have the SCPH1001.BIN in the BIOS folder, but the executable icon doesnt do anything and if I put "./pSX" in the terminal, it says "no such file or directory". I'm running Ubuntu 9.04 64-bit.

you're obviously trying to run pSX from the wrong directory. cd to the directory where you've put pSX, and try again.

---

### Post by Sef on 2009-07-25
Closed.[IMG]http://ubuntuforums.org/home/sef/Desktop/necromancing.png[/IMG]  Necromancing.

---

