---
title: "HP Deskjet 7 series"
date: 2005-11-07
forum: Desktop Environments
---

### Post by ubuntu-nerd2005 on 2005-11-07
Hi

I have noticed from a number of posts that CUPS with HP Deskjet 700 series seems to be broken inBreezy Badger 5.10.

Basically the printers get recognised and acept print jobs but they then just disappear with no out put.

On my 720C my logs have errors like this -

localhost pnm2ppa[10572]: read_config_file(): error parsing config file at line 18

I [07/Nov/2005:16:02:01 +0000] Adding start banner page "none" to job 2.
I [07/Nov/2005:16:02:01 +0000] Adding end banner page "none" to job 2.
I [07/Nov/2005:16:02:01 +0000] Job 2 queued on 'DeskJet-720C' by 'williamgates'.
I [07/Nov/2005:16:02:01 +0000] Started filter /usr/lib/cups/filter/pstops (PID 10564) for job 2.
I [07/Nov/2005:16:02:01 +0000] Started filter /usr/lib/cups/filter/foomatic-rip (PID 10565) for job 2.
I [07/Nov/2005:16:02:01 +0000] Started backend /usr/lib/cups/backend/parallel (PID 10566) for job 2.
E [07/Nov/2005:16:02:05 +0000] PID 10565 stopped with status 3!
I [07/Nov/2005:16:02:05 +0000] Hint: Try setting the LogLevel to "debug" to find out more.

Anybody know if somebody is working on a solution for this?

Cheers

---

### Post by Yotam2 on 2005-11-08
I have similar problem with psc 1410 in breezy. The printer prints, but the print job dissappears in the middle of printing, after several pages of the multi-page print jobs have been printed!
The error message is similar. If anyone can help, I will be most grateful.

---

### Post by rjacintoh@hotmail.com on 2005-11-14
Dear Friends

I need help,
I have followed several procedures pointed by ubustu-users
however, until now
I can not get that my printer HP DesJet 720C to function:( 

I launch printing orders, but they stay in the queue and never
bever arrive on the printer

Thanks
Raul T. Jacinto
Lima-Peru

---

### Post by kingcharles1666 on 2005-11-16
Hi,

I am also expiriancing printer drama.
I have been looking all over (for 2 weeks now!!!) and tried all suggestions on other posts
I am trying to get a HP Laserjet 6L to work.
I managed to get 1 ubuntu test page out but I have no idea why it worked only that 1 time.
All the other attempts only resulted in asci characters in the top 1 or 2 lines of the page and the printer just continues printing these pages until i reboot or unplug the parallel cable.
just cleaning the print cue and resetting the printer does not stop the printing.
LPT is set as ECP and using CUPS with HPLIP and the hpijs ppd

do whe have a printer guru in the forum??

---

### Post by ckr on 2005-11-21
They have a solution in this thread:
[http://ubuntuforums.org/showthread.php?t=87164&highlight=cups+deskjet+720c+print](http://ubuntuforums.org/showthread.php?t=87164&highlight=cups+deskjet+720c+print)

Add your version number of your printer (720) to the file /etc/pnm2ppa.conf.  There will be a line that simply says "Version" with nothing after it.  That would be where you'd put your 720.

sudo gedit /etc/pnm2ppa.conf
(password)

Make your changes.  Worked immediately for me.

---

