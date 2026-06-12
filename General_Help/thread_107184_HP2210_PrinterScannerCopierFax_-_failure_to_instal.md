---
title: "HP2210 Printer/Scanner/Copier/Fax - failure to install scanner"
date: 2005-12-22
forum: General Help
---

### Post by JimS on 2005-12-22
Printer install successful, but scanner install failed with Ubuntu.
I started with Applications - Graphics - XSane Image scanning program.
It scanned for devices and came up with the following error.
Error reads: Failed to open device 'hpaio:/usb/PSC_2200_Series?serial...;
Error during device I/O/  
 :confused:  

I had previously install this scanner successfully
with WinME and Suse 9.0.  Yesterday it scanned
a picture successfully in WinME on this box.

PC is 5 year old Dell 4100, 512MB RAM, 2 HDs, 
Ubuntu BB 5.10 recently installed on new 2nd HD,
Original WinME on old 1st HD,
USB1.1, duel boot.
Only other Ubuntu problem is occasional lost
of cursor movement ability after boot up.

Any help will be greatly appreciated.

JimS
Prostate Cancer Aware

---

### Post by JimS on 2006-01-03
...

I am so surprized that no one responded.
This was so easy in Suse 9.0!
It doesn't follow that it should be so difficult here.

JimS
Prostate Cancer Aware

 ...

---

### Post by docmanny on 2006-01-03
I have an HP5510 MFC and it works OK with ubuntu with a fresh install. You may want to try to install the HPOJ or HPLIP package and try again. With other installs, I had to install HPOJ and set it up.

[http://hpoj.sourceforge.net/](http://hpoj.sourceforge.net/)

There's a forum there that may address your specific printer.

---

### Post by JimS on 2006-01-03
...

Thank you.

Clarification:
The printer installed and prints just fine.
The scanner works in Windows and
worked in Suse 9.0 Linux just fine,
but not in newly installed Ubuntu Breezy.

Xsane error: Failed to open device 'hpaio:/usb/PSC_2200_Series?
serial=MY34OF46FQ':0G: Error during device I/O.

Any advice is greatly appreciated.

JimS
Prostate Cancer Aware

 ...

---

### Post by docmanny on 2006-01-03
I had a similar problem happen before with another distro. Sometimes turning the printer off and on again did the trick. Beyond that, I'm not sure. In other distros, I've used the hpoj backend, but ubuntu uses hpaio. Try a reboot also for what its worth.

---

### Post by Sef on 2006-01-04
Have you downloaded libsane-extras through the Synaptice Package Manager or through the Terminal?   I downloaded it and my scanner (PSC 1610) scans just fine.

---

### Post by JimS on 2006-01-04
...

Docmanny and Sef

Mucho Mucho     :D 
I found the sanelib-extras this time and installed.
I rebooted both and Xsane worked, granted I have
a bit of study ahead, but I did scan and saved the scan
and found the scanned file.  Now to make things pretty.

Again Many thanks, Tusan tak, Danke, Arigato,  etc.
Happy New Year

JimS
Prostate Cancer Aware
 ...

---

