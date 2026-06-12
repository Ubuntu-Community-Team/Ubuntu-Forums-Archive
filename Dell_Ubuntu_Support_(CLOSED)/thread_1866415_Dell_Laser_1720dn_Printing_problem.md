---
title: "Dell Laser 1720dn Printing problem"
date: 2011-10-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TheOneEyedMan on 2011-10-21
I just upgraded to 11.10 and my printing is no longer working. When I first set the printer up with earlier versions of Ubuntu the following the directions worked:  [Dell Laser 1720dn PostScript PPD]("http://ubuntuforums.org/showthread.php?t=466568&highlight=dell+1720dn"). Now they don't seem to. The file seems to have corrupted the printer properties dialog box and most of the drop down boxes are blank. It keeps trying to print A-size not letter and so it looks weird and won't duplex. The only generic driver I could get to work is hpijs5e which looks horrible (hard to read text and low-res images).  

Can anyone help?

---

### Post by TheOneEyedMan on 2011-10-25
I was able to make some progress with the driver Generic PCL 6/PCL XL Printer - CUPS+Gutenprint v5.2.7. I found a set of options that lets me print, though not at the printer's maximum resolution and sometimes 2-up printing doesn't seem to work.

---

### Post by TheOneEyedMan on 2011-10-26
I'm getting similar (but more reliable results) from a different driver: HP LaserJet 4 Plus v2013.111 Postscript (recommended) after finding under HP-LaserJect 4 plus. I got the idea from [https://wiki.ubuntu.com/HardwareSupportComponentsPrintersDell](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersDell)

Again 600x600 is the maximum (here only) resolution but duplexing and 2-up printing seem to work. Things definitely don't look as sharp as they used to before upgrading to 11.10.

---

