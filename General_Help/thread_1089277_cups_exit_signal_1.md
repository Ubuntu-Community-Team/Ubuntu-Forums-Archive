---
title: "cups exit signal 1"
date: 2009-03-06
forum: General Help
---

### Post by nat0925 on 2009-03-06
I am trying to install an Epson cx4400 on Ubuntu 8.10.  I have used this printer before in Ubuntu 8.10 and scaned pictures in.  Recently I made a backup of my system using Remastersys to reformat and make my partiions bigger; however, after doing this I noticed I couldn't print anymore.  I think CUPS is now ruined.  When I try to add a printer via System --> Admin --> Printer it won't detect my USB Epson cx4400.  I have tried removing CUPS and reinstalling it.  It didn't work.  lsusb detects my epson printer correctly.  And the printer works on my girlfriends windows pc.  Right now my error_log from CUPS is empty and I can't understand why I am getting this error when I execute CUPSD.

nick@nick-laptop:~$ cupsd
cupsd: Child exited with status 1!


Guys please let me know what you think.

Thanks,

Nick

---

### Post by cmnorton on 2009-03-07
cups daemon not starting has to got to be in some log under /var/log.

You can edit /etc/init.d/cups

and look for exit -1. It looks like a pid file was lying around before you started cups. This kind of wierd error does happen.

I cannot remember if /etc/init.d/cups stop will do that for you or if you have to delete the pid file directly and then restart cups.

---

### Post by nat0925 on 2009-03-08
the terminal says /etc/init.d/cups is a bad symbolic link.  (Black background with red letters).

---

### Post by nat0925 on 2009-03-08
Ok I removed the bad links in that folder... cups and usb.  It has detected my Epson printer; however, when I try to print to that tprinter it won't print.  It gets stuck at 9% and the printer doesn't make a sound.  The computer does recignize the printer correct now.

---

### Post by cmnorton on 2009-03-09
Is this a direct or network connect?

Do you have the correct port #? It sounds like you are initializing the printer, and something else is going wrong.

I would like also look in your logs under /var/log.

---

