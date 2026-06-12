---
title: "Printer installation"
date: 2006-02-21
forum: Desktop Environments
---

### Post by Abel Berenstein on 2006-02-21
Hi!
I don't know if this is the proper place for this post, excuse me if not.

I am installing an epson cx4700 in my 5.1 box.
Gutenprint package seems to have been installed ok (cupsys-driver-gutenprint version 4.3.99+cvs20060121.dfsg.1-1 from debian testing).
The printer seems to have been recognized by the OS since I got the following:

  root@emilio:~# lsusb
  Bus 005 Device 006: ID 04b8:0819 Seiko Epson Corp.
  Bus 005 Device 001: ID 0000:0000
  Bus 004 Device 001: ID 0000:0000
  Bus 003 Device 001: ID 0000:0000
  Bus 002 Device 001: ID 0000:0000
  Bus 001 Device 001: ID 0000:0000

where the first line is the printer.

I need to turn the printer off and back on to get the printer visible to the OS, when booting up I don't see the printer with lsusb.

As the printer should be on before CUPS starts up I restart CUPS with '/etc/init.d/cupsys restart'.

After that I install the printer using the 'System/Administration/Printing/New Printer' applet which runs smoothly.

The only remark is that the applet does not detect any printer.

What am I doing wrong? How can I troubleshoot this problem?

Any help is greatly appreciated.

---

