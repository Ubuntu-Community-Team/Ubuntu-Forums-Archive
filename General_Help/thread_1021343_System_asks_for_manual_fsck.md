---
title: "System asks for manual fsck"
date: 2008-12-25
forum: General Help
---

### Post by Taidgh on 2008-12-25
Hi, today I got a new (second hand)laptop with a fresh install of Ubuntu 8.10. After installing a theme and messing around a bit (nothing unusual) I tried to install AssaultCube. It crashed, and gave me a screen saying it could not locate X (windows), before restarting. Now whenever I turn it on, it goes to a message about cleaning up after an unclean reboot, before crashing halfway through the process. It than gives me this (on a terminal screen):
```
Checking drive /dev/sda1: 46% (stage 1/5, 143/214)
Checking drive /dev/sda1: 47% (stage 1/5, 146/214)
Checking drive /dev/sda1: 48% (stage 1/5, 147/214)
Checking drive /dev/sda1: 48% (stage 1/5, 148/214)
Checking drive /dev/sda1: 49% (stage 1/5, 151/214)
Checking drive /dev/sda1: 49% (stage 1/5, 152/214)
Checking drive /dev/sda1: 50% (stage 1/5, 153/214)
Checking drive /dev/sda1: 50% (stage 1/5, 155/214)
/dev/sda1: Inodes that were part of a corrupted orphan linked list found.

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
     (i.e, without -a or -p options)
Checking drive /dev/sda1: 51% (stage 1/5, 157/214)
fsck died wih exit status 4
                                                    [fail]
* An automatic file system check (fsck) of the root filesystem failed.
A manual fsck must be performed, then the system restarted.
The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.
* The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D
to terminate the maintenance shell and restart the system.
Give root password for maintenance 
(or type Control-D to continue):_ 
```

I tried restarting with control-d, and got the same thing.
I wouldn't know how to effectively run fsck on the system. What am I supposed to do? I miss my friendly mac :(

---

### Post by taurus on 2008-12-25
Boot from the LiveCD and open a terminal and run

Applications -> Accessories -> Terminal
```
sudo fsck /dev/sda1
```

---

### Post by Taidgh on 2008-12-25
If I can do that from the maintenance shell provided by my system, should I? As it would be quicker than burning a live cd.

---

### Post by taurus on 2008-12-25
> 
Give root password for maintenance 
(or type Control-D to continue):_


Do you have root password?

---

### Post by Taidgh on 2008-12-25
Yes, so I went ahead with the fsck, and said yes to everything. This better leave me with a usable laptop.

---

### Post by taurus on 2008-12-25
Type in the root password.  It will drop you to a prompt and you can run **fsck /dev/sda1** from there.  When it's done, you can exit it and it would boot normally.

---

### Post by Taidgh on 2008-12-25
It worked! Thanks, the scary terminal screen and talk of manual maintenance just scared me. Laptop seems to be working fine now.

---

