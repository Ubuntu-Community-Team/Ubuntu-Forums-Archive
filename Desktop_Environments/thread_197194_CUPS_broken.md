---
title: "CUPS broken"
date: 2006-06-15
forum: Desktop Environments
---

### Post by trepanne on 2006-06-15
I'm a new user running Kubuntu 5.10 a/k/a "Breezy Badger".  I'm trying to set the system up to share a printer.

I added user 'cupsys' to group 'shadow', and tried to add a Samba printer both in the KDE System Settings menu, and in the standard CUPS web admin interface on port 631.  Neither succeeded.  AFAICR, that's pretty much all I've done.

Whereas CUPS was formerly working, now it's completely broken.
I start CUPS with:
```
/etc/init.d/cupsys start
```
The init script returns [ok].

I see the running process:
```
ps ax | grep cups
```
returns
```
10760 ?        Ss     0:00 /usr/sbin/cupsd -F
10771 ?        S      0:00 /usr/lib/cups/backend/hp
10775 pts/4    S+     0:00 grep cups
```

But if I point a browser at [http://localhost:631](http://localhost:631), I get no response.
If I open up KDE System Settings and click on 'Printers', it pops up a window reading 'Initializing Manager', and then proceeds to hang there forever.

These activities leave no trace in /var/log/cups/ , while other errors cause something to be written to that log.

I do get a trace in /var/log/syslog:
```
Jun 15 10:31:16 localhost hp: unable to connect hpiod socket 32770: Connection timed out: prnt/hpijs/hplip_api.c 693
```

I have tried restarting /etc/init.d/hplip , but no dice.  I am reaching the end of my severely limited sysadmin troubleshooting skillz.

Can anybody point me in the direction of a cure?

I'm also looking for KDE-specific information on how to get KDE/CUPS setting up a printer connected to a Windows machine & shared via Samba, if anyone has experience with that.  The Gnome-specific HOWTOs I googled up didn't quite match.

TIA

---

