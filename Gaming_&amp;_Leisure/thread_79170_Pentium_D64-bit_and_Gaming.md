---
title: "Pentium D/64-bit and Gaming"
date: 2005-10-19
forum: Gaming &amp; Leisure
---

### Post by ThinkOpen on 2005-10-19
A couple of questions here, first is there an optimized kernel for EMT64, as opposed to AMD64?  If not, will I be OK installing the version of Ubuntu that's built for AMD64 on my EMT64 CPU?  Also, if I install the 64-Bit version of Ubuntu, will I be able to run my Windows games that are 32-Bit?  I'm trying to rid myself of Windows, please help me!  ;) 

Thanks in Advance...

---

### Post by jecos on 2005-10-19
There is no optimized EMT64 kernel that I know of..I have an A64 and run 32bit 686 kernel.
If I ever had a EMT64 I would install 32bit ubuntu, everything will work and won't have any troubles with things not working b/c 64bit...Never ran cedega/wine in 64bit might work.. I would still run 32bit just so everythings known to work. still too many 32bit systems out there anyway..

---

### Post by mlomker on 2005-10-19
It'll run the amd64 version but I'd recommend that you stick with 32-bit unless you have a specific reason to run 64-bit.  There are just too many things that don't work yet (mostly multimedia and games).

---

### Post by Dolphin on 2005-10-19
[QUOTE=mlomker]It'll run the amd64 version but I'd recommend that you stick with 32-bit unless you have a specific reason to run 64-bit.  There are just too many things that don't work yet (mostly multimedia and games).[/QUOTE]

That, and Intel's "64 bit" is trash.  Best to stick to 32.

---

### Post by ThinkOpen on 2005-10-19
Hey, thanks for the help guys.  I'm planning on installing the 32-bit version of Ubuntu... What programs do I need to install in order to run my Windows games?  I've heard about cedega, wine, and point2click... Maybe someone has already posted this info, if so could you please point me in the right direction?  Thanks again.

---

### Post by leech on 2005-10-20
Cedega and Point2Play are commercial products that you can find at [http://www.transgaming.com](http://www.transgaming.com)
Wine is available for free, just 'sudo apt-get install wine' from a terminal.

The main difference between them is, Point2Play is a GUI wrapper for Cedega.  Cedega is a DirectX enhanced version of Wine.  So anything that is OpenGL will probably work just as well under Wine as it would under Cedega.  

Wine is working on their own DirectX stuff as well, but I don't know if it is in the main branch yet.  I know there was a patch to it a while back that I saw.

Good luck.

Leech

---

