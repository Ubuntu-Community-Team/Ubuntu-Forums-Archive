---
title: "Mupen 64 plus closes after emulation start"
date: 2010-07-29
forum: Gaming &amp; Leisure
---

### Post by jjsullivan on 2010-07-29
So I just recently gifted my old laptop to my little cousin. He likes games so I thought he would enjoy some old n64 games. So I've used mupen 64 in the past so I re-downloaded it from the universe repository and for some reason it wont work, it just closes after I start up a rom. It also loses all config information. I just use all of the standard plugins and just load a rom from the list in the main window. Help?

---

### Post by BigSilly on 2010-07-30
Can you run it from a terminal and tell us the error messages you get? Someone might be able to help if you post them up.

---

### Post by jjsullivan on 2010-07-30
> **BigSilly said:**
> Can you run it from a terminal and tell us the error messages you get? Someone might be able to help if you post them up.

```


Compression: Uncompressed
Imagetype: .v64 (byteswapped)
Rom size: 12582912 bytes (or 12 Mb or 96 Megabits)
MD5: 70C525880240C1E838B8B1BE35666C3B
80 37 12 40
ClockRate = f
Version: 1447
CRC: dcbc50d1 9fd1aa3
Name: GOLDENEYE
Manufacturer: Nintendo
Cartridge_ID: 4547
Country: USA
PC = 80000400
EEPROM type: 0
init timer!
Segmentation fault

```

Well, nothing I know.

---

### Post by BigSilly on 2010-07-30
Have a tinker with some different settings perhaps? It can't hurt to find more suitable settings for the hardware you are using. What sort of graphics hardware does it have? Will it be suitable for OpenGL etc? My missus has a Dell laptop with integrated Intel graphics, and I'm not sure that would be able to run this emulator comfortably.

It might also be an idea to just try reinstalling it again to start with. May be a fault with the download. Could try sudo apt-get clean to purge the packets, then reinstall using whatever method you are most comfortable with. Make sure the config files are deleted first though. You have mentioned they are gone anyway, but I would still make sure.

---

### Post by jjsullivan on 2010-07-30
> **BigSilly said:**
> Have a tinker with some different settings perhaps? It can't hurt to find more suitable settings for the hardware you are using. What sort of graphics hardware does it have? Will it be suitable for OpenGL etc? My missus has a Dell laptop with integrated Intel graphics, and I'm not sure that would be able to run this emulator comfortably.

It might also be an idea to just try reinstalling it again to start with. May be a fault with the download. Could try sudo apt-get clean to purge the packets, then reinstall using whatever method you are most comfortable with. Make sure the config files are deleted first though. You have mentioned they are gone anyway, but I would still make sure.

Yeah I think it's the graphics, just tried to hit the config button on the video settings and it closed. My laptop can handle half life 2 on full though so I think I'll just try to find my own way around things now, thanks anyway.

---

