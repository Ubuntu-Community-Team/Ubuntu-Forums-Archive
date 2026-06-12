---
title: "rsync and cron"
date: 2009-05-24
forum: General Help
---

### Post by sn0m on 2009-05-24
Hi Guys
I've written, actually copy this script to backup my main drive in my laptop to an old desktop that I have designated as backup server.
They're both run ubuntu jaunty and this is the script:

#!/bin/sh
#script to backup to remote desktop
#i have set up connection already using tutorial in linux
/usr/bin/rsync -e ssh -qaruzP /media/sda4/ sn0m-desktop.local:/media/sdb1/sn0m-laptop-backup/


this is the line from crontab -e

#back_upd
00 21 * * * /home/sn0m/my_scripts/rsync.sh


I can actually run it from shell but it dosen't run from cron.
Can anyone help me with it!
Regards
Sokol

---

### Post by kmitnick on 2009-05-24
access /home/sn0m/my_scripts using the cd command
and then```
ls -al 
```

---

### Post by kmitnick on 2009-05-24
post output of the previous command here

---

### Post by sn0m on 2009-05-24
total 208
drwx------  4 sn0m sn0m  4096 2009-05-24 21:24 .
drwxr-xr-x 72 sn0m sn0m  4096 2009-05-24 21:40 ..
-rwx------  1 sn0m sn0m  2370 2009-01-10 16:53 aLive.sh
-rwx------  1 sn0m sn0m  2487 2009-01-10 17:17 amc.sh
-rwx------  1 sn0m sn0m  2487 2009-01-10 17:17 amc.sh~
-rw-r--r--  1 sn0m sn0m   225 2009-05-23 05:45 back_upd.sh~
-rwx------  1 sn0m sn0m  3172 2009-05-22 12:19 back_up.sh
-rw-------  1 sn0m sn0m  3172 2009-05-22 12:18 back_up.sh~
-rwx------  1 sn0m sn0m   667 2009-05-07 13:02 clean_up.sh
-rw-------  1 sn0m sn0m   667 2009-05-06 23:00 clean_up.sh~
drwxr-xr-x  2 sn0m sn0m  4096 2009-05-15 19:58 dummy1
-rwx------  1 sn0m sn0m  2479 2009-01-11 23:06 emig1.sh
-rwx------  1 sn0m sn0m  2480 2009-01-10 17:11 emig1.sh~
-rwx------  1 sn0m sn0m  2438 2009-01-10 17:09 emig.sh
-rwx------  1 sn0m sn0m  2439 2009-01-10 17:09 emig.sh~
-rwx------  1 sn0m sn0m  2437 2009-01-11 23:05 emigtophits.sh
-rwx------  1 sn0m sn0m  2438 2009-01-10 17:06 emigtophits.sh~
drwx------  2 sn0m sn0m  4096 2009-05-20 22:32 exp
-rwx------  1 sn0m sn0m 12288 2008-12-26 12:57 .exp.sh.swp
-rwx------  1 sn0m sn0m  2493 2009-01-10 17:01 krastontop.sh
-rwx------  1 sn0m sn0m  2493 2009-01-10 17:00 krastontop.sh~
-rwx------  1 sn0m sn0m   483 2008-12-09 09:32 mpl_tar~
-rwx------  1 sn0m sn0m   501 2008-12-09 10:25 mpl_tir_liv~
-rwx------  1 sn0m sn0m   502 2008-12-17 17:59 mpl_tir_live.sh~
-rwx------  1 sn0m sn0m  2370 2009-01-10 16:17 nkpt.sh
-rwx------  1 sn0m sn0m  2371 2009-01-10 16:10 nkpt.sh~
-rwx------  1 sn0m sn0m  2384 2009-01-10 16:55 one_off.sh
-rwx------  1 sn0m sn0m  2397 2009-01-08 01:24 one_off.sh~
-rwx------  1 sn0m sn0m     1 2009-01-11 22:42 prova.sh
-rwx------  1 sn0m sn0m   151 2008-12-19 09:43 radio_url
-rwx------  1 sn0m sn0m   797 2008-12-10 18:05 record_aLive~
-rwx------  1 sn0m sn0m  2370 2009-01-10 16:53 record_aLive.sh
-rwx------  1 sn0m sn0m  2336 2009-01-10 16:51 record_aLive.sh~
-rwx------  1 sn0m sn0m   827 2008-12-10 18:06 record_liv_from_tirana~
-rwx------  1 sn0m sn0m  1785 2008-12-26 04:18 record_liv_from_tirana.sh~
-rwx------  1 sn0m sn0m  2469 2009-01-26 09:12 record_liv_from_tir.sh
-rwx------  1 sn0m sn0m  2469 2009-01-26 09:11 record_liv_from_tir.sh~
-rwx------  1 sn0m sn0m   806 2008-12-10 17:52 record_rikoshet~
-rwx------  1 sn0m sn0m  2419 2009-01-10 16:35 record_rikoshet.sh~
-rwx------  1 sn0m sn0m  2420 2009-04-16 04:55 rikoshet.sh
-rwx------  1 sn0m sn0m  2418 2009-01-10 16:37 rikoshet.sh~
-rwxr-xr-x  1 sn0m sn0m   233 2009-05-24 21:24 rsync.sh
-rw-r--r--  1 sn0m sn0m   234 2009-05-23 06:12 rsync.sh~
-rwx------  1 sn0m sn0m   151 2008-12-27 13:42 tar_program_list
-rwx------  1 sn0m sn0m   151 2008-12-10 17:21 tar_program_list~
-rwx------  1 sn0m sn0m  2384 2009-01-10 16:32 Tirana_live.sh
-rwx------  1 sn0m sn0m  2479 2009-01-08 01:26 Tirana_live.sh~
-rwx------  1 sn0m sn0m  1575 2008-12-30 02:42 wake -up.sh~
-rwx------  1 sn0m sn0m  2330 2009-01-10 16:26 wake_up.sh
-rwx------  1 sn0m sn0m  2331 2009-01-10 16:26 wake_up.sh~

---

### Post by sn0m on 2009-05-25
Thanks for your reply guys.
I've got it, apparently i used a password when generating keys and cron will ask for it. So I re-generated keys leaving password blank and it works a dream. No more files going missing as I hopefully will have them backed up in the desktop.
Chaps, can someone help me with a command line to check whether desktop is online or not, I'm planning to extend my script so that it asks first whether desktop is online, and if yes proceeds to execute rsync, otherwise aborts.
Thanks in advance
Sokol

---

