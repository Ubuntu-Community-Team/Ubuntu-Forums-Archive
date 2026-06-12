---
title: "ePSXe OSS problem."
date: 2007-03-28
forum: Gaming &amp; Leisure
---

### Post by Lateralus@desktop on 2007-03-28
I've recently just installed ePSXe 1.60, got everything working (graphics, BIOS, etc) except sound. The only driver I've been able to find is the OSS driver, but that doesnt produce any sound on my PC. I'm using ALSA right now, everything works perfectly. Amarok, Gaim, etc all use my ALSA sound perfectly. Just ePSXe wants to use OSS.

If anyone could please help me find an ALSA plugin for ePSXe, that would be greatly apreciated. 

I'm running Ubuntu 6.10, fully up to date, running on a Celeron with a C-Media sound card (Dont know what it is exactally, but in the sound menu, it says its a C-Media PCI IEC958)

Thanks for any assistance.

---

### Post by Lateralus@desktop on 2007-04-01
Nevermind. Found a solution. 

For those of you who have the same problem, I found an ALSA plugin for ePSXe while googling. Here it is:

[http://packages.debian.org/unstable/games/psemu-sound-alsa](http://packages.debian.org/unstable/games/psemu-sound-alsa)

Install that, then go to the directory it installs to (/usr/lib/games/psemu/...) and move the file in the config/ folder and the files in the lib/ folder to your plugins/ folder in ePSXe (which is usually /usr/local/games/epsxe/plugins/...)

Then select the ALSA plugin from the list in the sound configuration, and it _should_ work.

---

