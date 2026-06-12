---
title: "Printer Compatibility"
date: 2007-06-24
forum: Dell  Ubuntu Support
---

### Post by W998AFR on 2007-06-24
I have an Inspiron 6000d (dedicated ATI 128 MB video card).  I am dedicating this laptop to Linux only.  What printers work with Ubuntu?  Looking for a color laser printer with a network card.  I have a Netgear Router with a print server built in.  Suggestions?

---

### Post by magicfab on 2007-06-28
Generally speaking you can look at [http://www.linux-foundation.org/en/OpenPrinting](http://www.linux-foundation.org/en/OpenPrinting) for printers supported under any Linux distribution (including Ubuntu).

---

### Post by nick_h on 2007-06-29
Dell recommend printers with a PostScript engine - [link](http://linux.dell.com/wiki/index.php/Tech/Printers).

---

### Post by whizbaby on 2007-06-29
Basically if you want a network printer anyways you could take any and make it run with a generic postscript driver. On linuxprinting.org printers are listed for which it is easy to get a .ppd (postscript printer definition) file, but it doesnt mean that its impossible for the others. 
I recommend though to chose one from linuxprinting.org, e.g. HP is very good supported. Dell usually has the .ppd flyin around somewhere on their homepage.
Flawless experiences with the HP4250 and P2015, and 1720 from Dell is not bad too (if you found the .ppd).

---

### Post by whizbaby on 2007-06-29
> **nick_h said:**
> Dell recommend printers with a PostScript engine - [link](http://linux.dell.com/wiki/index.php/Tech/Printers).

But BEWARE ----- theres a big difference between a real postscript engine and a postscript emulator. All emulators have their limitations and it usually doesnt take long until the first document the printer is unable to print shows up (others will follow).  Get the real engine (usually more expensive), the emu will make you lose a lot of time and hair...
(and never listen to sellers, theyll tell you everything just to get that crap out of their store)

---

### Post by HotShotDJ on 2007-06-29
> **nick_h said:**
> Dell recommend printers with a PostScript engine - [link](http://linux.dell.com/wiki/index.php/Tech/Printers).
Dell's "recommendations" are meaningless.  Dell also recommends Vista for their Ubuntu PC's.  Magicfab's link is your best bet to find a printer that meets your needs and is compatible with Linux.

---

### Post by uputer on 2007-07-01
I'm looking for a printer as well but something that can copy, scan and print colour (inkjet) so I guess I'm considering a multifunction machine.   

I went to the linux printing site and still can't decide on a printer.

I was thinking of these:
HP OfficeJet 5610
Epson Photo CX6000
Brother MFC440CN

Is the HP or Epson better for linux?  Brother has a lot on their site for using their printers but they are proprietary?   

Edit:   I'm not considering the Epson anymore as that printer seems to have problems with ink running out faster than what is acceptable.   Can anyone recommend a multifunction printer that works well in Linux?  I want all the functions and hopefully it's an easy setup.  

Comments?

---

### Post by AdrianVeidt on 2007-07-01
Epson printers have the best open source driver support and work without any crazy configuration work. If you're worried about ink and so forth, spend a decent amount of money on the device. Don't buy something cheap, buy something >$200.

---

