---
title: "Low disk space error yet I have 35GB free in File Browser"
date: 2010-11-10
forum: Desktop Environments
---

### Post by juliushibert63 on 2010-11-10
Every time I start my system I'm getting an error message that says

```
The volume "Filesystem root" has only 352.7 MB disk space remaining.
```

The weird thing is in my File Browser it's saying there's plenty of space 30+GB available. But I'm guesing it might be refering to the system partition. The system is setup as 8GB / ext4, I think a 2gb SWAP and then the rest for the remainder of the drive for things like HOME directories (was suggsted setup by an online tutorial).

I've found a few bits online talking about it's possible that files were deleted as root and so are in root's Trash. So I've used the following commands to clear it;

```
gksudo nautilus  
Press Ctrl+H to view hidden folders and then delete anything in;

PHP Code:
/root/.Trash
/.Trash-root
/root/.local/share/Trash  
```

But I've only cleared up around 300MB. As this is messing around on the root filesystem I'm wary to start deleting stuff as my linux system knowledge is still developing.

Any suggestions what else I might be able to delete as I'm sure there must be some rouge files somewhere as the machine is only used as a HTPC?

---

### Post by Viciou§ on 2010-11-10
Yes there's low disk space on the root file system, just as the warning says.
You can free some space by removing unused programs.
If it's a htpc you could remove openoffice for example.
Open synaptic package manager and sort by status and then installed.
For every program that you don't need: right click and select total remove.
(Not sure of the exact naming since I translated mine to english)

Edit: you can use the Disk Usage Analyzer (Menu: Accessories > Disk Usage Analyzer) to see what consumes the most space. Start it and then press Ctrl+F to analyze the filesystem.

---

### Post by sikander3786 on 2010-11-10
If you've got any personal files on the root partition, I would suggest you move them to some other place.

You can free up some space by cleaning the apt-get cache by

```
sudo apt-get clean
```

Some related threads.

[http://ubuntuforums.org/showthread.php?t=1037151](http://ubuntuforums.org/showthread.php?t=1037151)

[http://ubuntuforums.org/showthread.php?t=1032262](http://ubuntuforums.org/showthread.php?t=1032262)

---

### Post by juliushibert63 on 2010-11-10
Thanks for the links and suggestions. All very helpful especially in learning some new bits and pieces on the filesystem and in Terminal.

I tried cleaning out the apt-cache and configuring dpkg. But it hasn't really cleared up any space.

Digging around though it looks like the big chunk of space is being taken up in /var/log/

```
drwxr-xr-x 20 root              root        4096 2010-11-10 07:51 .
drwxr-xr-x 16 root              root        4096 2010-10-05 22:09 ..
drwxr-x---  2 root              adm         4096 2010-11-07 09:45 apache2
drwxr-xr-x  2 root              root        4096 2010-03-30 23:05 apparmor
drwxr-xr-x  2 root              root        4096 2010-11-01 07:34 apt
-rw-r--r--  1 root              root           0 2010-10-21 08:03 aptitude
-rw-r--r--  1 root              root         318 2010-10-20 20:03 aptitude.1.gz
-rw-r-----  1 syslog            adm        38314 2010-11-10 18:50 auth.log
-rw-r-----  1 syslog            adm        60483 2010-11-07 09:44 auth.log.1
-rw-r-----  1 syslog            adm         7365 2010-10-31 09:20 auth.log.2.gz
-rw-r-----  1 syslog            adm         8155 2010-10-24 09:32 auth.log.3.gz
-rw-r-----  1 syslog            adm         9973 2010-10-18 07:30 auth.log.4.gz
-rw-r-----  1 root              adm           31 2010-08-16 10:55 boot
-rw-r--r--  1 root              root         793 2010-11-10 07:22 boot.log
-rw-r--r--  1 root              root       41715 2010-08-16 10:56 bootstrap.log
-rw-rw----  1 root              utmp           0 2010-11-01 07:34 btmp
-rw-rw----  1 root              utmp         218 2010-10-23 00:32 btmp.1.gz
drwxr-xr-x  2 root              root        4096 2010-11-01 07:34 ConsoleKit
drwxr-xr-x  2 root              root        4096 2010-11-10 07:50 cups
-rw-r-----  1 syslog            adm       579937 2010-11-10 18:13 daemon.log
-rw-r-----  1 syslog            adm       427980 2010-11-07 09:44 daemon.log.1
-rw-r-----  1 syslog            adm        57655 2010-10-31 09:27 daemon.log.2.gz
-rw-r-----  1 syslog            adm        51750 2010-10-24 09:53 daemon.log.3.gz
-rw-r-----  1 syslog            adm        58860 2010-10-18 07:29 daemon.log.4.gz
-rw-r-----  1 syslog            adm       163607 2010-11-10 07:22 debug
-rw-r-----  1 syslog            adm       189655 2010-11-07 09:27 debug.1
-rw-r-----  1 syslog            adm        19765 2010-10-31 09:20 debug.2.gz
-rw-r-----  1 syslog            adm        17125 2010-10-24 09:32 debug.3.gz
-rw-r-----  1 syslog            adm        28844 2010-10-18 07:14 debug.4.gz
drwxr-xr-x  2 root              root        4096 2010-07-01 22:34 dist-upgrade
-rw-r-----  1 root              adm        52291 2010-11-10 07:22 dmesg
-rw-r-----  1 root              adm        52515 2010-11-09 23:04 dmesg.0
-rw-r-----  1 root              adm        13765 2010-11-09 18:02 dmesg.1.gz
-rw-r-----  1 root              adm        13793 2010-11-09 07:55 dmesg.2.gz
-rw-r-----  1 root              adm        13789 2010-11-09 07:21 dmesg.3.gz
-rw-r-----  1 root              adm        13820 2010-11-08 22:46 dmesg.4.gz
-rw-r--r--  1 root              root       53065 2010-11-10 18:37 dpkg.log
-rw-r--r--  1 root              root      378632 2010-10-31 18:35 dpkg.log.1
-rw-r--r--  1 root              root       98841 2010-09-29 21:31 dpkg.log.2.gz
-rw-r--r--  1 root              root       32032 2010-10-31 17:58 faillog
-rw-r--r--  1 root              root        2964 2010-10-28 08:04 fontconfig.log
drwxr-xr-x  2 root              root        4096 2010-08-16 10:55 fsck
drwxrwx--T  2 root              gdm         4096 2010-11-10 07:22 gdm
drwxr-xr-x  2 root              root        4096 2010-09-25 14:03 installer
-rw-r--r--  1 root              root           0 2010-10-28 08:01 jockey.log
-rw-r--r--  1 root              root       27495 2010-10-28 08:01 jockey.log.1
-rw-r--r--  1 root              root        4402 2010-09-26 00:39 jockey.log.2.gz
-rw-r-----  1 syslog            adm    915044990 2010-11-10 18:51 kern.log
-rw-r-----  1 syslog            adm      9836565 2010-11-07 09:45 kern.log.1
-rw-r-----  1 syslog            adm       348792 2010-10-31 09:33 kern.log.2.gz
-rw-r-----  1 syslog            adm       336426 2010-10-24 09:57 kern.log.3.gz
-rw-r-----  1 syslog            adm       459808 2010-10-18 07:45 kern.log.4.gz
-rw-rw-r--  1 root              utmp      292292 2010-11-10 18:50 lastlog
-rw-r-----  1 syslog            adm            0 2010-11-07 09:45 lpr.log
-rw-r-----  1 syslog            adm          134 2010-11-05 07:40 lpr.log.1
-rw-r-----  1 syslog            adm          104 2010-11-01 07:15 lpr.log.2.gz
-rw-r-----  1 syslog            adm          105 2010-10-20 17:43 lpr.log.3.gz
-rw-r-----  1 syslog            adm          104 2010-10-06 07:13 lpr.log.4.gz
-rw-r-----  1 syslog            adm            0 2010-09-25 14:04 mail.err
-rw-r-----  1 syslog            adm            0 2010-09-25 14:04 mail.info
-rw-r-----  1 syslog            adm            0 2010-09-25 14:04 mail.log
-rw-r-----  1 syslog            adm            0 2010-09-25 14:04 mail.warn
-rw-r-----  1 syslog            adm    914892330 2010-11-10 18:51 messages
-rw-r-----  1 syslog            adm      9657838 2010-11-07 09:45 messages.1
-rw-r-----  1 syslog            adm       319661 2010-10-31 09:34 messages.2.gz
-rw-r-----  1 syslog            adm       313136 2010-10-24 09:57 messages.3.gz
-rw-r-----  1 syslog            adm       421710 2010-10-18 07:46 messages.4.gz
drwxr-xr-x  2 mpd               audio       4096 2010-11-07 09:45 mpd
drwxr-s---  2 mysql             adm         4096 2010-11-10 07:50 mysql
-rw-r-----  1 mysql             adm            0 2010-09-25 19:12 mysql.err
-rw-r-----  1 mysql             adm            0 2010-11-10 07:50 mysql.log
-rw-r-----  1 mysql             adm           20 2010-11-09 07:39 mysql.log.1.gz
-rw-r-----  1 mysql             adm           20 2010-11-08 08:08 mysql.log.2.gz
-rw-r-----  1 mysql             adm           20 2010-11-07 09:45 mysql.log.3.gz
-rw-r-----  1 mysql             adm           20 2010-11-06 10:49 mysql.log.4.gz
-rw-r-----  1 mysql             adm           20 2010-11-05 07:57 mysql.log.5.gz
-rw-r-----  1 mysql             adm           20 2010-11-04 07:39 mysql.log.6.gz
-rw-r-----  1 mysql             adm           20 2010-11-03 08:12 mysql.log.7.gz
drwxrwsr-x  2 mythtv            mythtv      4096 2010-09-25 19:13 mythtv
drwxr-xr-x  2 root              root        4096 2010-09-25 14:04 news
drwxr-xr-x  2 ntp               ntp         4096 2010-04-09 04:14 ntpstats
-rw-r--r--  1 root              root        8117 2010-11-10 07:22 pm-powersave.log
-rw-r--r--  1 root              root       24077 2010-11-01 07:16 pm-powersave.log.1
-rw-r--r--  1 root              root         390 2010-10-01 07:32 pm-powersave.log.2.gz
drwxrwxrwt  2 root              root        4096 2010-11-07 09:45 pms-linux
-rw-r--r--  1 root              root           0 2010-11-01 07:34 pm-suspend.log
-rw-r--r--  1 root              root       17561 2010-10-17 19:35 pm-suspend.log.1
-rw-r--r--  1 root              root        2006 2010-09-26 09:29 pm-suspend.log.2.gz
-rw-r--r--  1 root              root           0 2010-08-16 10:56 pycentral.log
drwxr-xr-x  3 root              root        4096 2010-11-08 22:58 samba
drwxr-xr-x  2 speech-dispatcher root        4096 2010-04-15 17:29 speech-dispatcher
-rw-r-----  1 syslog            adm       193764 2010-11-10 18:51 syslog
-rw-r-----  1 syslog            adm      1198694 2010-11-10 07:51 syslog.1
-rw-r-----  1 syslog            adm     36631073 2010-11-09 07:39 syslog.2.gz
-rw-r-----  1 syslog            adm       224253 2010-11-08 08:08 syslog.3.gz
-rw-r-----  1 syslog            adm       338098 2010-11-07 09:45 syslog.4.gz
-rw-r-----  1 syslog            adm        94884 2010-11-06 10:48 syslog.5.gz
-rw-r-----  1 syslog            adm       340225 2010-11-05 07:56 syslog.6.gz
-rw-r-----  1 syslog            adm        65802 2010-11-04 07:39 syslog.7.gz
-rw-r--r--  1 root              root      257923 2010-11-10 07:22 udev
-rw-r-----  1 syslog            adm            0 2010-09-25 14:04 ufw.log
drwxr-xr-x  2 root              root        4096 2010-04-29 16:02 unattended-upgrades
-rw-r-----  1 syslog            adm          744 2010-11-10 07:22 user.log
-rw-r-----  1 syslog            adm          823 2010-11-07 09:26 user.log.1
-rw-r-----  1 syslog            adm          215 2010-10-31 09:20 user.log.2.gz
-rw-r-----  1 syslog            adm          797 2010-10-24 09:32 user.log.3.gz
-rw-r-----  1 syslog            adm          356 2010-10-18 07:14 user.log.4.gz
-rw-rw-r--  1 root              utmp      116352 2010-11-10 18:50 wtmp
-rw-rw-r--  1 root              utmp        9622 2010-11-01 07:17 wtmp.1.gz
-rw-r--r--  1 root              root       27501 2010-11-10 07:22 Xorg.0.log
-rw-r--r--  1 root              root       27852 2010-11-10 00:07 Xorg.0.log.old
-rw-r--r--  1 root              root        7059 2010-11-05 07:41 Xorg.1.log
-rw-r--r--  1 root              root        2505 2010-10-15 22:33 Xorg.1.log.old
-rw-r--r--  1 root              root        7059 2010-11-05 07:41 Xorg.2.log
-rw-r--r--  1 root              root        7059 2010-09-30 08:15 Xorg.2.log.old
-rw-r--r--  1 root              root        7059 2010-11-05 07:41 Xorg.3.log
-rw-r--r--  1 root              root        7059 2010-09-30 08:15 Xorg.3.log.old
-rw-r--r--  1 root              root        7059 2010-11-05 07:41 Xorg.4.log
-rw-r--r--  1 root              root        7059 2010-09-30 08:15 Xorg.4.log.old
-rw-r--r--  1 root              root        7059 2010-11-05 07:41 Xorg.5.log
-rw-r--r--  1 root              root        7059 2010-09-30 08:15 Xorg.5.log.old
-rw-r--r--  1 root              root       39578 2010-11-05 07:44 Xorg.failsafe.log
-rw-r--r--  1 root              root       39676 2010-09-30 08:17 Xorg.failsafe.log.old

```

inparticular by these two files which are over 500M each

```
/var/log/messages
/var/log/kern.log

```

But reading through some of those posts it seems to indicate only clearing out *.gz logs as these are safe to bin because they've been archived, Does anyone know if I can clear these two files or not?

---

### Post by dFlyer on 2010-11-10
You might want to read man logrotate and make some modification to the logrotate.conf located /etc.

---

### Post by juliushibert63 on 2010-11-10
It also looks like there's a few large files in here. Which looks to be a Trash directory on my external drive. Is it ok to delete the files in here or not?

```
72188151 255236 -rw-rw-rw-   1 gil      gil      261099444 Nov  6 16:43 ./media/Media/.Trash-1000/expunged/
```

They're just par2 files and a few cryptic numbered files.

---

### Post by Viciou§ on 2010-11-10
The numbers you see are in bytes.
The highest number (579973) equals ~580 kB.

Nothing to really be concerned about :)
I know that there are something tied to teletext in docs that takes up a couple of hundred MB.
Purge the corresponding packages if you don't need them.

---

### Post by juliushibert63 on 2010-11-10
> **Viciou§ said:**
> Purge the corresponding packages if you don't need them.

Not quite sure which packages you're referring to?

---

### Post by blackmail on 2010-11-10
apt-get autoremove also helps

---

### Post by cforput on 2010-12-09
I have the same problem and will used this information to try and fix it but one of juliushibert63's other questions was overlooked as everyone tried to offer fixes.

juliushibert63 also asked why the message is even happening because he had 35GB of disk space free. 

I have a similar circumstance where I have over 60GB free on my drive. So why does the message even appear?

---

### Post by blackmail on 2011-03-01
Regarding the second question could it not be that he has two partitions?

/ (the root partition)
and
/home (...duh)

and he is referring to the fact that he still has that space available on the /home partition?

If this is right then the answer would be straightforward because the root needs to be cleaned if not then we need to look further...

---

