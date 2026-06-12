---
title: "Root partion filling up, help. And delete old kernels?"
date: 2009-01-20
forum: General Help
---

### Post by rug2 on 2009-01-20
Hello, 

This question has been posted here:
[http://www.linuxquestions.org/questions/ubuntu-63/so-many-kernels-and-running-out-of-space-in-698596/](http://www.linuxquestions.org/questions/ubuntu-63/so-many-kernels-and-running-out-of-space-in-698596/)

Basically my problem is my root partition is filling up and I have no idea what's doing it. I even deleted unwanted things, but root keeps filling up (I'm not installing anything... all downloads and such go in other partitions, root takes care of /usr, /lib and some other stuff). 

This is the output of df -A 
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda7              8815372   8340364     27200 100% /
proc                         0         0         0   -  /proc
/sys                         0         0         0   -  /sys
varrun                 1037076       252   1036824   1% /var/run
varlock                1037076         0   1037076   0% /var/lock
udev                   1037076        68   1037008   1% /dev
devshm                 1037076       136   1036940   1% /dev/shm
devpts                       0         0         0   -  /dev/pts
/dev/sda6             12096724   4864916   6617324  43% /home
/dev/sda1              1535996    192060   1343936  13% /media/win
/dev/sda2             58367996  57932168    435828 100% /media/winc
/dev/sda3             31714296  30388992   1325304  96% /media/wine
securityfs                   0         0         0   -  /sys/kernel/security
binfmt_misc                  0         0         0   -  /proc/sys/fs/binfmt_misc
/dev/mmcblk0p1          495168    206720    288448  42% /media/disk

```

Could it be some log files? 

Also I have about 12 different kernel versions, I'd like to delete at least 9 of those to free up space. How to do that? Just apt them out? 

Help to get my space back is well appreciated. 


Thanks

---

### Post by cmnorton on 2009-01-20
Your old kernels are probably not taking up that much space.

Basically, you will need to do two things, and you will get other useful suggestions as well:

1) Run du -h -r | sort -r | less

to locate directories with the highest sized files. du -a includes the files as well as the directories.

2) Search these forums -- I have never done this -- for a re-partitioning tool. I saw what I thought was one of your partitions at 100%.

3) Whoops, there were three things ...
Look in your logs to see what's running and
look at the output of ps -ef (also to see what's running).

---

### Post by HermanAB on 2009-01-20
The problem is likely in /var/log.  The logrotate script in /etc should be removing old log files.  Check the configuration thereof, or simply delete everything in /var/log, then restart the syslog daemon.

Cheers,

Herman

---

### Post by Yellow Pasque on 2009-01-20
You can remove the old kernels with apt. Search for linux-image and linux-headers in Synaptic. It's a good idea to keep one old kernel that's known to work.

---

### Post by rug2 on 2009-01-20
Here's another funny thing, the above listing in a better format says
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             8.5G  8.0G   27M 100% /

```

Where's the .5 gigs gone? 

Found the culprit using du. It was my hellanzb log file, 998MB. :o Did not know about du, cheers for that.


:)

---

