---
title: "Epson NX300 All-in-One"
date: 2009-01-14
forum: General Help
---

### Post by AJExtreme on 2009-01-14
I am running Unbuntu 8.10; I have my printer working thanks to some great help here.  But I still can't get my scanner portion of my Epson NX300 to work.  

I open terminal and run lsusb and it shows I have an Epson, but not the model information: don't know if it is important to show.  I have tried to follow some other post about similar problems, but either they don't work with the NX300 or I am doing something wrong. 

I open xsane it doesn't find any devices.

One of the items it shows in the help is possible multi versions of sane install.  If that is the case how do I check and uninstall them if nessecary?

I am looking for some help in trouble shooting this problem as I am still new to Linux, and not really sure where to start.  

If I need to get a different All-in-One then so be it but I want to ensure that my problem isn't something else with the software.

Aaron

---

### Post by todak on 2009-01-14
According to [http://www.sane-project.org/sane-mfgs.html#Z-EPSON](http://www.sane-project.org/sane-mfgs.html#Z-EPSON) your scanner is not supported. If you are going to change devices, may i suggest Hewlett-Packard? They have the best support of their products for Linux of any printer, scanner, all-in-one mfr. that I know of, in my opinion!

---

### Post by AJExtreme on 2009-01-14
What about Cups is this different it is supported through cups.  Is there a scanner for that or is it only sane.

Thanks for the advice of the All in One to get next.

---

### Post by todak on 2009-01-15
Printers are supported under cups, scanners are supported under sane. HP has their own HPLIP (HP Linux Imaging and Printing) that supports their own hardware. CUPS and sane will automatically detect the hardware when you use a program requiring the use of the printer or scanner, once the HP software is installed. See here [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html) for details. Ubuntu automatically recognizes and installs the HPLIP software when you connect the HP hardware.

---

### Post by gmendoza on 2009-08-02
I just bought the Epson Stylus NX300 printer/fax/scanner... and was able to get the scanning function to work with "Image Scan".

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

Fill out their little form, after which they redirect you to a download page.

Download the latest version of their Image Scan software (they have a .deb package for versions of Ubuntu 8.10 and later.

Installing was a snap, and the software worked on the first shot.  Awesome.

---

### Post by larsman1 on 2009-08-03
[SIZE=5]Thanks for the Avasys link.:)  The iScan utility for my RX580 "all in one" has more resolution (dpi) options than xsane.  I'm going to try the Avasys Epson printing utility now.
I'm using Jaunty 9.04 AMD64 for my HP Pavilion Slimline.

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do)
[/SIZE]

---

### Post by uboy14 on 2010-04-05
i tried the web site and when i try to install the deb page it says 
Error: Dependency is not satisfiable: libltdl3 (>= 1.5.2-2)

so can some one tel me how to install

---

