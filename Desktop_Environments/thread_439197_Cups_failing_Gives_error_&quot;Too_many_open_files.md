---
title: "Cups failing: Gives error &quot;Too many open files&quot;"
date: 2007-05-10
forum: Desktop Environments
---

### Post by pwest on 2007-05-10
The CUPS on a Feisty Edubuntu LTSP desktop server I manage for a youth home is intermittantly failing. When cupsys is restarted it will run fine for about a day and then stop taking any jobs with the same error.

It stops responding and the log file "cups/error_log" contains the following lines:

```
E [timestamp] Unable to create job status pipes - Too many open files.
E [timestamp] Unable to accept client connection - Too many open files.
```

The first of those lines is repeated 1-4 times. But the second is then repeated continually about 800 times per second! Leading to error_log files over 180MB :confused: 

At that very point cups stops taking jobs and stops displaying the printers in any of the usual graphical places. Alongside this occasionaly dhcpd will also then stop working but unlike cups it actually crashes and stops doing anything.

A few details to the system: FEISTY i386 Edubuntu; Opteron 2200 with 2GB ram; RAID-1 hardware; up to 10 client PCs; three laser printers Lexmark OptraS 1250 connected over network using their lpd servers.

Any ideas?

---

### Post by P_Squiddy on 2007-06-19
Looks like this is a known problem, and is in the process of being figured out.  Check this link for further info:  [https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/112803](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/112803)

---

### Post by npman on 2007-07-30
This bug has given me no end of grief at one of my sites.

It appears that a fix has been committed and should be appearing very shortly.

I am not very skilled at decoding all the bug stuff, but it sounds like it was a bug in dbus?

---

