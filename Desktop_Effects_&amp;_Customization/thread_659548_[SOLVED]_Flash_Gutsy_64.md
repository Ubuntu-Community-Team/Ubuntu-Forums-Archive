---
title: "[SOLVED] Flash Gutsy 64"
date: 2008-01-05
forum: Desktop Effects &amp; Customization
---

### Post by MNICY on 2008-01-05
Im running Gutsy 64.

I had flash working before (just went to youtube, and installed the plugin when asked to) but then i reinstalled Ubuntu and it does not work anymore.

Tried going to youtube, did not work.

Removed with
```
sudo apt-get autoremove flashplugin-nonfree
```
tried to install with
```
sudo apt-get install flashplugin-nonfree
```
but get this feedback in terminal:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  nspluginwrapper
The following packages will be REMOVED:
  flashplugin-nonfree nspluginwrapper
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking, 537kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 98224 files and directories currently installed.)
Removing flashplugin-nonfree ...
Removing nspluginwrapper ...
casey@ubuntu:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  nspluginwrapper
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree nspluginwrapper
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/129kB of archives.
After unpacking, 537kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package nspluginwrapper.
(Reading database ... 98189 files and directories currently installed.)
Unpacking nspluginwrapper (from .../nspluginwrapper_0.9.91.5-1ubuntu1_amd64.deb) ...
Selecting previously deselected package flashplugin-nonfree.
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_amd64.deb) ...
Setting up nspluginwrapper (0.9.91.5-1ubuntu1) ...
Setting up flashplugin-nonfree (9.0.48.0.2+really0ubuntu12) ...
Downloading...
--18:05:22--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.246.110.70
Connecting to fpdownload.macromedia.com|72.246.110.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,036,127 (2.9M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%  253.07 KB/s
   50K .......... .......... .......... .......... ..........  3%  372.49 KB/s
  100K .......... .......... .......... .......... ..........  5%  450.77 KB/s
  150K .......... .......... .......... .......... ..........  6%  584.46 KB/s
  200K .......... .......... .......... .......... ..........  8%  551.20 KB/s
  250K .......... .......... .......... .......... .......... 10%  554.15 KB/s
  300K .......... .......... .......... .......... .......... 11%  541.79 KB/s
  350K .......... .......... .......... .......... .......... 13%  648.38 KB/s
  400K .......... .......... .......... .......... .......... 15%  588.66 KB/s
  450K .......... .......... .......... .......... .......... 16%  572.58 KB/s
  500K .......... .......... .......... .......... .......... 18%  578.96 KB/s
  550K .......... .......... .......... .......... .......... 20%  588.42 KB/s
  600K .......... .......... .......... .......... .......... 21%  595.55 KB/s
  650K .......... .......... .......... .......... .......... 23%  597.67 KB/s
  700K .......... .......... .......... .......... .......... 25%  585.29 KB/s
  750K .......... .......... .......... .......... .......... 26%  596.00 KB/s
  800K .......... .......... .......... .......... .......... 28%  598.51 KB/s
  850K .......... .......... .......... .......... .......... 30%  596.13 KB/s
  900K .......... .......... .......... .......... .......... 32%  584.31 KB/s
  950K .......... .......... .......... .......... .......... 33%  591.49 KB/s
 1000K .......... .......... .......... .......... .......... 35%  598.98 KB/s
 1050K .......... .......... .......... .......... .......... 37%  592.72 KB/s
 1100K .......... .......... .......... .......... .......... 38%  600.51 KB/s
 1150K .......... .......... .......... .......... .......... 40%  578.90 KB/s
 1200K .......... .......... .......... .......... .......... 42%  601.02 KB/s
 1250K .......... .......... .......... .......... .......... 43%  591.53 KB/s
 1300K .......... .......... .......... .......... .......... 45%  597.61 KB/s
 1350K .......... .......... .......... .......... .......... 47%  601.10 KB/s
 1400K .......... .......... .......... .......... .......... 48%  560.02 KB/s
 1450K .......... .......... .......... .......... .......... 50%  613.62 KB/s
 1500K .......... .......... .......... .......... .......... 52%  579.56 KB/s
 1550K .......... .......... .......... .......... .......... 53%  613.03 KB/s
 1600K .......... .......... .......... .......... .......... 55%  582.78 KB/s
 1650K .......... .......... .......... .......... .......... 57%  596.28 KB/s
 1700K .......... .......... .......... .......... .......... 59%  595.93 KB/s
 1750K .......... .......... .......... .......... .......... 60%  598.31 KB/s
 1800K .......... .......... .......... .......... .......... 62%  584.26 KB/s
 1850K .......... .......... .......... .......... .......... 64%  532.71 KB/s
 1900K .......... .......... .......... .......... .......... 65%  606.13 KB/s
 1950K .......... .......... .......... .......... .......... 67%  578.13 KB/s
 2000K .......... .......... .......... .......... .......... 69%  573.77 KB/s
 2050K .......... .......... .......... .......... .......... 70%  584.93 KB/s
 2100K .......... .......... .......... .......... .......... 72%  565.14 KB/s
 2150K .......... .......... .......... .......... .......... 74%  584.77 KB/s
 2200K .......... .......... .......... .......... .......... 75%  600.33 KB/s
 2250K .......... .......... .......... .......... .......... 77%  594.53 KB/s
 2300K .......... .......... .......... .......... .......... 79%  589.36 KB/s
 2350K .......... .......... .......... .......... .......... 80%  584.21 KB/s
 2400K .......... .......... .......... .......... .......... 82%  592.20 KB/s
 2450K .......... .......... .......... .......... .......... 84%  596.27 KB/s
 2500K .......... .......... .......... .......... .......... 86%  590.14 KB/s
 2550K .......... .......... .......... .......... .......... 87%  586.58 KB/s
 2600K .......... .......... .......... .......... .......... 89%  569.88 KB/s
 2650K .......... .......... .......... .......... .......... 91%  585.92 KB/s
 2700K .......... .......... .......... .......... .......... 92%  578.39 KB/s
 2750K .......... .......... .......... .......... .......... 94%  596.63 KB/s
 2800K .......... .......... .......... .......... .......... 96%  582.29 KB/s
 2850K .......... .......... .......... .......... .......... 97%  567.87 KB/s
 2900K .......... .......... .......... .......... .......... 99%  571.87 KB/s
 2950K .......... ....                                       100%  625.01 KB/s

18:05:27 (565.39 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.
```

Anyone have any idea whats wrong?

---

### Post by Sef on 2008-01-05
Have you checked this [thread]("http://ubuntuforums.org/showthread.php?t=476924")?

---

### Post by MNICY on 2008-01-05
Thanks :)
It worked great


weird though. I had to do a script back when i wanted to get flash to work on 64 bit Feisty..
But i though i did not need to for Gutsy? I mean, last time, on this same computer, same install CD, it let me just easily install flash... 
weird.

---

