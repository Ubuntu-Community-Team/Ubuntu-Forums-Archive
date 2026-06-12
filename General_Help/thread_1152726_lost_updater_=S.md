---
title: "lost updater =S"
date: 2009-05-08
forum: General Help
---

### Post by KEE on 2009-05-08
I boot ubuntu Intrepid this morning and the updater is missing in administration and in the notification area on my desk top please help. as this something to do with the flash-plugin not functioning lately? I removed the flash-plugin free in synaptic package manager and rebooted this morn and I m now missing updater =S

---

### Post by _Purple_ on 2009-05-08
Type this in terminal and see if it opens update manager
```
gksudo update-manager
```

If it does not open, what does it say?

---

### Post by KEE on 2009-05-08
> **_Purple_ said:**
> Type this in terminal and see if it opens update manager
```
gksudo update-manager
```

If it does not open, what does it say?

hmm do I have a virus?```
me@me-desktop:~$ gksudo update-manager
GNOME_SUDO_PASS
sudo: 1 incorrect password attempt
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSme@me-desktop:~$ 

``` cause my password doesnt work and this way of telling me is wonky and I never seen it like this before

---

### Post by _Purple_ on 2009-05-08
how about 
```
update-manager
```

---

### Post by KEE on 2009-05-08
> **_Purple_ said:**
> how about 
```
update-manager
```

ah i got it with ```
sudo apt-get install update-manager
```
thanks =D 
do you know if the flash plugin free is working in synaptic now?

---

### Post by _Purple_ on 2009-05-08
Do you mean flashplugin-nonfree? You can install it using
```
sudo apt-get install flashplugin-nonfree

```

---

### Post by KEE on 2009-05-08
> **_Purple_ said:**
> Do you mean flashplugin-nonfree? You can install it using
```
sudo apt-get install flashplugin-nonfree

```

yeah is it broken though? I had to removed or firefox would crash everytime it opened. someone said to remove the flashplugin nonfree and it would work so i did and now i am able to visit site like msn. is it fixed do you know?

---

### Post by _Purple_ on 2009-05-08
I am using it with firefox in intrepid and so far did not face any problem.

---

### Post by KEE on 2009-05-08
> **_Purple_ said:**
> I am using it with firefox in intrepid and so far did not face any problem.

well i just installed it and its not working =S do I need to restart ubuntu? ```
 me@me-desktop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfreebob0 libwildmidi0 libdc1394-22 libsoundtouch1c2 libjack0 libopenspc0
  mysql-common libfftw3-3 libmysqlclient15off freepats libcdaudio1 libmpcdec3
  libofa0 libmms0 libneon27-gnutls libiptcdata0
Use 'apt-get autoremove' to remove them.
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/19.4kB of archives.
After this operation, 168kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 104377 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.0.22.87ubuntu1~intrepid1_i386.deb) ...
Setting up flashplugin-nonfree (10.0.22.87ubuntu1~intrepid1) ...
Downloading...
--2009-05-08 00:55:14--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz
Resolving fpdownload.macromedia.com... 72.246.130.70
Connecting to fpdownload.macromedia.com|72.246.130.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3994294 (3.8M) [application/x-gzip]
Saving to: `./install_flash_player_10_linux.tar.gz'

     0K .......... .......... .......... .......... ..........  1%  170K 23s
    50K .......... .......... .......... .......... ..........  2%  146K 24s
   100K .......... .......... .......... .......... ..........  3%  232K 21s
   150K .......... .......... .......... .......... ..........  5%  285K 19s
   200K .......... .......... .......... .......... ..........  6%  263K 18s
   250K .......... .......... .......... .......... ..........  7%  244K 17s
   300K .......... .......... .......... .......... ..........  8%  322K 16s
   350K .......... .......... .......... .......... .......... 10%  247K 16s
   400K .......... .......... .......... .......... .......... 11%  127K 17s
   450K .......... .......... .......... .......... .......... 12%  175K 17s
   500K .......... .......... .......... .......... .......... 14%  203K 17s
   550K .......... .......... .......... .......... .......... 15%  214K 16s
   600K .......... .......... .......... .......... .......... 16%  270K 16s
   650K .......... .......... .......... .......... .......... 17%  259K 15s
   700K .......... .......... .......... .......... .......... 19%  212K 15s
   750K .......... .......... .......... .......... .......... 20%  236K 15s
   800K .......... .......... .......... .......... .......... 21%  310K 14s
   850K .......... .......... .......... .......... .......... 23%  287K 14s
   900K .......... .......... .......... .......... .......... 24%  277K 13s
   950K .......... .......... .......... .......... .......... 25%  332K 13s
  1000K .......... .......... .......... .......... .......... 26%  260K 13s
  1050K .......... .......... .......... .......... .......... 28%  250K 12s
  1100K .......... .......... .......... .......... .......... 29%  350K 12s
  1150K .......... .......... .......... .......... .......... 30%  338K 12s
  1200K .......... .......... .......... .......... .......... 32%  353K 11s
  1250K .......... .......... .......... .......... .......... 33%  349K 11s
  1300K .......... .......... .......... .......... .......... 34%  362K 10s
  1350K .......... .......... .......... .......... .......... 35%  331K 10s
  1400K .......... .......... .......... .......... .......... 37%  414K 10s
  1450K .......... .......... .......... .......... .......... 38%  457K 9s
  1500K .......... .......... .......... .......... .......... 39%  297K 9s
  1550K .......... .......... .......... .......... .......... 41%  406K 9s
  1600K .......... .......... .......... .......... .......... 42%  414K 9s
  1650K .......... .......... .......... .......... .......... 43%  400K 8s
  1700K .......... .......... .......... .......... .......... 44%  151K 8s
  1750K .......... .......... .......... .......... .......... 46%  238K 8s
  1800K .......... .......... .......... .......... .......... 47%  202K 8s
  1850K .......... .......... .......... .......... .......... 48%  263K 8s
  1900K .......... .......... .......... .......... .......... 49%  279K 8s
  1950K .......... .......... .......... .......... .......... 51%  296K 7s
  2000K .......... .......... .......... .......... .......... 52%  266K 7s
  2050K .......... .......... .......... .......... .......... 53%  301K 7s
  2100K .......... .......... .......... .......... .......... 55%  105K 7s
  2150K .......... .......... .......... .......... .......... 56%  215K 7s
  2200K .......... .......... .......... .......... .......... 57%  211K 7s
  2250K .......... .......... .......... .......... .......... 58%  225K 6s
  2300K .......... .......... .......... .......... .......... 60%  109K 6s
  2350K .......... .......... .......... .......... .......... 61%  161K 6s
  2400K .......... .......... .......... .......... .......... 62%  159K 6s
  2450K .......... .......... .......... .......... .......... 64%  181K 6s
  2500K .......... .......... .......... .......... .......... 65%  112K 6s
  2550K .......... .......... .......... .......... .......... 66%  178K 6s
  2600K .......... .......... .......... .......... .......... 67%  130K 6s
  2650K .......... .......... .......... .......... .......... 69%  138K 5s
  2700K .......... .......... .......... .......... .......... 70%  138K 5s
  2750K .......... .......... .......... .......... .......... 71%  189K 5s
  2800K .......... .......... .......... .......... .......... 73%  217K 5s
  2850K .......... .......... .......... .......... .......... 74%  149K 5s
  2900K .......... .......... .......... .......... .......... 75% 75.0K 5s
  2950K .......... .......... .......... .......... .......... 76% 81.1K 4s
  3000K .......... .......... .......... .......... .......... 78%  106K 4s
  3050K .......... .......... .......... .......... .......... 79%  170K 4s
  3100K .......... .......... .......... .......... .......... 80%  182K 4s
  3150K .......... .......... .......... .......... .......... 82%  217K 3s
  3200K .......... .......... .......... .......... .......... 83%  236K 3s
  3250K .......... .......... .......... .......... .......... 84%  253K 3s
  3300K .......... .......... .......... .......... .......... 85%  259K 3s
  3350K .......... .......... .......... .......... .......... 87%  199K 2s
  3400K .......... .......... .......... .......... .......... 88%  270K 2s
  3450K .......... .......... .......... .......... .......... 89%  323K 2s
  3500K .......... .......... .......... .......... .......... 91%  190K 2s
  3550K .......... .......... .......... .......... .......... 92%  118K 1s
  3600K .......... .......... .......... .......... .......... 93%  159K 1s
  3650K .......... .......... .......... .......... .......... 94%  192K 1s
  3700K .......... .......... .......... .......... .......... 96%  222K 1s
  3750K .......... .......... .......... .......... .......... 97%  209K 0s
  3800K .......... .......... .......... .......... .......... 98%  279K 0s
  3850K .......... .......... .......... .......... .......... 99%  260K 0s
  3900K                                                       100% 1293G=19s

2009-05-08 00:55:33 (203 KB/s) - `./install_flash_player_10_linux.tar.gz' saved [3994294/3994294]

Download done.
Flash Plugin installed.
```

---

### Post by _Purple_ on 2009-05-08
Try to restart and see what happens. If it does not work, post what happens when you try to run firefox.

---

### Post by KEE on 2009-05-08
> **_Purple_ said:**
> Try to restart and see what happens. If it does not work, post what happens when you try to run firefox.Awsome!

Thanks abunch Purple =)

---

### Post by _Purple_ on 2009-05-08
My pleasure. Glad to know it worked for you. :)

---

