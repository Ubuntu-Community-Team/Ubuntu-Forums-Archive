---
title: "Dell latitude d610"
date: 2011-07-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by titen96 on 2011-07-21
i am completely new in using ubuntu 11.04 and i cant get my wireless connection to work, i alrady got ndiswrapper to try and install the windows drivers but when i put in the bcmw5.inf file it wouldnt detect the hardware, then i went to device manager on windows(i installed the dual boot) and saw that my ethernet controller wasnt recognized but i saw that a wireless adapter was installed, the driver was a dell wireless 1470 dual band wlan mini pci card, i checked the properties and went into details and the ethernet controller gave me:
PCI\VEN_14E4&DEV_1677&SUBSYS_01821028&REV_01\4&2959CBDC&0&00E0
and the dell driver gave me:
PCI\VEN_14E4&DEV_4319&SUBSYS_00051028&REV_02\5&2FA23535&0&18F0

i cant find the drivers to use, and im not sure if ndiswrapper works either, i compiled and installed the source through the ubuntu software centre, can anybody help me with this?

---

### Post by titen96 on 2011-07-23
its been 2 days since i posted this can anybody help, also i think i put this in the wrong topic can it be moved?

---

### Post by MrSmith1131 on 2011-07-23
i have almost the exact same problem

---

### Post by MrSmith1131 on 2011-07-23
have you found a way to get the drivers form EXE. to INI.?

---

### Post by titen96 on 2011-07-23
i extracted the files from the exe for the dell driver and got bcmwl5.ini but when i used it wth ndiswrapper it said it couldnt detect the hrdware but when i pressed ok it said hardware was present, but i couldnt see any networks

---

### Post by MrSmith1131 on 2011-07-23
have you tried wine

---

### Post by MrSmith1131 on 2011-07-23
and by the way what did you use to extract the driver to get a ini

---

### Post by titen96 on 2011-07-23
universal extractor
and no i dont drink wine

---

### Post by MrSmith1131 on 2011-07-23
lol no like the program wine on ubuntu, look it up

---

### Post by MrSmith1131 on 2011-07-23
and also if you dont mind going further into how to get the drivers into ubuntu that would be great

---

### Post by titen96 on 2011-08-07
I dont know why but i got an ethernet cable and connected my laptop to my router and updated linux, after that the wireless networks showed up and connected normally

---

