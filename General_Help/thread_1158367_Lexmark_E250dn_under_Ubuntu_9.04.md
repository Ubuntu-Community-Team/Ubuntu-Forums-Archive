---
title: "Lexmark E250dn under Ubuntu 9.04"
date: 2009-05-13
forum: General Help
---

### Post by Muki on 2009-05-13
This is how I got my networked Lexmark E250dn laser printer to work with Ubuntu 9.04.

1. Download the PPD file from [www.lexmark.com](www.lexmark.com). Look for the E250d, then choose Debian/Linux3.1.
2. Download the PPD-Files-LMABJ.tar.z file, and extract it. You will use the Lexmark_E250dn_en.PPD file under UTF-8/en.
3. Open web browser and type in [http://localhost:631/admin](http://localhost:631/admin) to get to CUPS.
4. Click on Add Printer
5. Name your printer
6. Choose App/Socket/HP JetDirect
7. socket://192.168.x.x whatever the IP address of your printer is. Do not add :9100 to your url.
8. Choose the PPD file above, and click Add Printer.

It worked for me! Nobody was more surprised than I!

---

### Post by tzicatl on 2009-09-03
Thanks!!

Works Like a Charm!!


Noe.:popcorn:

---

### Post by rswithanage@yahoo.com on 2009-11-30
You can also download all the PPD files for the E250dn printer in a tarball from
[http://www.boblycat.org/~karltk/stuff/lexmark-e250dn-ppds.tar.gz](http://www.boblycat.org/~karltk/stuff/lexmark-e250dn-ppds.tar.gz)

Connect your printer via USB or the network

Go to System -> Administration -> Printing -> New Printer

Provide the extracted PPD file (Lexmark_E250dn_en.PPD )from the tarball above.
:p

---

### Post by paulsänger on 2009-12-13
Hello,

I have a Lexmark **E250d** Printer, **_not_ E250dn**.

I have tried to install my printer with the ppd from above under ubuntu 9.10.

The printer was installed but it does not print the Testpage and it does not print from open office. It does not print at all.

How could I install my usb-printer Lexmark E250d under ubuntu 9.10?

---

### Post by efflandt on 2009-12-13
It should not be that complicated.  I actually have a C543dn (color laser) that worked fine with the C534dn cups driver on the live CD (since either does postscript).

Once I downloaded the tarball from Lexmark and unwrapped that, the install_ppd.sh script did not appear to work, but I may not have known to use sudo then.  But System > Administration > Printing > New, found my printer IP, and when it did not list that specific model, I just had to point it to the ppd_files/GlobalPPD/ directory, pick my C543, it defaulted to 1 tray and duplex, and that was it.

Test page and OO print fine, even when I used the older model C534dn driver.

NOTE: Ubuntu Printing > New can now find the Lexmark driver for my printer, however that method of installation is untested and does not work.  So it is probably best to still point to the directory containing with the Lexmark ppd files.

I have never installed a USB printer, so not sure what type of port that shows up as in Printing > New, but if you pick the correct port, I would think that even an older driver for E230 or E238 might work in a pinch (even if only single sided), if you do not have the proper ppd for E250d.

---

