---
title: "The volume &quot;filesystem root&quot; has only X bytes disk space remaining"
date: 2012-08-17
forum: Desktop Environments
---

### Post by cmygeHm on 2012-08-17
Hello!
Please help me.
Throws this error message: "The volume 'filesystem root' has only X bytes disk space remaining". Where X near 1 Gb. Capacity on the first device is 50Gb. Really used near 20Gb.

root@gafarov-pc:/usr/bin# du -hx --max-depth=1 / | sort -h

du: cannot access `/home/me/.gvfs': Permission denied
0   /dev
0   /proc
0   /run
0   /sys
4.0K   /cdrom
4.0K   /lib64
4.0K   /mnt
4.0K   /selinux
4.0K   /srv
8.0K   /media
16K   /lost+found
176K   /root
792K   /tmp
8.8M   /bin
9.2M   /sbin
15M   /etc
15M   /lib32
24M   /boot
125M   /opt
224M   /lib
1.8G   /home
3.3G   /usr
12G   /var
17G   /

It seems, trouble in ~/.gvfs, I don't know what is it.
What another way to understand what reason of trouble?
OS Ubuntu 11.10

---

### Post by spjackson on 2012-08-17
Don't worry about .gvfs - that is normal. Please post the output of these commands.
```

df -h
df -i

```

---

### Post by cmygeHm on 2012-08-17
> **spjackson said:**
> Don't worry about .gvfs - that is normal. Please post the output of these commands.
```

df -h
df -i

```

```

root@gafarov-pc:/home/me# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              49G   17G   29G  37% /
udev                  1.5G  4.0K  1.5G   1% /dev
tmpfs                 604M  836K  603M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  1.5G  9.7M  1.5G   1% /run/shm
/dev/sda3             406G   10G  375G   3% /home/me/Workspace

root@gafarov-pc:/home/me# df -i
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sda1            3203072  231818 2971254    8% /
udev                  384211     501  383710    1% /dev
tmpfs                 386190     416  385774    1% /run
none                  386190       1  386189    1% /run/lock
none                  386190      19  386171    1% /run/shm
/dev/sda3            27009024     143 27008881    1% /home/me/Workspace

```

---

### Post by spjackson on 2012-08-17
Well, clearly the filesystem is far from full. Do you get this message now or does it come up intermittently? It's possible that something is creating very large temporary files that are eventually removed.

12GB for /var seems pretty high. The most common things to use a lot of disk space in /var are a) installing and updating packages in /var/cache b) excessive logging in /var/log. Less commonly, /var/spool, /var/mail, /var/tmp. Additionally, if the machine is a server, there may be websites and/or databases in /var.

```

du -hx --max-depth=1 /var | sort -h

```However, the current content of /var does not explain the message you are getting.

---

### Post by cmygeHm on 2012-08-17
This message does come up intermittently, 2-3 two times in day.
It is very large postgresql db files. I think it is normal. I can't understand what big files (30Gb) can be temporary created?

```
4.0K	/var/crash
4.0K	/var/games
4.0K	/var/local
4.0K	/var/mail
4.0K	/var/opt
96K	/var/spool
9.3M	/var/backups
11M	/var/tmp
19M	/var/log
575M	/var/cache
754M	/var/www
16G	/var/lib
17G	/var

```
It is more then 12Gb here bcz I restored dump. When I wrote first message it was 12GB. New db restored right now is 16Gb.

---

### Post by cmygeHm on 2012-08-17
Right now:
```

root@gafarov-pc:/var/www/h/Service/Holder/Scripts/Vkontakte# du -hx --max-depth=1 / |sort -h
du: cannot access `/home/me/.gvfs': Permission denied
0	/dev
0	/proc
0	/run
0	/sys
4.0K	/cdrom
4.0K	/lib64
4.0K	/mnt
4.0K	/selinux
4.0K	/srv
8.0K	/media
16K	/lost+found
144K	/tmp
180K	/root
8.8M	/bin
9.1M	/sbin
15M	/etc
15M	/lib32
24M	/boot
125M	/opt
224M	/lib
1.7G	/home
3.3G	/usr
17G	/var
23G	/

```

---

### Post by cmygeHm on 2012-08-20
Anybody can help me? Please...

---

### Post by spjackson on 2012-08-20
You need to see whether the disk is actually filling up, or whether the message is incorrect. I think it unlikely that the message is incorrect, but it's always possible.

Whenever you have posted, the disk has been nowhere near full. You need to do your df and du commands when the message appears. If these don't catch it, then perhaps have a cron job to log df and du to a file once a minute. Something like this:

sudo crontab -e
```

* * * * * (date ; df /) >> /var/log/df.log
* * * * * (date ; du -hx --max-depth=1 / | sort -h) >> /var/log/du1.log
* * * * * (date ; du -hx --max-depth=1 /var | sort -h) >> /var/log/du2.log

```Since you are running a database installation of several gigabytes, my money would be on an errant query - probably an unintended cartesian product. Is there any relevant message in the postrgesql log? (probably in /var/log/postgresql/ )

---

### Post by cmygeHm on 2012-08-20
ok, I will set jobs in cron.
So big database bcz I develop one program and use outside database. It db really very big.

---

### Post by cmygeHm on 2012-08-20
It is strange:
```

13G	/var
18G	/
Mon Aug 20 13:50:01 MSK 2012
0	/dev
0	/proc
0	/run
0	/sys
4.0K	/cdrom
4.0K	/lib64
4.0K	/mnt
4.0K	/selinux
4.0K	/srv
8.0K	/media
16K	/lost+found
136K	/tmp
184K	/root
8.8M	/bin
9.1M	/sbin
15M	/etc
15M	/lib32
24M	/boot
125M	/opt
224M	/lib
1.7G	/home
3.3G	/usr
13G	/var
18G	/
Mon Aug 20 13:55:01 MSK 2012
0	/dev
0	/proc
0	/run
0	/sys
4.0K	/cdrom
4.0K	/lib64
4.0K	/mnt
4.0K	/selinux
4.0K	/srv
8.0K	/media
16K	/lost+found
136K	/tmp
184K	/root
8.8M	/bin
9.1M	/sbin
15M	/etc
15M	/lib32
24M	/boot
125M	/opt
224M	/lib
1.7G	/home
3.3G	/usr
13G	/var
18G	/
Mon Aug 20 14:00:02 MSK 2012
0	/dev
0	/proc
0	/run
0	/sys
4.0K	/cdrom
4.0K	/lib64
4.0K	/mnt
4.0K	/selinux
4.0K	/srv
8.0K	/media
16K	/lost+found
136K	/tmp
184K	/root
8.8M	/bin
9.1M	/sbin
15M	/etc
15M	/lib32
24M	/boot
125M	/opt
224M	/lib
1.7G	/home
3.3G	/usr
13G	/var
18G	/
Mon Aug 20 14:05:02 MSK 2012
0	/dev
0	/proc
0	/run
0	/sys
4.0K	/cdrom
4.0K	/lib64
4.0K	/mnt
4.0K	/selinux
4.0K	/srv
8.0K	/media
16K	/lost+found
136K	/tmp
184K	/root
8.8M	/bin
9.1M	/sbin
15M	/etc
15M	/lib32
24M	/boot
125M	/opt
224M	/lib
1.7G	/home
3.3G	/usr
13G	/var
18G	/
Mon Aug 20 14:10:01 MSK 2012
0	/dev
0	/proc
0	/run
0	/sys
4.0K	/cdrom
4.0K	/lib64
4.0K	/mnt
4.0K	/selinux
4.0K	/srv
8.0K	/media
16K	/lost+found
136K	/tmp
184K	/root
8.8M	/bin
9.1M	/sbin
15M	/etc
15M	/lib32
24M	/boot
125M	/opt
224M	/lib
1.7G	/home
3.3G	/usr
13G	/var
18G	/
Mon Aug 20 14:15:02 MSK 2012
0	/dev
0	/proc
0	/run
0	/sys
4.0K	/cdrom
4.0K	/lib64
4.0K	/mnt
4.0K	/selinux
4.0K	/srv
8.0K	/media
16K	/lost+found
136K	/tmp
184K	/root
8.8M	/bin
9.1M	/sbin
15M	/etc
15M	/lib32
24M	/boot
125M	/opt
224M	/lib
1.7G	/home
3.3G	/usr
13G	/var
18G	/
Mon Aug 20 14:20:01 MSK 2012
0	/dev
0	/proc
0	/run
0	/sys
4.0K	/cdrom
4.0K	/lib64
4.0K	/mnt
4.0K	/selinux
4.0K	/srv
8.0K	/media
16K	/lost+found
136K	/tmp
184K	/root
8.8M	/bin
9.1M	/sbin
15M	/etc
15M	/lib32
24M	/boot
125M	/opt
224M	/lib
1.7G	/home
3.3G	/usr
13G	/var
18G	/

```

AND in this time:
```

/dev/sda1             50395844  32932236  14903608  69% /
Mon Aug 20 13:46:01 MSK 2012
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             50395844  33215992  14619852  70% /
Mon Aug 20 13:47:01 MSK 2012
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             50395844  33551632  14284212  71% /
Mon Aug 20 13:48:01 MSK 2012
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             50395844  33853420  13982424  71% /
Mon Aug 20 13:50:01 MSK 2012
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             50395844  34395428  13440416  72% /
Mon Aug 20 13:55:01 MSK 2012
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             50395844  36052812  11783032  76% /
Mon Aug 20 14:00:02 MSK 2012
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             50395844  37764636  10071208  79% /
Mon Aug 20 14:05:02 MSK 2012
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             50395844  39437880   8397964  83% /
Mon Aug 20 14:10:01 MSK 2012
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             50395844  41111448   6724396  86% /
Mon Aug 20 14:15:02 MSK 2012
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             50395844  42781360   5054484  90% /
Mon Aug 20 14:20:01 MSK 2012
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             50395844  44438256   3397588  93% /
Mon Aug 20 14:25:02 MSK 2012
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             50395844  46112620   1723224  97% /

```
I restared PC and it is again
```

Mon Aug 20 14:35:01 MSK 2012
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             50395844  18579648  29256196  39% /

```

---

### Post by spjackson on 2012-08-20
There are several reasons why df can show much higher values than du, but we can rule out some of these possibilities because the problem goes away when you reboot, and then the problem repeats.

This usually means that a file is being written to that has been deleted. Try monitoring as follows.

sudo crontab -e
```

 * * * * (date ; lsof | egrep 'COMMAND|deleted') >> /var/log/lsof.log

```If you find a process that is doing this, especially if SIZE/OFF column is large, then note the PID from the first column and do
```

ps -F pid_number

```substituting the PID for pid_number.

Did you look at the postrgesql log?

A query such as this which does an unintended cartesian product will result in a huge temporary file if there are many rows in the table.
```

select a.* from mytable a, mytable b

```

---

### Post by GeorgeWhite5 on 2012-08-20
> **cmygeHm said:**
> Hello!
Please help me.
Throws this error message: "The volume 'filesystem root' has only X bytes disk space remaining". Where X near 1 Gb. Capacity on the first device is 50Gb. Really used near 20Gb.

root@gafarov-pc:/usr/bin# du -hx --max-depth=1 / | sort -h

du: cannot access `/home/me/.gvfs': Permission denied
0   /dev
0   /proc
0   /run
0   /sys
4.0K   /cdrom
4.0K   /lib64
4.0K   /mnt
4.0K   /selinux
4.0K   /srv
8.0K   /media
16K   /lost+found
176K   /root
792K   /tmp
8.8M   /bin
9.2M   /sbin
15M   /etc
15M   /lib32
24M   /boot
125M   /opt
224M   /lib
1.8G   /home
3.3G   /usr
12G   /var
17G   /

It seems, trouble in ~/.gvfs, I don't know what is it.
What another way to understand what reason of trouble?
OS Ubuntu 11.10

How strange... how old is the harddrive in question?

**EDIT:** You aren't connecting to remote servers (using Nautilus or another gnome program), are you? If you don't, then it is nothing to do with .gvfs

---

### Post by GeorgeWhite5 on 2012-08-20
This may help:

You can change where PostregreSQL stores its temporary files (through a variable). I found it here:

[http://archives.postgresql.org/pgsql-general/2008-10/msg01406.php]("http://archives.postgresql.org/pgsql-general/2008-10/msg01406.php")

You could possibly change this (or get the variable)?

---

### Post by cmygeHm on 2012-08-21
spjackson, thank you very much!
Excuse me, please =)
One day I play with mplayer and cron =)
I past task for mplayer to start play in on time. And I found
```

cron      13577       root    5u      REG                8,1 6284358798     786599 /tmp/tmpfUQsuAA (deleted)
sh        13578         me    1u      REG                8,1 6284360256     786599 /tmp/tmpfUQsuAA (deleted)
sh        13578         me    2u      REG                8,1 6284360418     786599 /tmp/tmpfUQsuAA (deleted)
mplayer   13579         me    1u      REG                8,1 6284373783     786599 /tmp/tmpfUQsuAA (deleted)
mplayer   13579         me    2u      REG                8,1 6284373864     786599 /tmp/tmpfUQsuAA (deleted)

```
when tried ```
lsof | egrep 'COMMAND|deleted'
```
I killed this process and space on hard disk released =)
Thank you very much =)
Of course I removed task for mplayer from crontab.

---

### Post by spjackson on 2012-08-21
> **cmygeHm said:**
> I killed this process and space on hard disk released =)
Thank you very much =)
Of course I removed task for mplayer from crontab.
Great. I'm glad you've managed to solve it. Could you please mark the thread as solved?

Also, make sure to remove all the logging you added to crontab, or that will fill your disk eventually!

---

### Post by cmygeHm on 2012-08-21
I marked it.
Thank you =) Ok, I have only one task in crontab, which creates so big logs.

---

