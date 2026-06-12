---
title: "fixing/recovering a partion"
date: 2006-09-28
forum: Desktop Environments
---

### Post by Trab on 2006-09-28
hello,
i have no freaking clue wat happend. i was playing around with some software (ldm), and messed up my ubuntu. thats rather irrelevent. basically i decided to reinstall over / (my /home is saved on a seperate partion) with edgy. i did that but it was acting weird. i rebooted and couldnt get anything to work. edgy, edgy liveCD, Dapper LiveCD, or my other HDD's windows. i figured out it had something to do with my sata hdd being plugged in. well now thats all resolved, and im in Dapper LiveCD, trying to install dapper to /dev/sda1 with /dev/sda3 back as my home partion. too bad /dev/sda3 is totally messed up :-/.

its an ext3 partion and ive been trying to REMOVE the journal settings from it as i have reason to believe thats the cause of the problem (i deleted /sda1 and /sda2 which could have messed up something basic like that).
to be honest i dont need the partion to be perfect, i just need to copy some files off it (i ironically backed most of my stuff up 2 days before for no reason).

```

ubuntu@ubuntu:~$ sudo e2fsck /dev/sda3
e2fsck 1.38 (30-Jun-2005)
/dev/sda3: Attempt to read block from filesystem resulted in short read while reading block 528

/dev/sda3: Attempt to read block from filesystem resulted in short read reading journal superblock

e2fsck: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/sda3

```

is the first error. googling around i found that trying this should help
```

ubuntu@ubuntu:~$ sudo tune2fs -f -O ^has_journal /dev/sda3
tune2fs 1.38 (30-Jun-2005)
The needs_recovery flag is set.  Please run e2fsck before clearing
the has_journal flag.

```
but because of the needs_recovery flag being set i cannot do so.

i then moved on in the howto for recoving partions, and it suggested
```

ubuntu@ubuntu:~$ sudo debugfs /dev/sda3
debugfs 1.38 (30-Jun-2005)
/dev/sda3: Can't read an inode bitmap while reading inode bitmap

```

supposedly if that doesnt work then the partion is fried. my only option is to use dd to copy it elsewhere and then try and recover.

i dont believe the harddrive is damaged itself, i was able to create /dev/sda1 and mkdir on it just fine, but its entirely possible the hard drive is broken (any suggestions to check?)
cheers much,
Trab

---

### Post by Trab on 2006-09-28
hate to bump, but i NEED an answer to this.
can i recover the data on that partition?
must i first dd it off and then attempt to recover?
any advice?
cheers,
Trab

---

### Post by Sef on 2006-09-28
Can you download and burn on your computer or another one?  If so, try [GParted.]("http://gparted.sourceforge.net/livecd.php")

---

### Post by Trab on 2006-09-28
...
yes, im currently using dapper LiveCD, it has GParted on it as well.
gparted allowed me to create a new sda1 but i cannot do anything with sda3.

---

