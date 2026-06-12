---
title: "problem  with sudo command"
date: 2011-02-04
forum: Desktop Environments
---

### Post by pdp2907 on 2011-02-04
Hi
I login into ubuntu as pdp2907.
I some time ago, to make my life easy changed the ownership of all the files in /usr/bin to pdp2907. 
if i do a ls -l /usr/bin/sudo

i get the following :

> ls -l /usr/bin/sudo
---s--x--x 2 pdp2907 root 127664 2010-08-31 16:39 /usr/bin/sudo

this leads to the following :
pdp2907@pdp2907-laptop:~$ sudo -s
sudo: must be setuid root

I tried changing the ownership back to root using the following:

pdp2907@pdp2907-laptop:~$ chown root:root /usr/bin/sudo
chown: changing ownership of `/usr/bin/sudo': Operation not permitte

how do i change back the ownership back to root so that i can go on with my sudo command  and help me install the different updates.

any help is really welcome

regards

Parag

---

### Post by anglican on 2011-02-04
> **pdp2907 said:**
> Hi
I login into ubuntu as pdp2907.
I some time ago, to make my life easy changed the ownership of all the files in /usr/bin to pdp2907.That certainly wont make your life easier!.. as you discovered. **_Never_** change ownership of anything in the system directories.
> **pdp2907 said:**
> if i do a ls -l /usr/bin/sudo

i get the following :

> ls -l /usr/bin/sudo
---s--x--x 2 pdp2907 root 127664 2010-08-31 16:39 /usr/bin/sudo

this leads to the following :
pdp2907@pdp2907-laptop:~$ sudo -s
sudo: must be setuid root

I tried changing the ownership back to root using the following:

pdp2907@pdp2907-laptop:~$ chown root:root /usr/bin/sudo
chown: changing ownership of `/usr/bin/sudo': Operation not permitte

how do i change back the ownership back to root so that i can go on with my sudo command  and help me install the different updates.

any help is really welcome

regards

ParagYou're going to have to boot from a live CD to fix this I suspect - though quite honestly I'd consider completely re-installing to make sure everything is back with correct ownership.

H

---

### Post by Forlong on 2011-02-04
Reinstalling is not necessary. Booting into the Recovery Console option in GRUB should be sufficient to change ownership back to root.

---

### Post by asmoore82 on 2011-02-04
> **anglican said:**
> That certainly wont make your life easier!.. as you discovered. **_Never_** change ownership of anything in the system directories.
[SIZE="3"]+1[/SIZE]
Pick anyone you want from this list:
1. Be careful what you wish for.
2. With great power, comes great responsibility.
3. Freedom means Free to do anything, even if it's not a good idea.
4. Linux is not Windows.

> **anglican said:**
> though quite honestly I'd consider completely re-installing to make sure everything is back with correct ownership
Again, I concur.
Those initial permissions are special on several system files.
A system with all files owned by your everyday account is an intruder's delight.
See #4 above - we need to keep it that way.

A few files with special properties are:
```
**$ ls -dl /tmp/ /bin/su /usr/bin/sudo /usr/bin/crontab /usr/bin/at**
-rwsr-xr-x  1 root   root     31100 2010-01-26 12:09 /bin/su
drwxrwxrwt 23 root   root     28672 2011-02-04 23:55 /tmp/
-rwsr-sr-x  1 daemon daemon   42812 2010-03-04 21:35 /usr/bin/at
-rwxr-sr-x  1 root   crontab  31656 2010-04-14 19:29 /usr/bin/crontab
-rwsr-xr-x  2 root   root    127664 2010-08-31 16:39 /usr/bin/sudo
**$ ls -l /usr/bin/ | grep rws**
-rwsr-xr-x 1 root   root      13820 2010-03-11 18:12 arping
-rwsr-sr-x 1 daemon daemon    42812 2010-03-04 21:35 at
-rwsr-xr-x 1 root   root      36180 2010-01-26 12:09 chfn
-rwsr-xr-x 1 root   root      31700 2010-01-26 12:09 chsh
-rwsr-xr-x 1 root   root      11214 2010-01-28 19:42 fileshareset
-rwsr-xr-x 1 root   root      53812 2010-01-26 12:09 gpasswd
-rwsr-xr-x 1 root   root       9644 2010-01-28 20:17 kgrantpty
-rwsr-xr-x 1 root   root       9676 2010-01-28 20:17 kpac_dhcp_helper
-rwsr-xr-x 1 root   lpadmin   13540 2010-06-18 11:08 lppasswd
-rwsr-xr-x 1 root   root      52092 2010-03-06 22:17 mtr
-rwsr-xr-x 1 root   root      26784 2010-01-26 12:09 newgrp
-rwsr-xr-x 1 root   root      37140 2010-01-26 12:09 passwd
-rwsr-xr-x 1 root   root      18048 2010-04-09 08:35 pkexec
-rwsr-xr-x 1 root   root       9672 2010-01-28 20:17 start_kdeinit
-rwsr-xr-x 2 root   root     127664 2010-08-31 16:39 sudo
-rwsr-xr-x 2 root   root     127664 2010-08-31 16:39 sudoedit
-rwsr-xr-x 1 root   root      13952 2010-03-11 18:12 traceroute6.iputils
-rwsr-sr-x 1 root   root       9664 2010-04-08 19:53 X
```

---

### Post by Forlong on 2011-02-05
Here's my list of files in /usr/bin not exclusively owned by root:
```
ls -l /usr/bin | grep -v "root   root"
total 215540
-rwsr-sr-x 1 daemon daemon     42752 2010-06-27 21:36 at
-rwxr-sr-x 1 root   tty         9708 2010-05-26 22:02 bsd-write
-rwxr-sr-x 1 root   shadow     45196 2010-09-03 12:28 chage
-rwxr-sr-x 1 root   crontab    30624 2010-08-25 01:01 crontab
-rwxr-sr-x 1 root   mail       13840 2010-05-18 17:08 dotlockfile
-rwxr-sr-x 1 root   shadow     18064 2010-09-03 12:28 expiry
-rwsr-xr-x 1 root   lpadmin     9404 2011-01-04 19:19 lppasswd
-rwxr-sr-x 1 root   mail        9668 2010-06-22 19:36 mail-lock
-rwxr-sr-x 1 root   mail        9668 2010-06-22 19:36 mail-touchlock
-rwxr-sr-x 1 root   mail        9668 2010-06-22 19:36 mail-unlock
-rwxr-sr-x 1 root   mlocate    30316 2010-03-24 11:16 mlocate
-rwxr-sr-x 1 root   utmp      340604 2010-06-18 14:42 screen
-rwxr-sr-x 1 root   ssh        95592 2011-01-09 13:11 ssh-agent
-rwxr-sr-x 1 root   tty         9728 2011-02-02 09:56 wall
```
In other words: you can safely revert ownership of every file back to root:root except these.

---

### Post by anglican on 2011-02-05
> **Forlong said:**
> Reinstalling is not necessary. Booting into the Recovery Console option in GRUB should be sufficient to change ownership back to root.I didn't say that it was *necessary* but in my opinion *advisable*. If anyone came to me at work with a system that they'd made such changes to (the ownership of _everything_ in /usr/bin) then I'd advise reinstall.

H

---

