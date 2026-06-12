---
title: "lots of problems after crash"
date: 2008-12-11
forum: General Help
---

### Post by readycarpenter on 2008-12-11
ok the other night installed a bunch of games via synaptic package manager, in the morning i ran world of padman and my system froze, nothing would respond, so i did a hard shutown, also pkg manager had not completed the instalation of the games i choose.

im running ubuntu 8.10 fully updated
3.0ghz  1.5gb ram

after restart alot of new problems 

firefox  
when i click a link i cannot hit the back button its greyed out, and search bar not work

thunderbird
! unable to write the email to mailbox. make sure the filesystem allows you write privilages, and you have enough disk space to copy the mailbox

terminal has no bash history(when i press up nothing there)

pidgin, when i run from terminal i get > Segmentation fault

thats just the surface, many games stopped working also, i do have 1.5gb free space on root fs, ill free some space see if that helps...
any idea what went wrong?

---

### Post by albinootje on 2008-12-11
If i were you i would boot in "recovery mode", and then run a forced filesystem check. To do that you need to know the names of the device-files for your Linux-partitions. For example /dev/sda1 /dev/sda3 etc.

If the Linux-partitions are ext3, then it would be for example :
fsck.ext3 -f /dev/sda3 
in case your Linux-partition is /dev/sda3

Apart from this you can already check the /lost+found/ directories on your Linux-partitions. If any files are in there already, that's an indication that there was a problem and you've lost some files.

(I'm been using the word "Linux-partitions" here, perhaps you have just one Linux-partition, but the same would apply of course).

One other thing you can do is to start a simple program like xcalc from a terminal, and see whether that shows some errors in the terminal.
Checking your logfiles like /var/log/syslog is also an idea, and try :
dmesg in a terminal (the command dmesg sometimes shows errors which do not show up in the most common logfiles).

---

### Post by readycarpenter on 2008-12-11
ok not enough free space on hd(even with 1.5gb free?,) duh problem fixed, the only app that pointed me in the right direction was thunderbird with 

error:
unable to write the email to mailbox. make sure the filesystem allows you write privilages, and you have enough disk space to copy the mailbox

---

