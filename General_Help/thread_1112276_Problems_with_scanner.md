---
title: "Problems with scanner"
date: 2009-03-31
forum: General Help
---

### Post by Dibbling Dave on 2009-03-31
Hello I already posted this in the beginners forum but got no reply. Basically I get the following error message when I try to open XSane:

Failed to open device 'snapscan:libusb:003:006':
Invalid argument

I have updated the libsane-extras

dave@dave-desktop:~$ sudo apt-get install libsane-extras
Reading package lists... Done
Building dependency tree
Reading state information... Done
libsane-extras is already the newest version.
The following packages were automatically installed and are no longer required:
libtwolame0 libdca0 libdvbpsi4 libenca0 libiso9660-5 liblua5.1-0 libvcdinfo0
libebml0 libmatroska0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dave@dave-desktop:~$

I still cannot open my scanner and get the same message. Any ideas what to do now, Dave.

---

### Post by ivanvajar on 2009-03-31
What scanner are you trying to install?

---

### Post by Dibbling Dave on 2009-03-31
Hi, An Epson Prefection 3490 Photo. It was working but has recently stopped. Dave

---

### Post by ivanvajar on 2009-03-31
Give me the output of

> sudo lsusb

please.

---

### Post by Dibbling Dave on 2009-03-31
dave@dave-desktop:~$ sudo lsusb 
[sudo] password for dave: 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 002: ID 04b8:0005 Seiko Epson Corp. Stylus D88+
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04b8:0122 Seiko Epson Corp. Perfection 3590 scanner
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
dave@dave-desktop:~$ 

Thanks Dave

---

### Post by ivanvajar on 2009-03-31
It looks like many people had problem with that scanner. I found this:
[http://doc.ubuntu-fr.org/scanner_epson]("http://doc.ubuntu-fr.org/scanner_epson")

---

### Post by Dibbling Dave on 2009-03-31
Thanks I shall have a read of that. I think it's time for a new scanner

Dave.

---

### Post by ivanvajar on 2009-03-31
I had trouble installing HP ScanJet 2400. Solution was manual copying of some files. I know how frustrating this can be. :-)

---

