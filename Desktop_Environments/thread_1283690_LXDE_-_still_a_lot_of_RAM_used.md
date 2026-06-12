---
title: "LXDE - still a lot of RAM used"
date: 2009-10-05
forum: Desktop Environments
---

### Post by asianette on 2009-10-05
I run LXDE, and I'm still finding that a lot of memory is being used. I don't have anything 'gnome' running and wicd tray is on. Anything I can do to take it down some? I'm running about ~300MB most of the time on a ASUS eee 1005HA-V, Jaunty

---

### Post by asianette on 2009-10-05
ps aux output:

root        19  0.0  0.0      0     0 ?        S<   16:56   0:00 [kacpi_notify]
root        20  0.0  0.0      0     0 ?        S<   16:56   0:00 [ata/0]
root        21  0.0  0.0      0     0 ?        S<   16:56   0:00 [ata/1]
root        22  0.0  0.0      0     0 ?        S<   16:56   0:00 [ata_aux]
root        23  0.0  0.0      0     0 ?        S<   16:56   0:00 [ksuspend_usbd]
root        24  0.0  0.0      0     0 ?        S<   16:56   0:00 [khubd]
root        25  0.0  0.0      0     0 ?        S<   16:56   0:00 [kseriod]
root        26  0.0  0.0      0     0 ?        S<   16:56   0:00 [kmmcd]
root        27  0.0  0.0      0     0 ?        S<   16:56   0:00 [bluetooth]
root        28  0.0  0.0      0     0 ?        S    16:56   0:00 [khungtaskd]
root        29  0.0  0.0      0     0 ?        S    16:56   0:00 [pdflush]
root        30  0.0  0.0      0     0 ?        S    16:56   0:00 [pdflush]
root        31  0.0  0.0      0     0 ?        S<   16:56   0:00 [kswapd0]
root        32  0.0  0.0      0     0 ?        S<   16:56   0:00 [aio/0]
root        33  0.0  0.0      0     0 ?        S<   16:56   0:00 [aio/1]
root        34  0.0  0.0      0     0 ?        S<   16:56   0:00 [ecryptfs-kthr]
root        35  0.0  0.0      0     0 ?        S<   16:56   0:00 [crypto/0]
root        36  0.0  0.0      0     0 ?        S<   16:56   0:00 [crypto/1]
root        46  0.0  0.0      0     0 ?        S<   16:56   0:00 [scsi_eh_0]
root        47  0.0  0.0      0     0 ?        S<   16:56   0:00 [scsi_eh_1]
root        48  0.0  0.0      0     0 ?        S<   16:56   0:00 [scsi_eh_2]
root        49  0.0  0.0      0     0 ?        S<   16:56   0:00 [scsi_eh_3]
root        53  0.0  0.0      0     0 ?        S<   16:56   0:00 [scsi_eh_4]
root        54  0.0  0.0      0     0 ?        S<   16:56   0:00 [scsi_eh_5]
root        57  0.0  0.0      0     0 ?        S<   16:56   0:00 [kstriped]
root        58  0.0  0.0      0     0 ?        S<   16:56   0:00 [kmpathd/0]
root        59  0.0  0.0      0     0 ?        S<   16:56   0:00 [kmpathd/1]
root        60  0.0  0.0      0     0 ?        S<   16:56   0:00 [kmpath_handle]
root        61  0.0  0.0      0     0 ?        S<   16:56   0:00 [ksnapd]
root        62  0.0  0.0      0     0 ?        S<   16:56   0:00 [kondemand/0]
root        63  0.0  0.0      0     0 ?        S<   16:56   0:00 [kondemand/1]
root        64  0.0  0.0      0     0 ?        S<   16:56   0:00 [kconservative]
root        65  0.0  0.0      0     0 ?        S<   16:56   0:00 [kconservative]
root        66  0.0  0.0      0     0 ?        S<   16:56   0:00 [krfcommd]
root       732  0.0  0.0      0     0 ?        S<   16:56   0:01 [kjournald]
root       867  0.0  0.0   2356   672 ?        S<s  16:56   0:00 /sbin/udevd --d
root      1261  0.0  0.0      0     0 ?        S<   16:56   0:00 [kpsmoused]
root      1420  0.0  0.0      0     0 ?        S<   16:56   0:01 [phy0]
root      1653  0.0  0.0      0     0 ?        S<   16:56   0:00 [hd-audio0]
root      1913  0.0  0.0      0     0 ?        S<   16:56   0:00 [kjournald]
root      2237  0.0  0.0   1808   528 tty4     Ss+  16:56   0:00 /sbin/getty 384
root      2238  0.0  0.0   1808   528 tty5     Ss+  16:56   0:00 /sbin/getty 384
root      2241  0.0  0.0   1808   532 tty2     Ss+  16:56   0:00 /sbin/getty 384
root      2242  0.0  0.0   1808   528 tty3     Ss+  16:56   0:00 /sbin/getty 384
root      2243  0.0  0.0   1808   528 tty6     Ss+  16:56   0:00 /sbin/getty 384
root      2291  0.0  0.1   2732  1644 ?        Ss   16:56   0:00 /usr/sbin/acpid
syslog    2332  0.0  0.0   2040   684 ?        Ss   16:56   0:00 /sbin/syslogd -
root      2353  0.0  0.0   1968   540 ?        S    16:56   0:00 /bin/dd bs 1 if
klog      2355  0.0  0.2   3916  2748 ?        Ss   16:56   0:00 /sbin/klogd -P
108       2376  0.4  0.1   2936  1316 ?        Ss   16:56   0:15 /bin/dbus-daemo
root      2398  0.0  0.0   2896   812 ?        S    16:56   0:00 /usr/sbin/lxnm
root      2411  0.5  0.6  20108  6304 ?        S    16:56   0:21 python /usr/sha
root      2437  0.0  0.2  17572  2656 ?        Ssl  16:56   0:00 /usr/sbin/conso
root      2621  0.0  0.1   3556  1544 ?        Ss   16:56   0:00 /usr/sbin/bluet
root      2656  0.0  0.3  15184  3560 ?        Ss   16:56   0:00 /usr/sbin/gdm
avahi     2700  0.0  0.1   2944  1480 ?        Ss   16:56   0:00 avahi-daemon: r
avahi     2701  0.0  0.0   2944   508 ?        Ss   16:56   0:00 avahi-daemon: c
root      2730  0.0  0.2   6108  2424 ?        Ss   16:56   0:00 /usr/sbin/cupsd
root      2772  0.0  0.1   4324  1156 ?        Ss   16:56   0:00 /usr/bin/system
root      2777  0.0  0.0   4280   964 ?        Ss   16:56   0:00 wpa_supplicant
daemon    2851  0.0  0.0   2096   452 ?        Ss   16:56   0:00 /usr/sbin/atd
root      2856  0.2  0.6  10964  6480 ?        S    16:56   0:09 python /usr/sha
root      2881  0.0  0.1   3480  1040 ?        Ss   16:56   0:00 /usr/sbin/cron
root      2980  0.0  0.1   3028  1616 tty1     Ss   16:56   0:00 /bin/login -- 
root      3150  0.0  0.0   2276   412 ?        Ss   16:56   0:00 /sbin/dhclient
machase   6329  0.0  0.2   5364  2896 tty1     S    17:30   0:00 -bash
root      7167  4.1  5.9 108472 60732 tty1     Sl+  17:33   0:53 aptitude
111       9262  0.1  0.4   6504  4436 ?        Ss   17:46   0:00 /usr/sbin/hald
root      9263  0.0  0.1   3328  1140 ?        S    17:46   0:00 hald-runner
root      9294  0.0  0.1   5176  1796 ?        S    17:46   0:00 hald-addon-inpu
root      9295  0.0  0.1   5176  1776 ?        S    17:46   0:00 /usr/lib/hal/ha
root      9315  0.0  0.1   5176  1776 ?        S    17:46   0:00 /usr/lib/hal/ha
root      9324  0.0  0.1   5172  1752 ?        S    17:46   0:00 /usr/lib/hal/ha
root      9360  0.0  0.1   5188  1780 ?        S    17:46   0:00 /usr/lib/hal/ha
111       9361  0.0  0.1   5032  1760 ?        S    17:46   0:00 hald-addon-acpi
root      9469  0.0  0.3  15616  3396 ?        S    17:46   0:00 /usr/sbin/gdm
machase   9637  0.0  0.1   3060  1272 ?        S    17:46   0:00 /usr/lib/gamin/
machase   9658  0.1  0.4  93176  4672 ?        Ssl  17:46   0:00 /usr/bin/pulsea
root      9819 11.4  1.5  27684 16112 tty7     Rs+  17:47   0:49 /usr/X11R6/bin/
machase   9870  0.0  0.1   9152  1992 ?        S    17:48   0:00 /usr/bin/gnome-
machase   9882  0.0  0.0   2756   924 ?        Ss   17:48   0:00 /usr/bin/lxsess
machase   9990  0.0  0.0   4784   604 ?        Ss   17:48   0:00 /usr/bin/ssh-ag
machase   9995  0.0  0.0   3144   688 ?        S    17:48   0:00 /usr/bin/dbus-l
machase   9996  0.0  0.0   2672   792 ?        Ss   17:48   0:00 //bin/dbus-daem
machase   9997  0.3  0.7  13388  7308 ?        S    17:48   0:01 openbox --confi
machase   9998  0.0  0.1   5112  1316 ?        S    17:48   0:00 lxde-settings
machase   9999  0.1  0.2   4576  2228 ?        S    17:48   0:00 xscreensaver -n
machase  10007  1.3  1.3  99648 14004 ?        Sl   17:48   0:05 lxpanel --profi
machase  10008  0.4  1.2  35404 13112 ?        S    17:48   0:01 pcmanfm -d
machase  10013  0.2  1.5  30060 15888 ?        S    17:48   0:01 python /usr/sha
machase  10019  0.0  0.1   5620  2036 ?        S    17:48   0:00 /usr/lib/gvfs/g
root     10040  0.0  0.0   3144   688 ?        S    17:48   0:00 dbus-launch --a
root     10041  0.0  0.0   2672   816 ?        Ss   17:48   0:00 //bin/dbus-daem
machase  10586 18.0  4.4 156380 45264 ?        Sl   17:53   0:19 /usr/lib/firefo
machase  10593  0.1  0.2   6176  3044 ?        S    17:53   0:00 /usr/lib/libgco
machase  10674  9.6  1.0  20940 10528 ?        R    17:55   0:00 /usr/bin/x-term
machase  10675  0.0  0.0   2036   696 ?        S    17:55   0:00 gnome-pty-helpe
machase  10676 13.0  0.2   5300  2832 pts/0    Ss   17:55   0:00 [bash]
root     10694  0.0  0.1   2768  1028 pts/0    R+   17:55   0:00 ps aux

---

### Post by kerry_s on 2009-10-05
unused ram is waisted ram, 300mb is pretty common for a modern system, the more ram you have the more a linux system will cache to improve performance. if you tweak it to use less ram, the system can actually feel slower, because it would have to load everything fresh each time you use it, caching it in ram is faster, just let the computer do it's thing, don't worry about it unless there is a problem, just do what ever it is you do. :lolflag:

---

### Post by theZoid on 2009-10-05
I'm using 431mb of ram right now on a full jaunty 9.04 x64 gnome install, with conky running.  I have 4 gb total ram.  I don't know, I think that sounds about right if I remember from running LXDE or Openbox.  What's your total ram in the eeepc, 1 or 2 gbs?

---

### Post by asianette on 2009-10-05
I have 1GB. I thought LXDE was supposed to be light on resources? I decided against installing conky or screenlets for that purpose. It just seems like an awful lot.

---

### Post by theZoid on 2009-10-05
> **asianette said:**
> I have 1GB. I thought LXDE was supposed to be light on resources? I decided against installing conky or screenlets for that purpose. It just seems like an awful lot.

Maybe....I'm just going from memory...I can understand why want to cut it down...I'll check and post back if I find anything useful...:)

---

### Post by kerry_s on 2009-10-05
> **asianette said:**
> I have 1GB. I thought LXDE was supposed to be light on resources? I decided against installing conky or screenlets for that purpose. It just seems like an awful lot.

it is, but what good is having resources if it's not being used. it's not a lxde problem, the kernel is detierming the way to use resouces by what resources are available, in most cases i have found that it will try to use 60% of the available resources.

in the past having more resouces free meant a better running system, that is no longer the case, as programs have gotten bigger & resources have increased it only makes sense to use those resouces to speed up the programs.

i have been working on low resource systems for some time & have learned a lot how to get the most out of them & 1 thing i don't do is mess with how it handles resources, which lets things feel as fast as they should.

so i'm telling you if you want the speed, let it do what it does, it does not matter what desktop or window manager, let the computer do the thinking, you can worry about more important things.

i use a vaio pcg-f430 450mhz 256mb ram running gnome & a ibm-t20 700mhz 128mb ram running jwm, i'm currently on the ibm.

---

### Post by Lukios on 2009-10-05
I have been working with lxde a lot lately and I don't use that much resources. I would suggest installing preload and upgrading your lxde to the current version if your using the ones from the ubuntu repositories.

---

### Post by earthpigg on 2009-10-06
just to make sure we are all clear, ill use my system as an example re: RAM and explain two relevant parts.

```
[chris: ~]$ free -m
             total       used       free     shared    buffers     cached
Mem:          5953       _***2452***_ <-1st 3500          0        146       1676
-/+ buffers/cache:        _***629***_ <-2nd 5323
Swap:            0          0          0
[chris: ~]$ 

```

***_the first bold/underline/italic line_*** is RAM used including cache -- your computer loading things ahead of time (based on guestimates and past usage patterns) to make starting them quicker later on. its good that so much is used -- in fact, so little is used on my system that it has me going "wtf, why isnt ***more*** of my RAM being used???"... ***on this line, unused RAM is wasted RAM.*** If Ubuntu's guess about what 'should' be loaded ahead of time is wrong, its no big deal... it instantly hands this RAM over to what it ***should*** have guessed when you do start that given program.

the ***_second bold/underline/italic line_*** is RAM used ***minus*** cache. this is what we worry about when we talk about bloat. in my case, so much is used because i have 10 ff tabs, a tv show, rhythmbox with a 3000 song playlist, and pidgin running.... on the other hand, when i have multiple VM's running much more of that gets used. when i boot into my LXDE desktop environment before i start opening things and whatnot, it's usually around 65 mb used.

---

### Post by asianette on 2009-10-06
What I am getting from the last two posts is that output of free -m gives the amount being used for EVERYTHING, not just process, is this correct? If that's it, I'll let it alone, it's really because I'm so OCD about these things. I managed to take a lot of unnecessary stuff off startup. It brought it down some.

---

### Post by kerry_s on 2009-10-06
> **asianette said:**
> What I am getting from the last two posts is that output of free -m gives the amount being used for EVERYTHING, not just process, is this correct? If that's it, I'll let it alone, it's really because I'm so OCD about these things. I managed to take a lot of unnecessary stuff off startup. It brought it down some.

trust me, we understand. :lolflag:
by all means if you don't need a program you can remove, & it won't be loaded & save resources. other than that, trust your system to manage all those 1's & 0's.

i bet you would go crazy if yours was like mine, but trust me i have enough resources to do what ever. :)

---

### Post by Rob Campbell on 2009-10-06
This is Linux not Windows! :-)
It's totally normal for a Linux box to cache previously opened applications, etc, so that they can be opened faster the next time. 

I wouldn't even think about it unless your swap space is also filling up for no reason and the disk is thrashing a lot.

---

### Post by asianette on 2009-10-06
> **Rob Campbell said:**
> This is Linux not Windows! :-)
It's totally normal for a Linux box to cache previously opened applications, etc, so that they can be opened faster the next time. 

I wouldn't even think about it unless your swap space is also filling up for no reason and the disk is thrashing a lot.

Swap isn't even being touched :)

Thank you all, I will try not to let it bother me XD

---

