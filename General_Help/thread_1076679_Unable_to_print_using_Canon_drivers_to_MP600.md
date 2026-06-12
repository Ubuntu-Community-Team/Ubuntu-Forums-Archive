---
title: "Unable to print using Canon drivers to MP600"
date: 2009-02-21
forum: General Help
---

### Post by mishad on 2009-02-21
I've tried to get the Canon MP600 driver to work as described at [http://mp610.blogspot.com/2007/11/setup-canon-pixma-mp600-or-mp610.html](http://mp610.blogspot.com/2007/11/setup-canon-pixma-mp600-or-mp610.html)  on Kubuntu 8.10 (Intrepid), but without success so far.

I've tried the Canon 2.70 drivers with the "Canon MP600" (hal:///org/freedesktop/Hal/devices/usb_device_4a9_1718_339491_if1_printer_noserial) or "Canon MP600 USB #1" (usb://Canon/MP600), and (with the addition of the 3.00 common drivers needed because I'm running CUPS 1.3.9) the "USB Printer #1 with status readback for Canon IJ" (cnijusb:/dev/usb/lp0). I've tried with the default "Canon MP600 Ver.2.70" ppd, and with both the 1.2 and 1.3 ppds from this site.

In all cases printing a test page has no effect.

I've even tried the "paper switch -> cassette" change suggested (for the MP620) in some comments on the MP600/610 blog referenced above, with no joy.

I _can_ print successfully using the "Canon MP600" or "Canon MP600 USB #1" devices and the gutenprint iP4200 or MP500 ppds (the MP610 ones work for B&W and yellow, but cyan and magenta are spread horizontally by a factor of 2), so the USB etc. is definitely working.

But the gutenprint driver seems to be limited to 600 dpi so I'd really like to get the proper Canon drivers working (I'd also like borderless printing and other advanced options made available with the custom ppds/confs.)

I've run the system-config-printer diagnostics (I installed the gnome version -- the KDE one didn't seem to have the Help->Troubleshoot feature, and the diagnostics don't appear to work in conjunction with the "connect to remote server" feature) and got the attached output.

I noticed two suspicious sections:

...
'D [21/Feb/2009:21:17:43 +0000] [Job 33] (Canon) langage moniter[/usr/bin/lgmonmp600 --gui --cups] start!',
'D [21/Feb/2009:21:17:43 +0000] [Job 33] sh: /usr/bin/lgmonmp600: not found',
...

and:

...
'D [21/Feb/2009:21:17:44 +0000] [Job 33] pstocanonij: /usr/bin/gs -r600 -g4958x7016 -q -dNOPROMPT -dSAFER -sDEVICE=ppmraw -sOutputFile=- -| /usr/bin/cifmp600 --imageres 600 --papersize a4 --media plain --paperload cassette --quality 3 --halftoning ed --renderintent photo --gamma 1.8 --balance_c 0 --balance_m 0 --balance_y 0 --density 0 --contrast 0 --bbox 9,14,586,834 --fit',
'D [21/Feb/2009:21:17:44 +0000] [Job 33] /bin/sh: /usr/bin/cifmp600: not found',
'D [21/Feb/2009:21:17:44 +0000] [Job 33] Wrote 1 pages...',
'D [21/Feb/2009:21:17:44 +0000] PID 7651 (/usr/lib/cups/filter/cpdftocps) exited with no errors.',
'D [21/Feb/2009:21:17:46 +0000] update_cups_browse: Refused 160 bytes from 192.168.1.55',
'D [21/Feb/2009:21:17:47 +0000] update_cups_browse: Refused 159 bytes from 192.168.1.55',
'D [21/Feb/2009:21:17:47 +0000] [Job 33] GPL Ghostscript 8.63: Unrecoverable error, exit code 1',
'D [21/Feb/2009:21:17:47 +0000] PID 7655 (/usr/lib/cups/filter/pstocanonij) exited with no errors.',
...

I tried to fix the first one with a symlink from /usr/bin/lgmonp600 to /usr/local/bin/lgmonmp600, but that just gets a library error (libgtk1.2 not found). I get the impression that's just some UI pop-up thing, so I thought I'd ignore that for now...

I fixed the cifmp600 not found with a similar symlink, and then got:
...
'D [21/Feb/2009:21:22:31 +0000] [Job 34] pstocanonij: /usr/bin/gs -r600 -g4958x7016 -q -dNOPROMPT -dSAFER -sDEVICE=ppmraw -sOutputFile=- -| /usr/bin/cifmp600 --imageres 600 --papersize a4 --media plain --paperload cassette --quality 3 --halftoning ed --renderintent photo --gamma 1.8 --balance_c 0 --balance_m 0 --balance_y 0 --density 0 --contrast 0 --bbox 9,14,586,834 --fit',
'D [21/Feb/2009:21:22:31 +0000] [Job 34] /usr/bin/cifmp600: error while loading shared libraries: libpng.so.3: cannot open shared object file: No such file or directory',
'D [21/Feb/2009:21:22:31 +0000] [Job 34] Wrote 1 pages...',
'D [21/Feb/2009:21:22:31 +0000] PID 7796 (/usr/lib/cups/filter/cpdftocps) exited with no errors.',
'D [21/Feb/2009:21:22:33 +0000] [Job 34] GPL Ghostscript 8.63: Unrecoverable error, exit code 1',
'D [21/Feb/2009:21:22:34 +0000] PID 7800 (/usr/lib/cups/filter/pstocanonij) exited with no errors.',
...

Added another symlink for libpng.so.3 -> libpng12.so.0 (guessing somewhat by now...) and got:
...
D [21/Feb/2009:21:28:37 +0000] [Job 36] pstocanonij: /usr/bin/gs -r600 -g4958x7016 -q -dNOPROMPT -dSAFER -sDEVICE=ppmraw -sOutputFile=- -| /usr/bin/cifmp600 --imageres 600 --papersize a4 --media plain --paperload cassette --quality 3 --halftoning ed --renderintent photo --gamma 1.8 --balance_c 0 --balance_m 0 --balance_y 0 --density 0 --contrast 0 --bbox 9,14,586,834 --fit
D [21/Feb/2009:21:28:37 +0000] [Job 36] Wrote 1 pages...
D [21/Feb/2009:21:28:37 +0000] PID 8005 (/usr/lib/cups/filter/cpdftocps) exited with no errors.
D [21/Feb/2009:21:28:38 +0000] update_cups_browse: Refused 159 bytes from 192.168.1.55
E [21/Feb/2009:21:28:38 +0000] [Job 36] Unable to send print file to printer: Broken pipe
I [21/Feb/2009:21:28:38 +0000] Saving subscriptions.conf...
...

(full error_log extract for this symlinked-up attempt also attached)

Anyone got these drivers working in [k]ubuntu 8.10?

Misha

---

### Post by akoblentz on 2009-03-24
I think you and I are having the same problem, except I'm using ubuntu, not kubuntu.  Might be an all-variants thing.  It works, but looks terrible, when I use a different driver.  If I use the canon drivers, it says processing for about a second, and then says idle.  I tried changing the paper source as well.

---

### Post by Mega_Mike on 2011-03-18
This might help since I use an explicit ppd file

[http://ubuntuforums.org/showthread.php?p=10575009#post10575009](http://ubuntuforums.org/showthread.php?p=10575009#post10575009)

---

### Post by ikari87 on 2011-12-09
Hi, and sorry for bringing the thread up after months.

Does the driver referenced in the last post help for the shifted colors issue? I have just plugged in a Canon MP600 and am experiencing the same - I needed to a print black-and-blue document, and it looks like black and yellow are getting printed in the right place, but cyan is scaled 200% horizontally. 

Moreover, it only happens with 600DPI, a 300DPI printout is correct. Oh, and I'm using Debian. 
The driver I use is: Canon PIXMA MP600 - CUPS+Gutenprint v5.2.7 
(there is a Canon MULTIPASS MP600 as well, but "can't copy PPD file" after selecting it)

---

