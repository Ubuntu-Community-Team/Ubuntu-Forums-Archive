---
title: "chmod/permissions bug?"
date: 2005-04-23
forum: Desktop Environments
---

### Post by brickbat on 2005-04-23
Hi, I am trying to change the permissions on a drive that is empty,

Here is the listing of my attempt

brickbat@lpc1:/media$ ls -l
total 64
drwxrwxrwx  17 root root  4096 1970-01-01 01:00 boot
lrwxrwxrwx   1 root root     6 2005-04-04 02:10 cdrom -> cdrom0
drwxrwxrwx   2 root root  4096 2005-04-04 02:10 cdrom0
drwxrwxrwx   2 root root  4096 2005-04-04 02:10 cdrom1
drwxrwxrwx   7 root root  4096 1970-01-01 01:00 data
drwxrwxrwx   3 root root  8192 1970-01-01 01:00 dloads
lrwxrwxrwx   1 root root     7 2005-04-04 02:10 floppy -> floppy0
drwxrwxrwx   2 root root  4096 2005-04-04 02:10 floppy0
drwxrwxrwx  12 root root  8192 1970-01-01 01:00 library
drwxrwxrwx   9 root root  4096 2005-04-23 19:07 lindata
drwxrwxrwx  10 root root  4096 1970-01-01 01:00 music
drwxr-xr-x   2 root root  4096 2005-04-23 19:30 scratch
drwxrwxrwx  12 root root 16384 1970-01-01 01:00 winxp
brickbat@lpc1:/media$ sudo chmod +gw scratch
brickbat@lpc1:/media$ ls -l
total 64
drwxrwxrwx  17 root root  4096 1970-01-01 01:00 boot
lrwxrwxrwx   1 root root     6 2005-04-04 02:10 cdrom -> cdrom0
drwxrwxrwx   2 root root  4096 2005-04-04 02:10 cdrom0
drwxrwxrwx   2 root root  4096 2005-04-04 02:10 cdrom1
drwxrwxrwx   7 root root  4096 1970-01-01 01:00 data
drwxrwxrwx   3 root root  8192 1970-01-01 01:00 dloads
lrwxrwxrwx   1 root root     7 2005-04-04 02:10 floppy -> floppy0
drwxrwxrwx   2 root root  4096 2005-04-04 02:10 floppy0
drwxrwxrwx  12 root root  8192 1970-01-01 01:00 library
drwxrwxrwx   9 root root  4096 2005-04-23 19:07 lindata
drwxrwxrwx  10 root root  4096 1970-01-01 01:00 music
drwxr-xr-x   2 root root  4096 2005-04-23 19:30 scratch
drwxrwxrwx  12 root root 16384 1970-01-01 01:00 winxp
brickbat@lpc1:/media$

---

### Post by alastair on 2005-04-23
sudo chmod +gw scratch

What's the "g" stand for? Are you sure this syntax is right?

---

### Post by brickbat on 2005-04-23
+ means add permission
g stands for group
w stands for write

thanks for the clue...only bug was in my brain!

The correct syntax is 

chmod g+w

now i wish i could delete the thread.  I feel silly.

ciao
bb

---

### Post by doc_holiday on 2005-11-29
Is it possible to give somebody write permission but not delete?

---

