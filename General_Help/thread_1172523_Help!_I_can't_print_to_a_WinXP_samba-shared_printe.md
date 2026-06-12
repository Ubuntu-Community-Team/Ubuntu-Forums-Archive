---
title: "Help! I can't print to a WinXP samba-shared printer."
date: 2009-05-28
forum: General Help
---

### Post by volanin on 2009-05-28
I have a notebook with Ubuntu Jaunty installed and fully upgraded, and a desktop with Windows XP to which the printer in connected. This printer is an HP Laserjet 1020. The files and printers in the WinXP desktop are shared, and the proof of that is that I can easily access the files through my notebook (no authentication required).

But when I add the printer via System > Administration > Printing, I cannot print to it. The Verify button that appears when you are adding the new printer detects the printer perfectly. But when I complete the installation and try to print a Test Page (or any other document), I get an error message: **foomatic-rip fail**

The print job appears on the WinXP box, but the size reported is just 50 bytes, so there is some problem going on. Also, the contents of the */var/log/cups/error_log* file is this:

```
E [28/May/2009:16:52:38 -0300] PID 8068 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!
E [28/May/2009:16:52:38 -0300] [Job 18] Job stopped due to filter errors.
```

When I tested the printer directly in my notebook via USB connection, the ubuntu installer downloaded a proprietary firmware file, and everything prints ok.

What can I do?
:(

---

### Post by clonne4crw on 2009-05-28
[http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1020](http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1020)

What driver are you using? OpenPrinting reccommends the foo2zjs driver.

---

### Post by volanin on 2009-06-02
I have no idea!
The Printing dialog says:
**Make and Model: HP LaserJet 1020 hpijs, 3.9.2**
The same make and model as the LOCAL USB connection that works.

---

