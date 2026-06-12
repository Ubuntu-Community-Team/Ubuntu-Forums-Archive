---
title: "Help please booting becomes very slow"
date: 2009-03-11
forum: General Help
---

### Post by Maccabee on 2009-03-11
Hi all,

Im using

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"
```

My hardware profile using lshw is [[COLOR="Red"]here[/COLOR]]("http://themaccabee.googlepages.com/computerhardware.html")
CPU-Intel(R) Core(TM)2 CPU 4300 @ 1.80GHz, 1GB Ram
Mother Board-Intel D945GCCR


My problem is 

Wen I boots up Ubuntu, splash screen loads up nicely..
just when gui is comming..before login screen appears..the screen is normal gnome human colour..the mouse pointer is a circle with loading ie rotating appearance..
It keeps on there for about 10-15 minutes..What should i do? Ive no idea..

1.I pressed Ctrl +C  = No effects
2.Ctrl+alt+f1 f2 etc logged into a terminal: give ```
$ top
``` ,,there is nothing suspicious
3.I ran```
 $ dmesg ,& dmesh | more
``` 
   the last two lines of the output of these commands were 

```
drm initialised i915 1.6.0 20060119 on minor 0
eth0: no ipV6 routers present
```

I use a braod band modem through a network card to connect to Internet

I switched on and off the modem = No use

4.I searched the net n saw many people advising others to use bootchart application to log boot process..
My /var/log/ contains no information about boot process in boot file.

I installed boot chart n rebooted, but in the /var/log/bootchart/ the folder remains empty .No png files appears there as bootchart people says

5.I had less space in hard disk so i tried freeing up some (thought maybe this could be a reason)

$df now gives 

```
/dev/sdb8              9682284   7966296   1228016  87% /
varrun                  512420       120    512300   1% /var/run
varlock                 512420         0    512420   0% /var/lock
udev                    512420        88    512332   1% /dev
devshm                  512420       148    512272   1% /dev/shm
lrm                     512420     39760    472660   8% /lib/modules/2.6.24-19-generic/volatile
/dev/sdb5             20095472  20069664     25808 100% /media/sdb5
/dev/sdb6             20095472  20011216     84256 100% /media/sdb6
/dev/sda5              4561532   3561012   1000520  79% /media/sda5
/dev/sda6              5667856   5036696    631160  89% /media/sda6
gvfs-fuse-daemon       9682284   7966296   1228016  87% /home/stephen/.gvfs

```

$ df -k /tmp/
 
gives

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb8              9682284   7966296   1228016  87% /

```


Now Im totally lost i dunno how to figure out this problem..
 I will be very thankful for some advices..
Regards
Stephen

---

### Post by Peter09 on 2009-03-11
You could try editing the boot menu - press escape immediately you see the Grub prompt and then type e(for edit).

Remove the *quiet* option and change *splash* to *nosplash*.

Type B and the boot process will continue, you should be able to see whats happening.

These changes are temporary and normal boot will resume next time.

---

### Post by Maccabee on 2009-03-27
@Peter09
Its of no use Ubuntu becomes slow after starting gnome not while booting i think coz no problems listed wen nosplash used.Everything normal until gnome begins..But i must wait half an hour after gnome starts to get my login prompt where i can type my username and password.
Somebody please please help...Its almost like i cant use my ubuntu system at all coz i cant wait tat much after a restart..

---

### Post by 3Miro on 2009-03-27
It is one of the processes started by Gnome. You could experiment with all the services that start when logged in Gnome. Turn some of them off and see if you can pinpoint the wrongdoer.

Other than that and/or using the system manager to randomly stop processes right after boot, I don't know if there is a way to find out who is keeping the system busy.

On a related matter, even when the circle is thinking, I can still work on Ubuntu. Is the system notably slower during the first 15-30 minutes, if so then top should be able to pinpoint the problem.

---

