---
title: "EPSON DX 6050 scanner [WORKING!]"
date: 2008-12-14
forum: General Help
---

### Post by sv1cdn on 2008-12-14
Managed to get it in 8.10 - Intrepid.
Follow this:

lsusb | grep Epson

Look for line with:

BUS 005 Device 003: ID 04b8:082e Seiko Epson Corp.

Notice the ID 04b8:082e yours could be different.

After:

sudo vim /etc/sane.d/epson.conf

Add to the last line:

 usb 0x04b8 0x082e

The numbers came from the previous step! I have also commented all the other lines in epson.conf file.
Restart the udev server or better hard reset:

sudo /etc/init.d/udev restart

MANY THANKS TO THIS GUY:

[http://cfavatar.wordpress.com/2008/06/12/installing-epson-dx6050-printerscanner-on-ubuntu-feisty/](http://cfavatar.wordpress.com/2008/06/12/installing-epson-dx6050-printerscanner-on-ubuntu-feisty/)

AND HIS GIRLFRIEND!

**If by any chance you happen to edit file /etc/udev/rules.d/45-libsane.rules you will probably end with no printing! Better don't!**

P.S. Isn't it great to have a community for Unix?!

---

