---
title: "Dapper Printer problems"
date: 2006-06-19
forum: Desktop Environments
---

### Post by master_b on 2006-06-19
I'm running Kubuntu Dapper and am now having printer problems.

After the initial install of Kubuntu Dapper my parrallel port Canon BJ230 inkjet printer worked fine.

Since the recent KDE updates/upgrade This printer begins printing as soon as Kubuntu is loaded, even before I log in. There are no outstanding print jobs.

The output is in ASCII and starts with my username, kdeprint, pc-name, all in large ascii, then in normal font the job name (kdeprint_gQZfZfMO - or similar) and the day, month time and year, then lots of numbers and letter.

Funnily enough, my Brother printer/scanner ( usb port, Brother drivers) works fine.

I tried removing the Canon driver and re-installing, only to find that there are no drivers, neither by /System Settings/Printers or by localhost:631
Help please.


(EDIT) downgraded to kdeprint 3.5.2-0 still same problems.

However, I noticed that in ?system Settings/Printers/AddPrinter Wizard?Backens Section that the choice for local printer (parrallel,serial,usb) is greyed out.

It would appear that KDEPrint 3.5.3-0, or some other part of the latest KDE updates, removes a necessary symlink to the foomatic printer driver file.

This is all still a bit beyond me, but as always with Linux, its a learning experience, albeit a very frustrating one.

Bill

---

### Post by stlutz on 2006-06-20
I'm not sure I'm clear on what is happening.  Have you tried removing and then re-adding the printer?  I'd do it from localhost:631.

---

### Post by master_b on 2006-06-20
Hi stlutz

Neither using localhost:631 or
using /system settings/printers will allow me to access the printer list.

/System settings/Printers has the entry for parallel port greyed out, so I cant get any further, the printer being connected to the parallel port.

localhost:631 lets me get as far as selecting the printer,and goes to the Devices section, rather than the printer listing.

The drivers are installed

/usr/share/foomatic/db/source/driver
and
/usr/share/foomatic/db/source/printer

Seems to be a problem with a missing link to/from lp0 or somesuch

all worked fine before the last kde upgrade

bill

---

### Post by master_b on 2006-06-20
Anyone?

This is getting beyond frustrating.

Bill

---

### Post by master_b on 2006-06-20
Thanks to post by Matteo, problem solved

see:   [http://ubuntuforums.org/showthread.php?p=1163263#post1163263](http://ubuntuforums.org/showthread.php?p=1163263#post1163263)

quote:-

Re: Cups config through browser 
here is the full procedure

Code:
# Add user cupsys to shadow group
sudo adduser cupsys shadow
# add yourself to lpadmin group
sudo adduser <yourusername> lpadmin
# restart cupsys
sudo sudo /etc/init.d/cupsys restart
# configure printer via browser and enter your username and pw when requested
[http://localhost:631/](http://localhost:631/)

ready to print!
__________________
Matteo

END QUOTE


Bill

---

