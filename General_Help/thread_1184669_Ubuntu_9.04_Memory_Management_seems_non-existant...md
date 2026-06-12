---
title: "Ubuntu 9.04 Memory Management seems non-existant..."
date: 2009-06-11
forum: General Help
---

### Post by omelette on 2009-06-11
Hi.  When Ubuntu boots, System Monitor informs me that between 170-200meg memory has been used - total physical memory is 1gig - which is very reasonable.  Presently, with an up-time of about 12 hours, and nothing running, apart from what Ubuntu itself loads, there is 80% physical memory and 10% swap usage. (1gig also)  'Googling' has informed my that this is in fact normal with Linux - Linux will use 'free' memory for services to increase efficiency, releasing it as required.

Fine in theory, unfortunately with just the Opera browser running now (to compose this!) system-performance is abysmal - disk-caching is constant, often even requiring having to wait for my typing to appear on screen as Linux tries to catch-up!  Just moving the mouse pointer around the screen results in continuous disk-access!!!  Using G-Parted, hoping it would force memory to be released, I turned off swap only to find that every program just crashes without an error message!  Using 'sudo sync' derivatives via the the terminal window seems to succeed in releasing 'cached' memory to a degree but it still informs me that 70% of physical ram is being used and there is no increase in performance!

In short, performance is lightning-fast after booting, but memory is gradually 'bled-away' and not returned, while swap usage steadily increases.  Left running overnight with no programs running, and just after a reboot, reported memory usage went from 350meg to over 650meg...

Something is definitely 'broken' here.  Having been around for awhile, this level of performance reminds me of what Win98 would deteriorate to having been left running for a day or so!  If it helps, this is a Dell M1210 laptop, Pro-Duo, with 1gig memory...

---

### Post by michy99 on 2009-06-11
I have noticed similar usage on my system. I usually have to reboot at least once a day just to free up memory that should already be free anyway. Certain programs are not releasing memory when done like they should.

---

### Post by Therion on 2009-06-11
What version of Ubuntu are you running?

---

### Post by omelette on 2009-06-11
I'm using Jaunty 9.04.  I have been using only Ubuntu for about 9 months now and never noticed this terrible memory-management with Intrepid 8.10...

Comforting (in a way!) to know I am not the only one experiencing this - especially as one of Linux's selling points has always been it's efficient memory-management!  Having to reboot your computer to release memory is something I thought I had seen the last of - from the 'dark-side', everything after Win98 would at least release the memory a program used onece you shut it down.  Not Ubuntu 9.04 it appears...

---

### Post by jimv on 2009-06-11
Open System > Administation > System Monitor and see what process is eating all of your RAM.

And please, in the future, keep the snarkiness to yourself.  Just tell us what the problem is.  For example, "All of my RAM is being used and I don't know why".  We don't need your judgments about how you think Ubuntu is broken or the same as Windows 98.

---

### Post by omelette on 2009-06-11
No 'snarkiness' was intended, just someone with wide & varied experience of every Windows OS from 3.1 onward, and in light of the performance, the comparasion seemed justified...

System Monitor tells me little - with nothing 'extra' running, 'Xorg' consumes the most memory, (about 50meg) everything else occupying 1-10meg, so in no way accounting for all the 'missing' memory.  I presumed that one/some of the  Not-Available (N/A) memory-usage listings for root services were somehow responsible.  But aftere searching, apart from the 'sudo sync' commands, the general consensus seems to suggest there is no other way to release memory...

---

### Post by Hobgoblin on 2009-06-11
Open a terminal, type **free**, press enter, post the output.

---

### Post by omelette on 2009-06-11
With just the terminal running:

$ free
             total       used       free     shared    buffers     cached
Mem:       1025224     772164     253060          0       7020     125824
-/+ buffers/cache:     639320     385904
Swap:      1052216     109860     942356

After issuing "sudo echo 3 | sudo tee /proc/sys/vm/drop_caches":

$ free
             total       used       free     shared    buffers     cached
Mem:       1025224     670064     355160          0        184      23144
-/+ buffers/cache:     646736     378488
Swap:      1052216     109856     942360

---

### Post by omelette on 2009-06-12
Up-time about 24hrs, left running overnight, I found that all programs open had closed/crashed with the following memory conditions:

> $ free
             total       used       free     shared    buffers     cached
Mem:       1025224     892996     132228          0       5400      70828
-/+ buffers/cache:     816768     208456
Swap:      1052216     176672     875544


This is with nothing except the terminal program running, with System Monitor showing the largest program running being 'Xorg', occupying 32meg!

So my question, where has the other 700-800 meg vanished to???

---

### Post by Hobgoblin on 2009-06-12
atop might help gather some stats.

```
sudo apt-get install atop
```

Try
```
atop -Mm 1 1 > somestatsfile
```
and post the contents of "somestatsfile", someone might understand it better than I.

The two figures are frequency and iterations so
```
atop -Mn 60 30 > somestatsfile
```
would perform 30 interations at 60 second intervals.

The output of
```
ps aux
```
may help also.

---

### Post by omelette on 2009-06-13
Hobgoblin, thanks for the input.  However, as I use this laptop as part of my day-job, and having to re-boot every 12hrs or so was no longer an option, I opted to restore from my last back-up - which fixed the problem! :D

The only thing I can suggest as the cause of the problem involves that oft-quoted '*dmrc' error that seems to occur randomly - the one concerning file/folder permissions that produces a warning pop-up box at login.  This happened (again!) recently and this time, the 'googled' solution did not work - the desktop itself wouldn't load!  After much 'messing' with folder permissions from the command-line, I finally 'fixed-it' by applying '777' folder permissions to my user-folder and its contents.  This seemed to fix the problem, but maybe not...

Anyway, all is working fine again. :)

---

### Post by omelette on 2009-06-17
Working fine, or so I thought!

Suffice it to say, I am becoming utterly disillusioned with Ubuntu...

---

### Post by cariboo on 2009-06-17
You are running something that has a memory leak, 

This is the output of free -m and uptime on my server:

```
free -m
             total       used       free     shared    buffers     cached
Mem:           488        474         14          0          3        334
-/+ buffers/cache:        136        352
Swap:          956          0        956
jim@willy:~$ uptime
 22:38:12 up 47 days,  6:02,  1 user,  load average: 0.00, 0.00, 0.00
```

note after running for 43 days the memory usage is 136MB.

Could you open a terminal and run top, and post the output, and please use the [noparse]```

```[/noparse] tags

---

### Post by omelette on 2009-06-18
After being running for 6-7hrs 'normally', but now with every app closed:

```
        total       used       free     shared    buffers     cached
Mem:          1001        661        339          0         10        191
-/+ buffers/cache:        459        541
Swap:         1027        218        808

```

Still usable but slow with lots of disk caching going on - memory-leak for sure, I just don't know to where.  I'm fustrated by the fact that whereas I have read several places that Linux can be seen to use up to 90% of available memory even with very little running, in reality this is just 'cached' and not really in use - however, Ubuntu's System Monitor seems to accurately display was is actually in use, at least judging from program performance.  This 90% 'apparent' usage is also shown explicitly when I boot the Xubuntu desktop. (which I installed yesterday)

Apart from Wine, a few Windoze apps, Opera and Blueman installed, I have essentially a 'default' Jaunty setup, so imo, nothing obscure that might have escaped detection till now.  I'm beginning to suspect it might be 'Metatrader', a Wine app, that may be the problem, which apart from Opera, is the only thing that is running continuously.  Below is 'atop' output over 4hrs at 15min intervals - the 1'st output is immediately after booting with nothing 'extra' running, 2'nd is within 15min with Metatrader running, 3'rd and last 'atop' output was 4hrs later, just prior to a very unusual crash which seemed hardware-related.  I really don't know what I should be looking for...

```


ATOP - omelette-laptop    2009/06/18  15:02:34              197 seconds elapsed
PRC | sys  11.63s | user  12.84s | #proc    136 | #zombie    0 | #exit      0 |
CPU | sys      8% | user     13% | irq       1% | idle    147% | wait     31% |
cpu | sys      5% | user      8% | irq       1% | idle     61% | cpu000 w 25% |
cpu | sys      4% | user      5% | irq       0% | idle     85% | cpu001 w  6% |
CPL | avg1   0.52 | avg5    0.42 | avg15   0.18 | csw   464664 | intr  115537 |
MEM | tot    1.0G | free  505.4M | cache 228.0M | buff   17.4M | slab   21.6M |
SWP | tot    1.0G | free    1.0G |              | vmcom 536.2M | vmlim   1.5G |
DSK |         sda | busy     29% | read    9322 | write    788 | avio    5 ms |
NET | transport   | tcpi       4 | tcpo       4 | udpi      16 | udpo     177 |
NET | network     | ipi      342 | ipo      349 | ipfrw      0 | deliv    340 |
NET | lo     ---- | pcki     324 | pcko     324 | si    1 Kbps | so    1 Kbps |
NET | wlan0  ---- | pcki      11 | pcko      29 | si    0 Kbps | so    0 Kbps |
                *** system and process activity since boot ***
  PID MINFLT MAJFLT      VSTEXT  VSIZE  RSIZE  VGROW  RGROW  MEM CMD     1/1   
 2814    157      0        103K 81512K 70332K 81512K 70332K   7% clamd
 3244  26045    274       1650K 58352K 34448K 58352K 34448K   3% Xorg
 3942   6960     50        478K 40760K 20916K 40760K 20916K   2% gnome-panel
 3943  12178     77       1602K 80916K 19884K 80916K 19884K   2% nautilus
 3964   5382     40       1905K 35808K 19632K 35808K 19632K   2% blueman-applet
 4077   4650      9         40K 48824K 15348K 48824K 15348K   1% mixer_applet2
 3963   4184      1         51K 31564K 14332K 31564K 14332K   1% update-notifie
 3955   4418      3       1905K 27812K 14204K 27812K 14204K   1% python
 4295   4125     10        244K 36932K 14084K 36932K 14084K   1% gnome-terminal
 4073   3912      6        113K 30960K 13832K 30960K 13832K   1% fast-user-swit
 3958   3557      7        286K 31012K 13124K 31012K 13124K   1% nm-applet
 3950   3405     35         91K 60316K 11932K 60316K 11932K   1% evolution-alar
 3970   3510      3        133K 26372K 11900K 26372K 11900K   1% notify-osd
 4164   3170     11        238K 43868K 11532K 43868K 11532K   1% evolution-exch
 4070   3150      2         38K 23972K 11084K 23972K 11084K   1% multiload-appl
 3932   3520     36         29K 39356K 10600K 39356K 10600K   1% gnome-settings
 3995   2846      4         29K 27528K 10404K 27528K 10404K   1% trashapplet
 3940   2787      6        478K 19240K  9956K 19240K  9956K   1% metacity
 3974   2301      7        316K 25288K  9140K 25288K  9140K   1% gnome-power-ma
 4080   2513      2         11K 22544K  9056K 22544K  9056K   1% indicator-appl
 4167   2527     27         17K 71024K  8972K 71024K  8972K   1% evolution-data
 3749   5873     17        189K 26476K  7192K 26476K  7192K   1% gnome-session
 3913   1387      5        119K 19056K  6084K 19056K  6084K   1% seahorse-agent
 3897   1795     16         64K 100.5M  5376K 100.5M  5376K   1% pulseaudio
 3083   2141      0        336K  6788K  4684K  6788K  4684K   0% hald
 3900   1293      2         49K  7740K  4624K  7740K  4624K   0% gconfd-2
 3949   1161      2         31K 18096K  4196K 18096K  4196K   0% xfce4-settings
 3999   1390      1         75K 33556K  3864K 33556K  3864K   0% gvfs-hal-volum
 4297   1445      0        690K  6396K  3656K  6396K  3656K   0% bash
 3945   1524      2         82K 41796K  3488K 41796K  3488K   0% bonobo-activat
 3227    999      2        307K 15600K  3316K 15600K  3316K   0% gdm
 2483    847      0         20K  4504K  3212K  4504K  3212K   0% klogd
 3265   1235      1         66K  7072K  3132K  7072K  3132K   0% nm-system-sett
 4015    923      4         50K  8320K  3088K  8320K  3088K   0% gvfs-gphoto2-v
 3737    750      4        550K 25668K  3084K 25668K  3084K   0% gnome-keyring-
 3245    745      0        409K 16552K  2804K 16552K  2804K   0% NetworkManager
 4001    953      2        119K  5940K  2792K  5940K  2792K   0% gvfsd-trash
 2515   1196      2        120K  2640K  2636K  2640K  2636K   0% atop
 3898    779      0          6K  7844K  2636K  7844K  2636K   0% gconf-helper
 2742   1253      0        119K 17380K  2612K 17380K  2612K   0% console-kit-da
 4156    430      0        134K 16644K  2588K 16644K  2588K   0% gnome-screensa
 4332   1890      2        120K  2580K  2576K  2580K  2576K   0% atop
 3301    593      2        384K  6108K  2420K  6108K  2420K   0% cupsd
 3925    642      0         23K 29584K  2376K 29584K  2376K   0% gvfs-fuse-daem
 4060    689      2        107K  5616K  2232K  5616K  2232K   0% gvfsd-burn
 4121    618      3        124K  5968K  2160K  5968K  2160K   0% obex-data-serv
 3919    705      2        107K  5616K  2120K  5616K  2120K   0% gvfsd
 3113    639      1         13K  5176K  2108K  5176K  2108K   0% hald-addon-del
 3187    564      8        222K  4100K  2072K  4100K  2072K   0% bluetoothd
 3165    643      1         17K  5180K  1908K  5180K  1908K   0% hald-addon-sto
    1   1972     37         96K  3084K  1884K  3084K  1884K   0% init
 3263    799      5        401K  4276K  1876K  4276K  1876K   0% wpa_supplicant
 3126    598      1         13K  5176K  1852K  5176K  1852K   0% hald-addon-rfk
 3142    562      0         10K  5172K  1808K  5172K  1808K   0% hald-addon-gen
 3168    573      0          9K  5032K  1808K  5032K  1808K   0% hald-addon-acp
 3116    548      1         15K  5176K  1792K  5176K  1792K   0% hald-addon-inp
 3166    545      1         26K  5188K  1780K  5188K  1780K   0% hald-addon-cpu
 3221    305      0        307K 15032K  1772K 15032K  1772K   0% gdm
 3973    524      1         52K  3664K  1756K  3664K  1756K   0% xfconfd
 3271    413      0        106K  2944K  1484K  2944K  1484K   0% avahi-daemon
 3059    290      4       4375K 10600K  1436K 10600K  1436K   0% winbindd
 2504    834      0        283K  3128K  1412K  3128K  1412K   0% dbus-daemon
 3892    645      0        283K  3068K  1260K  3068K  1260K   0% dbus-daemon
 3065    188      3       4375K 10600K  1192K 10600K  1192K   0% winbindd
 3329    261      0         18K  4324K  1160K  4324K  1160K   0% system-tools-b
 3084   2488      0         11K  3328K  1132K  3328K  1132K   0% hald-runner
 2419    757      0         18K  2204K  1128K  2204K  1128K   0% acpid
 2934    314      1        111K  3228K  1072K  3228K  1072K   0% freshclam
 3432    295      0         30K  3480K  1036K  3480K  1036K   0% cron
 4197    417      5        403K  2276K   984K  2276K   984K   0% dhclient
 3891    140      0         19K  3144K   704K  3144K   704K   0% dbus-launch
 4296    283      0          8K  2036K   704K  2036K   704K   0% gnome-pty-help
 2460    171      0         27K  2040K   684K  2040K   684K   0% syslogd
  968   7644      0         90K  2356K   608K  2356K   608K   0% udevd
 3888     86      0         75K  4784K   604K  4784K   604K   0% ssh-agent
 2481    227      0         47K  1968K   536K  1968K   536K   0% dd
 2346    209      1         13K  1808K   532K  1808K   532K   0% getty
 2347    210      0         13K  1808K   532K  1808K   532K   0% getty
 2354    214      0         13K  1808K   532K  1808K   532K   0% getty
 2353    212      0         13K  1808K   528K  1808K   528K   0% getty
 3523    207      0         13K  1808K   528K  1808K   528K   0% getty
 2350    210      0         13K  1808K   524K  1808K   524K   0% getty
 3272     88      0        106K  2944K   508K  2944K   508K   0% avahi-daemon
 3404     94      0         13K  2096K   456K  2096K   456K   0% atd
 
ATOP - omelette-laptop    2009/06/18  15:32:34              900 seconds elapsed
PRC | sys   2m15s | user  17m06s | #proc    145 | #zombie    0 | #exit    814 |
CPU | sys     14% | user    114% | irq       2% | idle     61% | wait      9% |
cpu | sys      7% | user     61% | irq       0% | idle     30% | cpu001 w  2% |
cpu | sys      7% | user     53% | irq       2% | idle     31% | cpu000 w  7% |
CPL | avg1   2.42 | avg5    2.39 | avg15   1.84 | csw  9501242 | intr 1695234 |
MEM | tot    1.0G | free   15.0M | cache 545.4M | buff   49.5M | slab   41.0M |
SWP | tot    1.0G | free    1.0G |              | vmcom 749.2M | vmlim   1.5G |
PAG | scan 301120 | stall      0 |              | swin     172 | swout   4915 |
DSK |         sda | busy     19% | read   42890 | write   4595 | avio    3 ms |
NET | transport   | tcpi    3663 | tcpo    3520 | udpi       1 | udpo      40 |
NET | network     | ipi     3664 | ipo     3599 | ipfrw      0 | deliv   3664 |
NET | wlan0  ---- | pcki    3684 | pcko    3582 | si    5 Kbps | so    3 Kbps |

  PID MINFLT MAJFLT      VSTEXT  VSIZE  RSIZE  VGROW  RGROW  MEM CMD     1/1   
10958  21945     28         68K 73900K 71656K 73900K 71656K   7% clamscan
 2814      0      0        103K 81628K 70392K     0K   -84K   7% clamd
 5365  29121      1       1228K 56368K 35940K   628K -4480K   4% clamtk
 3244 1293e3     10       1650K 69992K 21760K -2400K -20.9M   2% Xorg
 4359  13782     19          6K   2.6G 21116K 65540K -5496K   2% terminal.exe
 3943    655     48       1602K 84816K 20756K   136K -3916K   2% nautilus
 3964   2545     12       1905K 47868K 20376K  3492K   444K   2% blueman-applet
 3942    947      9        478K 42084K 17032K  1096K -4468K   2% gnome-panel
 4077      0      1         40K 48824K 11932K     0K -3484K   1% mixer_applet2
 3955      0      0       1905K 27812K 11924K     0K -2284K   1% python
 3940    197      2        478K 26024K 11656K     0K -1312K   1% metacity
 4295      0      0        244K 36932K 11632K     0K -2456K   1% gnome-terminal
 3963      1      0         51K 31564K 11584K     0K -2748K   1% update-notifie
 4073      6      2        113K 30960K 10976K     0K -2872K   1% fast-user-swit
 3970     42      5        133K 26784K 10740K     0K -1648K   1% notify-osd
 3958      1      1        286K 31012K 10680K     0K -2488K   1% nm-applet
 4070      0      0         38K 23972K  8780K     0K -2304K   1% multiload-appl
 3995      0      0         29K 27528K  8548K     0K -1856K   1% trashapplet
 4362      0      1        314K 11264K  8444K     0K   -80K   1% wineserver
 3950     15      6         91K 60316K  7992K     0K -3940K   1% evolution-alar
 3932      0      0         29K 39356K  7948K     0K -2652K   1% gnome-settings
 4164      0      0        238K 43868K  7464K     0K -4068K   1% evolution-exch
 4380      0      0          6K   2.5G  7144K     0K -2260K   1% explorer.exe
 3974      1      3        316K 25288K  7092K     0K -2048K   1% gnome-power-ma
 4080      0      1         11K 22544K  6988K     0K -2184K   1% indicator-appl
 3749     24      3        189K 26476K  6108K     0K -1084K   1% gnome-session
 3913      0      0        119K 19056K  5520K     0K  -564K   1% seahorse-agent
 4167      0      0         17K 71024K  5388K     0K -3584K   1% evolution-data
 4367      0      0          6K   2.5G  5008K     0K -1908K   0% winedevice.exe
 3900     26      1         49K  7744K  4540K    -4K  -100K   0% gconfd-2
 3897    167      2         64K 100.5M  4448K    24K -1304K   0% pulseaudio
 3949      6      0         31K 18504K  4184K     0K  -604K   0% xfce4-settings
 3999      0      0         75K 33556K  3764K     0K  -100K   0% gvfs-hal-volum
10871   1055      3        125K 17328K  3648K 17328K  3648K   0% gvfsd-obexftp
 4121    538      2        124K  6808K  3220K   824K   788K   0% obex-data-serv
 2483      0      0         20K  4504K  3200K     0K   -12K   0% klogd
 4297      0      0        690K  6396K  3084K     0K  -572K   0% bash
 3083    210      2        336K  6788K  3020K     0K -1664K   0% hald
 4015      0      0         50K  8320K  2988K     0K  -100K   0% gvfs-gphoto2-v
 3945      0      0         82K 41796K  2856K     0K  -632K   0% bonobo-activat
 4156     92      4        134K 16644K  2744K     0K   128K   0% gnome-screensa
 2515   2075      0        120K  2732K  2728K     0K     0K   0% atop
 4332    932      0        120K  2716K  2712K     0K     0K   0% atop
 4001      0      0        119K  5940K  2692K     0K  -104K   0% gvfsd-trash
 3737      0      0        550K 25668K  2600K     0K  -484K   0% gnome-keyring-
 3265      0      0         66K  7072K  2580K     0K  -580K   0% nm-system-sett
 2742    259      2        119K 17380K  2544K     0K   -68K   0% console-kit-da
 3245      4      1        409K 16552K  2380K     0K  -436K   0% NetworkManager
 3925      4      2         23K 29584K  2352K     0K   -76K   0% gvfs-fuse-daem
 3898      0      0          6K  7844K  2340K     0K  -296K   0% gconf-helper
 3227      0      1        307K 15600K  2256K     0K -1060K   0% gdm
 4060      0      0        107K  5616K  2156K     0K   -76K   0% gvfsd-burn
 3919    101      1        107K  5748K  2132K   132K    -8K   0% gvfsd
 4365      0      0          6K   2.5G  1876K     0K  -872K   0% services.exe
    1      0      0         96K  3084K  1804K     0K   -56K   0% init
 3165    450      0         17K  5180K  1784K     0K  -124K   0% hald-addon-sto
 3187    224     19        222K  4192K  1776K    92K  -304K   0% bluetoothd
 3126    152      0         13K  5176K  1740K     0K  -120K   0% hald-addon-rfk
 3113      0      0         13K  5176K  1652K     0K  -456K   0% hald-addon-del
 3973      0      0         52K  3664K  1652K     0K  -104K   0% xfconfd
 3116     16      7         15K  5176K  1640K     0K  -152K   0% hald-addon-inp
 3142      0      0         10K  5172K  1596K     0K  -212K   0% hald-addon-gen
 3168      0      0          9K  5032K  1576K     0K  -232K   0% hald-addon-acp
 3166      0      0         26K  5188K  1548K     0K  -232K   0% hald-addon-cpu
 2504     27      0        283K  3128K  1416K     0K   -16K   0% dbus-daemon
 3892      6      0        283K  3196K  1416K     0K    12K   0% dbus-daemon
 3271     15      7        106K  3056K  1320K     0K  -248K   0% avahi-daemon
 3263      7      0        401K  4276K  1276K     0K  -600K   0% wpa_supplicant
 2419      0      0         18K  2204K  1100K     0K   -28K   0% acpid
 3084   4009      1         11K  3328K  1080K     0K   -52K   0% hald-runner
 3301      0      0        384K  6108K  1044K     0K -1384K   0% cupsd
 3221      0      0        307K 15032K   880K     0K  -892K   0% gdm
 3329      0      0         18K  4324K   872K     0K  -288K   0% system-tools-b
 3432     24      1         30K  3480K   868K     0K  -168K   0% cron
 2934      0      0        111K  3228K   772K     0K  -144K   0% freshclam
 4197      0      0        403K  2276K   748K     0K  -236K   0% dhclient
 3059      9      0       4375K 10600K   740K     0K  -696K   0% winbindd
 4296      0      0          8K  2036K   692K     0K   -12K   0% gnome-pty-help
 3891      0      0         19K  3144K   676K     0K   -28K   0% dbus-launch
 2460      0      0         27K  2040K   672K     0K   -12K   0% syslogd
 3065      9      0       4375K 10600K   608K     0K  -584K   0% winbindd
10957    248      0         80K  1900K   608K  1900K   608K   0% sh
  968    524      0         90K  2356K   604K     0K    -4K   0% udevd
 3888      0      0         75K  4784K   560K     0K   -44K   0% ssh-agent
 2346      0      0         13K  1808K   516K     0K   -16K   0% getty
 2347      0      0         13K  1808K   516K     0K   -16K   0% getty
 2354      0      0         13K  1808K   516K     0K   -16K   0% getty
 2353      0      0         13K  1808K   512K     0K   -16K   0% getty
 2350      0      0         13K  1808K   508K     0K   -16K   0% getty
 3523      0      0         13K  1808K   508K     0K   -20K   0% getty
 2481      0      0         47K  1968K   500K     0K   -36K   0% dd
 3404      0      0         13K  2096K   308K     0K  -148K   0% atd
 3272      0      0        106K  2944K   272K     0K  -236K   0% avahi-daemon





ATOP - omelette-laptop    2009/06/18  19:17:34              900 seconds elapsed
PRC | sys   4m15s | user  82m16s | #proc    144 | #zombie    0 | #exit    613 |
CPU | sys     14% | user    107% | irq       1% | idle     70% | wait      8% |
cpu | sys      5% | user     66% | irq       0% | idle     26% | cpu001 w  3% |
cpu | sys      9% | user     41% | irq       1% | idle     43% | cpu000 w  5% |
CPL | avg1   1.53 | avg5    1.90 | avg15   1.95 | csw 17050965 | intr 1585909 |
MEM | tot    1.0G | free  305.9M | cache 310.3M | buff    3.7M | slab  175.7M |
SWP | tot    1.0G | free  842.5M |              | vmcom 817.0M | vmlim   1.5G |
PAG | scan 134147 | stall      0 |              | swin   10912 | swout  18941 |
DSK |         sda | busy     10% | read    9949 | write   6066 | avio    5 ms |
NET | transport   | tcpi    6291 | tcpo    6303 | udpi       0 | udpo       0 |
NET | network     | ipi     6291 | ipo     6309 | ipfrw      0 | deliv   6291 |
NET | wlan0  ---- | pcki    6204 | pcko    6133 | si    8 Kbps | so    4 Kbps |
NET | lo     ---- | pcki     120 | pcko     120 | si    0 Kbps | so    0 Kbps |

  PID MINFLT MAJFLT      VSTEXT  VSIZE  RSIZE  VGROW  RGROW  MEM CMD     1/1   
 3244  33401    329       1650K 83312K 29152K    24K  2888K   3% Xorg
 4359   9615     29          6K   2.5G 20180K     0K -1016K   2% terminal.exe
 2814      0      0        103K 81660K 19068K     0K -1484K   2% clamd
 6483  11932     38          6K   2.5G 18360K   2.5G 18360K   2% terminal.exe
 3943   1870    332       1602K 101.3M 14744K     0K  3628K   1% nautilus
 3942    514    170        478K 42592K 11812K     0K  1808K   1% gnome-panel
 4362    140     67        314K 11520K  8648K     0K   708K   1% wineserver
20501     58     33          6K   2.6G  8336K     0K  -788K   1% metaeditor.exe
 4073    412     67        113K 30960K  8008K     0K  1768K   1% fast-user-swit
 3955     35     19       1905K 27812K  7732K     0K   100K   1% python
 3958     21     17        286K 35620K  7696K     0K  -172K   1% nm-applet
 3940    132     19        478K 26024K  7316K     0K   276K   1% metacity
27959  43222    162        220K 34104K  6884K     0K  1112K   1% gnome-system-m
 3964      0      0       1905K 48384K  6744K     0K  -400K   1% blueman-applet
 4295     33     22        244K 37312K  6648K     0K   -40K   1% gnome-terminal
 4380     11      1          6K   2.5G  5688K     0K    44K   1% explorer.exe
 4077    110     35         40K 48824K  5272K     0K   372K   1% mixer_applet2
 3974     23     17        316K 74956K  4612K     0K   -64K   0% gnome-power-ma
 3950      0      0         91K 60316K  3960K     0K  -128K   0% evolution-alar
 4156     33     13        134K 16644K  3908K     0K  -136K   0% gnome-screensa
 4070     47      7         38K 23972K  3860K     0K   148K   0% multiload-appl
 3897    287     69         64K 100.5M  3796K    24K    36K   0% pulseaudio
 4164      0      0        238K 43868K  3744K     0K    -8K   0% evolution-exch
 3963     18      4         51K 31564K  3720K     0K   -92K   0% update-notifie
 4332    702      0        120K  3604K  3600K     0K     0K   0% atop
 3932     28     28         29K 39356K  3484K     0K    60K   0% gnome-settings
 3970     15      7        133K 27116K  3316K     0K   -16K   0% notify-osd
 4080     44     14         11K 22544K  3308K     0K    84K   0% indicator-appl
 3995     71     40         29K 27528K  3256K     0K   220K   0% trashapplet
 4167      0      0         17K 71024K  2820K     0K   -16K   0% evolution-data
 2515    988      0        120K  2732K  2728K     0K     0K   0% atop
 4367      2      1          6K   2.5G  2668K     0K   -16K   0% winedevice.exe
 3949     69     13         31K 18580K  2488K     0K   180K   0% xfce4-settings
 3749     20      9        189K 26476K  2476K     0K    12K   0% gnome-session
 3900     25      3         49K  7744K  2296K     0K   -36K   0% gconfd-2
 3083    185      6        336K  6788K  2080K     0K     4K   0% hald
 3245      2      3        409K 16676K  1900K     0K   -24K   0% NetworkManager
 2742    362      8        119K 17508K  1848K     0K    16K   0% console-kit-da
 3999      0      0         75K 33556K  1788K     0K    -8K   0% gvfs-hal-volum
 4121      0      0        124K  6808K  1660K     0K   -40K   0% obex-data-serv
 3265      7      2         66K  7072K  1416K     0K     0K   0% nm-system-sett
 4015      0      1         50K  8320K  1376K     0K    -8K   0% gvfs-gphoto2-v
 4001      0      0        119K  5940K  1352K     0K    -8K   0% gvfsd-trash
 2504      4      4        283K  3128K  1244K     0K    -8K   0% dbus-daemon
 4365      0      0          6K   2.5G  1224K     0K   -52K   0% services.exe
 3919      0      0        107K  5748K  1192K     0K    -4K   0% gvfsd
 3227      1      1        307K 15600K  1140K     0K     0K   0% gdm
 3892     30     10        283K  3196K  1128K     0K    20K   0% dbus-daemon
 3165    239      0         17K  5180K  1108K     0K    -8K   0% hald-addon-sto
 3737      0      0        550K 25668K  1084K     0K    -4K   0% gnome-keyring-
 3126    153      0         13K  5304K  1080K     0K   -12K   0% hald-addon-rfk
 3271      5      2        106K  3056K  1020K     0K  -116K   0% avahi-daemon
 3187      0      0        222K  4192K   996K     0K    -4K   0% bluetoothd
 3263      8      2        401K  4276K   920K     0K     0K   0% wpa_supplicant
 3168      0      0          9K  5032K   916K     0K    -8K   0% hald-addon-acp
 3113      0      0         13K  5176K   912K     0K    -8K   0% hald-addon-del
 3142      0      0         10K  5172K   896K     0K    -8K   0% hald-addon-gen
 3084   4010      0         11K  3328K   892K     0K     0K   0% hald-runner
 3116      0      0         15K  5176K   888K     0K   -12K   0% hald-addon-inp
 3166      0      0         26K  5188K   856K     0K    -8K   0% hald-addon-cpu
 3301      0      0        384K  6108K   812K     0K   -24K   0% cupsd
 3432     16      0         30K  3480K   744K     0K     0K   0% cron
 2934      0      0        111K  3228K   732K     0K  -256K   0% freshclam
18301      0      0        403K  2276K   708K     0K   -88K   0% dhclient
 3059      9      4       4375K 10600K   616K     0K     0K   0% winbindd
 2419      0      0         18K  2336K   584K     0K    -4K   0% acpid
 2460      0      1         27K  2040K   572K     0K     0K   0% syslogd
 4296      0      0          8K  2036K   572K     0K    -8K   0% gnome-pty-help
    1     10      8         96K  3084K   560K     0K    68K   0% init
 3065     14      1       4375K 10600K   520K     0K     0K   0% winbindd
 2483      0      0         20K  4504K   460K     0K   -24K   0% klogd
 2481      0      0         47K  1968K   388K     0K   -12K   0% dd
 3404      0      0         13K  2096K   328K     0K    -4K   0% atd
  968      0      0         90K  2356K   268K     0K    -4K   0% udevd
 
```

---

### Post by omelette on 2009-06-21
Continuing my efforts to track down the problem, I decided to reboot, (where 180Meg ram was reported as being in use) open & close apps included in the default Ubuntu installation for about 15min, (max ram used was 400Meg) then finally close everything that I had opened and let the computer sit overnight. (235Meg then reported as being in use)  The result of just letting it sit there for 10hrs has been that almost 250Meg of additional ram has slowly been consumed, along with some swap as well!  I say "slowly" 'cos just in the past 15min I have watched a further 5Meg being 'nibbled' away.  And all this with just the base-Ubuntu OS chugging along, nothing else loaded!  Intolerable...

---

### Post by omelette on 2009-07-04
Quick update - I finally figured out (or others did!) what the problem was, a kernel-bug no less!

[http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1716]("http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1716")

This nearly drove me crazy and it took switching my laptop to Debian linux, kernel 2.6.29 to find a solution - ubuntu's offering still hasn't fixed it (although my Ubuntu-based pc got a kernel upgrade yesterday, so maybe it's fixed now...)  Just a heads-up for anyone with the Intel 3945 chipset and a ad-hoc wireless connection...

---

