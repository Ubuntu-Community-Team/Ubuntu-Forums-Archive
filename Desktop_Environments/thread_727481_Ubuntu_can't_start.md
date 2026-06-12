---
title: "Ubuntu can't start"
date: 2008-03-17
forum: Desktop Environments
---

### Post by bjarne-jensen on 2008-03-17
Hello

I've just installed Ubuntu 7.10 and trying to get my logitech mx-500 mouse to work. I followed this guide: [http://ubuntuforums.org/showthread.php?t=65471](http://ubuntuforums.org/showthread.php?t=65471)

Result: I can't start Ubuntu! It says:

*STARTING ANAC(H)RONISITC CRON ANACRON [OK]
*STARTING DEFERRED EXECUTION SCHEDULER ATD [OK]
*STARTING PERIODIC COMMAND SCHEDULER CROND [OK]
*CHECKING BATTERU STATE... [OK]
*RUNNING LOCAL BOOT SCRIPTS (/etc/RC.local) [OK]

And then nothing happens. The last thing I did was editing the xorg.conf file. 
I'm new to Ubuntu and Linux = I don't know how to fix this in text-mode. 

Anyone ?

---

### Post by Patb on 2008-03-18
Bjarne. Can you restart in Recovery mode?  If so, back up your existing xorg.conf
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak1
```
(And it's good to back this file up every time before you edit it.  That guide should have said so!)

Then run:
```
dpkg-reconfigure xserver-xorg
```
If in doubt, choose the defaults.  This should bring you back to the settings you started with.  

Then reboot. 

Good luck, Pat

---

### Post by bjarne-jensen on 2008-03-18
Thanks a lot! Actually I did take a backup of xorg.conf. Then I used your first command to copy the backup and now Ubuntu starts again.

Now I just need to get my MX-500 mice to work. At least I know how to fix it if I do something wrong.

---

### Post by Tomatz on 2008-03-18
This link should get your MX 500 mouse fully working :)

[http://ubuntuforums.org/showthread.php?t=455656](http://ubuntuforums.org/showthread.php?t=455656)

---

### Post by bjarne-jensen on 2008-03-18
Great! Thanks

---

