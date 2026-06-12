---
title: "Serial port in wine?"
date: 2008-12-08
forum: General Help
---

### Post by defiancecp on 2008-12-08
So I'm having trouble getting serial port function in wine.  Ubuntu is version 8.1 (intrepid).  It's a USB serial cable, ttyUSB0, and I've confirmed it works in linux (I tested with Megatunix).  I've created the link in the .wine/dosdevices folder (com1 to ttyUSB0), but it doesn't seem to have made any difference - the software (logworks) reports no availble com ports.  Just to check if it was a software issue, I downloaded a serial port terminal program (advance serial port terminal), installed it in wine, and it also says no serial ports are available.  Any suggestions?

---

### Post by defiancecp on 2008-12-09
Any suggestions are appreciated :(

---

### Post by Victor516 on 2008-12-09
did you make the link to /dev/ttyUSB0?

---

### Post by defiancecp on 2008-12-10
The link is there.  The command I used to create it is "ln -s /dev/ttyUSB0 ~/.wine/dosdevices/com1", and ls of the dosdevices directory does show com1 and my drives.  But none of my programs can see that a com1 exists.  Is there something else in Wine that must be configured to tell wine that there is a com1?

---

### Post by dannysauer on 2009-06-27
It's a problem with how Logworks (and some other windows programs) try to get the serial port.  I can use TunerCat with the same USB serial adaptor that LogWorks somehow doesn't see at all...

You've done the right thing (symlink com1 to /dev/ttyUSB1 or whatever).  You just need to get the old LogWorks, and that apparently works.
[http://www.innovatemotorsports.com/support/downloads/legacy/LogWorks2Setup.exe](http://www.innovatemotorsports.com/support/downloads/legacy/LogWorks2Setup.exe)

---

