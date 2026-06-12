---
title: "psnup page sizes"
date: 2009-03-12
forum: Desktop Environments
---

### Post by Alien Kev on 2009-03-12
Hi all,

I'm a relatively new convert from M$ to ubunutu 8.10 (all of about 2 weeks!), most of the issues I have come across I've been able to resolve through research, but and I'm having a little difficulty with the psnup program.  I have been using scribus to put together booklets and although scribus doesn't allow you to print a booklet directly in the same way that M$Pub does I did come across a few postings and advice about using the psbook and psnup utilities.

The initial document is sent to file at PostScript Level 3. The resulting file page size is A4, if I use either Level 1 or 2 the resulting page size is US Letter.

I then run the ps file through psbook, this formats it into the correct order for print, 8, 1, 7, 6, 2, 4, 5 and the page size is still set to A4.

I then run the resulting ps file through psnup to place two pages on each side and this is where the page size changes to US Letter.

I have tried using the -p & -P options without much luck, along with setting the sizes manually using -w, -W, -h, -H, again without much luck.

I've done a reinstall of psutils, 
checked the page size using sudo dpkg-reconfigure libpaper

kevin@dns-desktop:~$ paperconf
a4

The output from printingbuginfo..
ProblemType: printingbuginfo v2.0: printingbug ([https://wiki.ubuntu.com/PrintingBugInfoScript](https://wiki.ubuntu.com/PrintingBugInfoScript))
CupsConfiguredDevices: device for hp-LaserJet-1320-series: parallel:/dev/lp0
CupsConfiguredPPDs: hp-LaserJet-1320-series: HP LaserJet 1320 Foomatic/hpijs, hpijs 2.8.7
Date: Thu Mar 12 17:46:14 2009
DesktopEnvironment: GNOME
DistroRelease: Ubuntu 8.10
EtcPapersize: a4
InstalledPrintingPackages:
 ii  cups-driver-gutenprint   5.2.0~rc1-0ubuntu1       printer drivers for CUPS
 ii  foo2zjs                  20080810-0ubuntu4        Support for printing to ZjStream-based printers
 ii  foomatic-db              20080918-0ubuntu4        OpenPrinting printer support - database
 ii  foomatic-db-engine       4.0.0~bzr219-0ubuntu1    OpenPrinting printer support - programs
 ii  foomatic-db-hpijs        20080915-0ubuntu1        OpenPrinting printer support - database for HPIJS driver
 ii  foomatic-filters         4.0.0-0ubuntu3           OpenPrinting printer support - filters
 ii  ghostscript              8.63.dfsg.1-0ubuntu6.2   The GPL Ghostscript PostScript/PDF interpreter
 ii  gs-gpl                   8.63.dfsg.1-0ubuntu6.2   Transitional package
 ii  hpijs                    2.8.7-0ubuntu6           HP Linux Printing and Imaging - gs IJS driver (hpijs)
 ii  hplip                    2.8.7-0ubuntu6           HP Linux Printing and Imaging System (HPLIP)
 ii  libgnomeprint2.2-0       2.18.5-1                 The GNOME 2.2 print architecture - runtime files
 ii  min12xxw                 0.0.9-1ubuntu1           Printer driver for KonicaMinolta PagePro 1[234]xxW
 ii  openprinting-ppds        20080918-0ubuntu4        OpenPrinting printer support - PostScript PPD files
 ii  pnm2ppa                  1.12-16.1ubuntu1         PPM to PPA converter
 ii  pxljr                    1.1-0ubuntu3             Driver for HP's Color LaserJet 35xx/36xx color laser printers
 ii  splix                    2.0.0~rc2-0ubuntu2.3     Driver for Samsung's SPL2 (bw) and SPLc (color) laser printers
Locale: LANG=en_GB.UTF-8, LC_CTYPE=en_GB.UTF-8, LC_PAPER=en_GB.UTF-8
Uname: Linux dns-desktop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

psutils v1.17-26

Any help would be gratefully received as i'm now at a bit of a loss.

Regards
Kevin

---

### Post by buster19 on 2009-05-06
Hi, i'm french and don't speak english very well ...

I have got the same problem and after a lot of manipulation, i have find a solution which is not very beauty.

1.  remove psutils v 1.17.26
2. install psutils v 1.17.24 which is here : [http://packages.ubuntu.com/fr/hardy/psutils](http://packages.ubuntu.com/fr/hardy/psutils)

it work's.

---

