---
title: "error"
date: 2012-11-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vaibhav yadav on 2012-11-25
sir ,


[xxxxx.xxxxxx]end_request: I/O error dev sda ,sector xxxxxx.


how to recover it and create backup.
i have tried sudo fdisk-l.

---

### Post by ajgreeny on 2012-11-25
[LIST=1]
[*]Where and when does this error appear?
[*]Is it a new problem that has suddenly appeared following a system crash or similar?
[*]The command is actually **sudo fdisk -l** so you missed the space after **fdisk**.
[*]That command does nothing except show the partitions on the disk; it does nothing more.
[/LIST]

---

### Post by vaibhav yadav on 2012-11-25
sir i have tried the same command but nothing happened...

I CANNOT LOGIN IN TERMINAL WITH AMINISTRATIVE USERNAME .....

NOR ANY COMMMAND EXECUTING LIKE SHUTDOWN....

ERROR IS [XXXXX.XXXXXX]end_request:I/O ,dev sda ,sector xxxxxxxx

---

### Post by vaibhav yadav on 2012-11-25
the warning on console screen is 
*** THIS VERSION OF THE ClamAV engine is outdated.    ***
not allowing to execute any command on terminal.....

error.

[xxxx.xxxxxx]end_request:I/O dev,sda , sector xxxxxx

---

### Post by vaibhav yadav on 2012-11-25
> **ajgreeny said:**
> [list=1]
[*]where and when does this error appear?
[*]is it a new problem that has suddenly appeared following a system crash or similar?
[*]the command is actually **sudo fdisk -l** so you missed the space after **fdisk**.
[*]that command does nothing except show the partitions on the disk; it does nothing more.
[/list]



its a problem followed by system crash.......

---

### Post by ajgreeny on 2012-11-26
Run a live system from CD or USB and run the terminal command ```
sudo e2fsck /dev/sda1
``` and then for all other ext4 sda# partitions, but not the swap partition.

That command may well report errors and allow you to correct them.  Report back here any results, good or bad, and let's see if we can get you up and running again.

---

