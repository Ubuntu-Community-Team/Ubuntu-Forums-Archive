---
title: "Pcsx2"
date: 2008-05-18
forum: Gaming &amp; Leisure
---

### Post by diablo69er on 2008-05-18
I have been trying for the past couple hours to get pcsx2 working on Ubuntu Hardy.  I have the ps2 bios in the bios folder, and when I tried to run the program via terminal I get this.

** (<unknown>:8632): WARNING **: Couldn't find pixmap file: pcsxAbout.bmp

I was trying to get to the SLU file

---

### Post by disturbedite on 2008-05-18
i had a problem similar to this with another application.  (missing image/graphic error/warning).  the program wouldn't launch.  i checked into it and found the file that was missing.  it was in the correct place, as it should be.  but the problem was that the program was expecting the image in a different format.  so i converted the image to the format the program wanted & voila!  the program worked fine from then on.
maybe you should check that...

---

### Post by diablo69er on 2008-05-19
what image should I convert it to?  I have crawled the web for hours and I have still not found a solution to my problem.  If you could I'd like to know what you did to fix it, and how you got it working, along with the web pages for reference so I can become more knowledgeable about the subject.

---

### Post by disturbedite on 2008-05-19
it should be self explanatory, but...
it obviously wants the file pcsxAbout.bmp.  so look for a file named "pcsxAbout.whatever".  if its pcsxAbout.bmp, then it is the correct filename & format.  if its named pcsxAbout.xpm, pcsxAbout.jpg, pcsxAbout.png or something else, convert it to bmp.

---

### Post by pablomme on 2008-06-05
I assume you have compiled pcsx2 from the sources and either copied the contents of the 'bin' directory to another location or moved the binary. The problem is that pcsx2 expects a (hidden) '.pixmaps' directory in the same location as the binary, containing the bitmap you mention. Just create the directory and copy the bitmap from the original 'bin/.pixmaps'.

---

### Post by graabein on 2008-06-06
How did this turn out?

Are people actually able to play their PS2 games on Ubuntu? 

What's the price tag on PS2 games these days? Can I get them in regular stores or just second hand? Would be great to have FIFA and NHL on the PC since the only console I have is a Wii.

---

### Post by 4th guy on 2008-06-06
Supposedly you can play if your video card has pixel shader 2.0 or above, but for some reason I can't.

---

### Post by acoustibop on 2008-06-06
Unless you have a fairly top end machine, it's unlikely you'll be able to play games at anything like acceptable frame rates - if they play at all.

pSX Author, the developer of pSX Emulator, is working on Playstation 2 emulation for it.  It's likely to take some time, and will still require a fairly high end machine, but if comparisons between pSX and other Playstation emulators are anything to go by, it should need significantly less resources than PCSX2 to run Playstation 2 games.

---

### Post by graabein on 2008-06-08
OK so this does not apply to me then, cause my machine is a piece of junk. I did however discover that [EVE Online]("http://www.eve-online.com/download/") has a Linux client. I loved games like Elite and Final Frontier so I've signed up for the 14 day free trial.

---

### Post by gruffy-06 on 2008-06-10
No PCSX2 in Ubuntu for me. I have a rather c4rpy Intel GPU, which means I can't use ZeroGS at all. Now I'm saving for quad core system.

---

