---
title: "Log Overflowing with read/write wait queue active"
date: 2010-08-09
forum: Desktop Environments
---

### Post by perhaad on 2010-08-09
Hello Everyone,

I am having some trouble with Ubuntu 9.10 

For some reason my logs keep overflowing. I have attached a screenshot and a snippet of my kernel log too.


```

Aug  9 18:52:04 eowyn kernel: [180754.977296] tty_release_dev: pts4: read/write wait queue active!
Aug  9 18:52:04 eowyn kernel: [180754.977302] tty_re55454545454545545554545545455455454.95454545554545555455455455545545545554545545455545455454554555455545545455455554554545545545554554555455554545554545554554554554555455545555545554554554.554555455455455455455554554554554555455455455545455554555455545545555455545545554555545555545545455545454555455555454554554545545555454554555455555554554554555554545554555454555455455554555545455455455455455454555455545554555455554545554545545455545554545545455455455555455454555545555455454554555545554545455455554555454554555455545545545545545545545554555554555455545545554555455455554555545554545555545555455554555545555454554545545545555455454554555554554545455454555554554554545554555545455545455455555455455455554555455555554545545545545554554554545455454555455545545545554545554545554545554545554555455545455455455545455545554545554554545554545555455455454554555545545554545545545555454545555455555454555454554555455555455455455545554545554.981767] tty_releas5454555545554554555
Aug  9 18:52:04 eowyn kernel: 455545455455545455455455545555554555545455554545554.982062] tty_release_dev: pts4: read/write wait queue active!
Aug  9 18:52:04 eowyn kernel: [180754.982067] tty_release_dev: pts4: read/write wait queue active!
Aug  9 18:52:04 eowyn kernel: [180754.982073] tty_release_dev: pts4: read/write wait queue active!
Aug  9 18:52:04 eowyn kernel: [180754.982079] tty_release_dev: pts4: read/write wait queue active!
Aug  9 18:52:04 eowyn kernel: [180754.982085] tty_release_dev: pts4: read/write wait queue active!
Aug  9 18:52:04 eowyn kernel: [180754.982091] tty_release_dev: pts4: read/write wait queue active!

```

I looked into /dev/pts/ and there is no pts4 present, Can anyone suggest any steps I can take ?
I also looked at the processes with top and have attached a screenshot, The main running process is dd, I dont understand what is it trying to do.

Syslog too has the same messages

```

Aug  9 19:26:39 eowyn kernel: [182829.80929.853875] tty_release_dev: pts4: read/write wait queue active!
Aug  9 19:26:39 eowyn kernel: [182829.853878] tty_release_dev: pts4: read/write wait queue active!
Aug  9 19:26:39 eowyn kernel: [182829.853881] tty_release_dev: pts4: read/write wait queue active!
Aug  9 19:26:39 eowyn kernel: [182829.853883] tty_release_dev: pts4: read/write wait queue active!
Aug  9 19:26:39 eowyn kernel: [182829.853886] tty_release_dev: pts4: read/write wait queue active!
Aug  9 19:26:39 eowyn kernel: [182829.853889] tty_release_dev: pts4: read/write wait queue active!

```

I can reboot the system but I have to do a hard reboot because these messages stop the reboot while they fill up the logs. I dont know when these messages start. I am running. 

Linux 2.6.31-22-generic #61-Ubuntu


My mounted filesystems are below. dev/sda5 is the one filling up

```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             51137684  39979232   8560748  83% /
udev                   2027748       272   2027476   1% /dev
none                   2027748      1228   2026520   1% /dev/shm
none                   2027748        88   2027660   1% /var/run
none                   2027748         0   2027748   0% /var/lock
none                   2027748         0   2027748   0% /lib/init/rw
/dev/sda2            103216948  31491664  66482072  33% /home


```

I would appreciate any help.

Thank You,
Perhaad

---

### Post by bradshaw_k1te on 2011-01-07
I have three identical, clonezilla'ed, notebooks running 10.04.1 LTS and one of them is getting into this sick, spewing mode about every three days.  This requires a hard boot to get it back running.  

Perhaad, How did you get around this problem?

Thanks, Bradshaw

---

### Post by perhaad on 2011-01-12
Hello Bradshaw,

I never did get around to finding the root of the problem.
I initially thought that it is triggered when the GPU driver misbehaves but that doesnt make sense for me because the problem happens with both AMD and Nvidia GPUs. I have not chased it too much more because it doesnt happen very often for me.

I would appreciate it if some one could point me to ways to see what process is triggering this

--
Perhaad

---

