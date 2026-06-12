---
title: "Swap suddently increasing after updates?"
date: 2009-02-19
forum: General Help
---

### Post by Belerophon on 2009-02-19
Did anyone noticed this? 

My last updates were for wine (I'm using updates from the wine HQ) and security updates for ati driver. I think it was after that that I noticed my swap being used, which is VERY uncommon as I have 2GiB of RAM and have swappiness set to 20. My swap partition is 1GiB.

I'm writing this with 27% of ram used, and 66% of swap.

Did someone noticed this?

Thanks.

---

### Post by Yellow Pasque on 2009-02-19
It almost sounds like a memory leak. I would try running the system for a while without using WINE and seeing if your swap is being used. Keep checking with:
```
free -m
```
Then use WINE for a while and check free -m

---

### Post by jerome1232 on 2009-02-19
> **Belerophon said:**
> Did anyone noticed this? 

My last updates were for wine (I'm using updates from the wine HQ) and security updates for ati driver. I think it was after that that I noticed my swap being used, which is VERY uncommon as I have 2GiB of RAM and have swappiness set to 20. My swap partition is 1GiB.

I'm writing this with 27% of ram used, and 66% of swap.

Did someone noticed this?

Thanks.

nope not really, but this desktop has only been up for 18 hours, restarted it recently. You could have some app that has a memory leak too.

```
free -m
             total       used       free     shared    buffers     cached
Mem:          1000        929         70          0         13        210
-/+ buffers/cache:        705        294
Swap:         2047         56       1991

```

Did you have a program like gimp that likes to use alot of swap? Is your system performance degraded? If performance isn't degraded it's really not something to worry about, swap will get used. I've noticed alot of times if swap does get used on my system it doesn't get deleted out once it's no longer needed.

---

### Post by Belerophon on 2009-02-19
Does wine runs in any form (daemon or something...) without us directly calling some wine app?

---

### Post by jerome1232 on 2009-02-19
No it doesn't run without explicitly calling it.

---

### Post by Belerophon on 2009-02-19
> Did you have a program like gimp that likes to use alot of swap? Is your system performance degraded? If performance isn't degraded it's really not something to worry about, swap will get used. I've noticed alot of times if swap does get used on my system it doesn't get deleted out once it's no longer needed.

I haven't been using anything "heavy". And my system performance does not seem degraded. Maybe it's nothing to worry.
But I really found this strange, 'cause I have this system set up for one year, and I never (unless I'm running for a while VirtualBox) see swap getting used. 

I'll try to find out if it is wine or not. Besides wine, the only apps that I've been using are firefox and thunderbird.

Thanks.

---

### Post by Yellow Pasque on 2009-02-19
> And my system performance does not seem degraded. Maybe it's nothing to worry.
But I really found this strange, 'cause I have this system set up for one year, and I never (unless I'm running for a while VirtualBox) see swap getting used.
As jerome noted, if you keep your system up for long periods of time, old stuff will eventually get swapped out and leave free RAM. This is desired behavior. [http://kerneltrap.org/node/3000](http://kerneltrap.org/node/3000)

---

### Post by Belerophon on 2009-02-19
> **Temüjin said:**
> As jerome noted, if you keep your system up for long periods of time, old stuff will eventually get swapped out and leave free RAM. This is desired behavior. [http://kerneltrap.org/node/3000](http://kerneltrap.org/node/3000)

Yes, I understand that. Where I was trying to get is that, after a year working on a machine with a given configuration, you start to know the behaviour you should expect. On my machine, which I use for work, on a variety of things, opening apps like VirtualBox with XP, thunderbird, firefox, amsn, Netbeans,...I NEVER (unless when I run VirtualBox for a while) see my swap getting used. In part, because I chose so, setting kernel variable swappiness to 20. That's why I found this so strange, and posted here :D

Either way, I tried to monitor the memory after a restart. I think its thunderbird:
Before thunderbird:
```
             total       used       free     shared    buffers     cached
Mem:          2022       1445        577          0         27       1065
-/+ buffers/cache:        353       1669
Swap:          996          0        996
```

After:
```
             total       used       free     shared    buffers     cached
Mem:          2022       1922        100          0         12        834
-/+ buffers/cache:       1075        947
Swap:          996        527        469

```

I opened one app at a time, giving some time (about 30 min) before opening the next app. It was hard job lol. 
At the time I'm writing this, I have a terminal open, thunderbird, firefox and system monitor.

The values above are not very significative. The swap did not increase from zero to that value. It seems to me that it increases each time thunderbird checks email.

After checking the system monitor, I see that java was using much memory. [COLOR="Red"]I'm guessing it was the thunderbird plugin Spamato that was leaking. It's using 70 MB[/COLOR] (right next to firefox, using 60 lol).

Tomorrow I'll try to check if it really was thunderbird leaking, by not opening it at all, and see if this situation happens again.

But it seems that it has nothing to do with the recent updates.

Thanks

---

### Post by Belerophon on 2009-02-20
I was wrong. It had nothing to do with thunderbird!

I simply don't know what's going on. I had my computer turned for a few hours, 3 or 4 hours, with only a terminal open, and my swap was used. 

Even if I had swapiness set to 100 I think this is not normal behaviour, but it is set to 20:
```
cat /proc/sys/vm/swappiness
20

```

And now it starts to piss me off 'cause from time to time my disk gets stuck...

---

### Post by megahead13 on 2009-03-03
I have exactly the same behaviour here with Kubuntu 8.04 x64 (upgraded successively from 7.04 and then 7.10 without any problems). The problem goes on for many months now. Last year I had the same issue with extremely high usage of swap, but I found out it was a memory leak from Xorg (the bug is here: [https://bugs.launchpad.net/xorg-server/+bug/186354](https://bugs.launchpad.net/xorg-server/+bug/186354), I have also contributed, so you can see the details I posted). Unfortunately, after upgrading from 7.10 to 8.04 the behaviour of the system remained the same: Extreme usage of swap! But this time I don't even have a clue about what's causing it! ps, top or similar point that everything works fine. Something strange though happened some days ago: I 've done two changes to the system. First, I formatted one of the two ntfs partitions I used to have to ext3 (I don't use windoze anymore for the last 4 years or so, and in the rare case of needing them I have Virtualbox). Second, I had a problem running gns3 (a python gui frontend for dynamips, the latter being a Cisco emulator), that was solved by deleting /etc/ld.so.cache. I don't know which of these actions contributed, but my system was 100% fine for 3 days or so. But then again the last days the problem reappeared. I created a new user, but nothing new. I also freed around 4GB of space in my root partition, because it was almost full, but again nothing new (I thought that without free space, the system would have to use swap for tmp data. Because as I read in an article about virtual memory, it's not only processes that make the system use swap, but sometimes file or network activity). Tried with rt and server kernels, but the problem is still here! For various reasons, I didn't do anything to solve the problem all these months, but now it started getting on my nerves!!! :evil: :evil: :evil: Below you can see what's going on now on my system...

```
ps -eo pmem,pcpu,rss,vsize,args | sort -k 1 -r -n

%MEM %CPU  RSS  VSZ     COMMAND
 6.9  2.1 142312 376276 konqueror [kdeinit] --silent
 3.4  3.7 70128 152800 /usr/bin/X -br -nolisten tcp :0 vt7 -auth /var/run/xauth/A:0-ilk0a5
 3.2  0.1 67488 327768 kmail -caption KMail -icon kmail -miniicon kmail
 3.0  4.2 63624 587776 amarokapp -session 10145e5ecdb000123595248800000216600054_1236046133_764848
 1.9  0.0 39956 232676 /usr/bin/python /usr/share/python-support/kde-guidance-powermanager/guidance-power-manager.py
 1.8  0.0 38464 217636 krusader -caption Krusader -icon krusader_blue -miniicon krusader_blue
 1.7  0.3 35164  73852 skype -session 10145e5ecdb000123595282600000108390016_1236046133_618402
 1.4  0.1 29960 248000 kded [kdeinit] --new-startup
 1.4  0.0 30520 280044 kmess -session 10145e5ecdb000123595282600000108390017_1236046133_617926
 1.4  0.0 29248 187772 katapult -session 10145e5ecdb000123596072800000108390034_1236046133_617765
 1.3  0.3 27392 320496 kicker [kdeinit]
 1.3  0.0 28804 216356 python -O /usr/lib/wicd/wicd-client.py
 1.2  2.0 26540 156552 superkaramba -session 10145e5ecdb000123594350100000108310028_1236046133_619081
 1.2  0.0 25468 214052 python /usr/bin/system-config-printer-applet-kde
 1.0  0.0 22132 224648 kdesktop [kdeinit]
 0.9  0.0 19804 161060 /usr/bin/python /usr/share/python-support/kde-guidance-powermanager/gpmhelper.py
 0.8  0.1 17136 149252 kget -session 10145e5ecdb000123595283500000108390018_1236046133_617607
 0.8  0.0 18532 166408 yakuake -session 10145e5ecdb000123570480600000090370030_1236046133_617432
 0.8  0.0 16552 195252 knotify [kdeinit]
 0.7  0.0 15028 139220 kshutdown -session 10145e5ecdb000122540756000000118910073_1236046133_617149
 0.7  0.0 14924 152192 kwin [kdeinit] -session 10145e5ecdb00011987913210000005841
 0.7  0.0 14908 154928 kmix [kdeinit] -session 10145e5ecdb00012047533660000009231
 0.7  0.0 14844 139268 kwalletmanager --kwalletd
 0.7  0.0 14820 165764 kio_uiserver [kdeinit]
 0.6  0.0 13780 138556 oooqs2
 0.6  0.0 13636 138996 kkbswitch -session 10145e5ecdb000120475337400000092310068_1236046133_616987
 0.6  0.0 12576 144152 konqueror [kdeinit] -session 10145e5ecdb000123518307100000
 0.5  0.2 12032  22456 /usr/sbin/preload -s /var/lib/preload/preload.state
 0.5  0.1 12160 179408 /usr/bin/artsd -F 10 -S 4096 -s 60 -m artsmessage -c drkonqi -l 3 -f
 0.5  0.0 12112 138388 kweatherservice
 0.5  0.0 12012 145344 klipper [kdeinit]
 0.4  0.0  9956 142476 ksmserver [kdeinit]
 0.4  0.0  9368 137944 kaccess [kdeinit]
 0.4  0.0  9128 183296 kio_pop3 [kdeinit] pop3s /tmp/ksocket-grinder/klauncherf5O
 0.4  0.0 10276 185976 kio_imap4 [kdeinit] imaps /tmp/ksocket-grinder/klauncherf5
 0.4  0.0 10196 186052 kio_imap4 [kdeinit] imaps /tmp/ksocket-grinder/klauncherf5
 0.3  0.0  7840 121368 python /usr/share/hplip/hpssd.py
 0.3  0.0  7792 170000 kio_http [kdeinit] http /tmp/ksocket-grinder/klauncherf5Ou
 0.3  0.0  7772 169868 kio_http [kdeinit] http /tmp/ksocket-grinder/klauncherf5Ou
 0.3  0.0  7712 135864 klauncher [kdeinit] --new-startup
 0.3  0.0  7616  81348 python -O /usr/lib/wicd/wicd-daemon.py
 0.3  0.0  6812  71268 python /usr/lib/wicd/monitor.py
 0.3  0.0  6740 134128 kio_file [kdeinit] file /tmp/ksocket-grinder/klauncherf5Ou
 0.2  0.0  5712  22112 ruby /usr/share/apps/amarok/scripts/lyrics_lyrc/lyrics_lyrc.rb
 0.2  0.0  5264 129936 kdeinit Running...
 0.2  0.0  4904  36100 /usr/sbin/hald
 0.2  0.0  4684  35212 aspell -a -S -B -d el -Tutf8 --encoding=utf-8
 0.2  0.0  4476 104356 /usr/sbin/console-kit-daemon
 0.1  0.0  4072   7384 /sbin/klogd -P /var/run/klogd/kmsg
 0.1  0.0  4056 134040 dcopserver [kdeinit] --nosid
 0.1  0.0  3712  20804 /bin/bash
 0.1  0.0  3340  17692 ruby /usr/share/apps/amarok/scripts/score_default/score_default.rb
 0.1  0.0  2588  72444 /usr/sbin/cupsd
 0.1  0.0  2560 194488 /usr/lib/ipsec/charon --use-syslog
 0.1  0.0  2500  54900 /usr/lib/ipsec/pluto --nofork --uniqueids --debug-none --nat_traversal
 0.1  0.0  2492  35212 aspell -a -S -B -d el -Tutf8 --encoding=utf-8
 0.1  0.0  2336  30396 /usr/lib/hal/hald-addon-dell-backlight
%MEM %CPU   RSS    VSZ COMMAND
 0.0  0.7   296   1392 /bin/busybox sh /bin/bootchart bottom
 0.0  0.1   236   1392 /bin/busybox sh /bin/bootchart bottom
 0.0  0.1   236   1392 /bin/busybox sh /bin/bootchart bottom
 0.0  0.0   996  16672 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
 0.0  0.0   988  16244 /sbin/mount.ntfs-3g /dev/sda2 /media/sda2 -o rw,locale=en_US.UTF-8
 0.0  0.0   952  21188 /usr/bin/dbus-daemon --fork --print-pid 9 --print-address 11 --session
 0.0  0.0   888   4020 /sbin/init
 0.0  0.0   856   6644 ps -eo pmem,pcpu,rss,vsize,args
 0.0  0.0   800   6272 /usr/sbin/dhcdbd --system
 0.0  0.0   772  10208 /sbin/rpc.statd
 0.0  0.0   764  26056 /usr/bin/kdm -config /var/run/kdm/kdmrc
 0.0  0.0   724   9116 sort -k 1 -r -n
 0.0  0.0   724  12296 /sbin/syslogd -u syslog
 0.0  0.0   704  25768 dbus-launch --autolaunch 9c00e184b02941ca9e6012004686b240 --binary-syntax --close-stderr
 0.0  0.0   640  10200 /usr/sbin/inetd
 0.0  0.0   624  33600 /usr/bin/ssh-agent /usr/bin/gpg-agent --daemon --sh --write-env-file=/home/grinder/.gnupg/gpg-agent-info-tuxlaptop x-session-manager
 0.0  0.0   604   3944 /bin/sh /usr/bin/x-session-manager
 0.0  0.0   596   3864 /sbin/getty 38400 tty5
 0.0  0.0   596   3864 /sbin/getty 38400 tty4
 0.0  0.0   596   3864 /sbin/getty 38400 tty3
 0.0  0.0   592   8132 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 0.0  0.0   592   3864 /sbin/getty 38400 tty6
 0.0  0.0   592   3864 /sbin/getty 38400 tty2
 0.0  0.0   592   3864 /sbin/getty 38400 tty1
 0.0  0.0   540   8084 /sbin/portmap
 0.0  0.0   532  16108 /usr/bin/gpg-agent --daemon --sh --write-env-file=/home/grinder/.gnupg/gpg-agent-info-tuxlaptop x-session-manager
 0.0  0.0   504  29580 avahi-daemon: chroot helper
 0.0  0.0   448   3848 kwrapper ksmserver
 0.0  0.0   420   3940 /usr/lib/ipsec/starter
 0.0  0.0   412   7916 _pluto_adns
 0.0  0.0    36    188 /bin/sleep 0.2
 0.0  0.0    32    188 /bin/sleep 0.2
 0.0  0.0    32    188 /bin/sleep 0.2
 0.0  0.0  1812  53464 -:0
 0.0  0.0  1748  13076 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
 0.0  0.0   164   3712 start_kdeinit --new-startup +kcminit_startup
 0.0  0.0  1472  29700 avahi-daemon: running [tuxlaptop.local]
 0.0  0.0  1388  55588 /usr/sbin/winbindd
 0.0  0.0  1328  13532 /usr/sbin/hcid -x -s
 0.0  0.0  1328  13428 /usr/lib/bluetooth/bluetoothd-service-audio
 0.0  0.0  1292  21512 /usr/bin/dbus-daemon --system
 0.0  0.0  1272  17160 /sbin/udevd --daemon
 0.0  0.0  1244  19940 /usr/lib/hal/hald-addon-cpufreq
 0.0  0.0  1188  17820 hald-runner
 0.0  0.0  1184  55588 /usr/sbin/winbindd
 0.0  0.0  1176  13352 /usr/lib/bluetooth/bluetoothd-service-input
 0.0  0.0  1172  19928 hald-addon-input: Listening on /dev/input/event6 /dev/input/event10 /dev/input/event8 /dev/input/event1 /dev/input/event3 /dev/input/event4 /dev/input/event5
 0.0  0.0  1156  19928 hald-addon-storage: polling /dev/scd0 (every 2 sec)
 0.0  0.0     0      0 [watchdog/1]
 0.0  0.0     0      0 [watchdog/0]
 0.0  0.0     0      0 [scsi_eh_1]
 0.0  0.0     0      0 [scsi_eh_0]
 0.0  0.0     0      0 [pdflush]
 0.0  0.0     0      0 [pdflush]
 0.0  0.0     0      0 [pccardd]
 0.0  0.0     0      0 [migration/1]
 0.0  0.0     0      0 [migration/0]
 0.0  0.0     0      0 [kthreadd]
 0.0  0.0     0      0 [kswapd0]
 0.0  0.0     0      0 [ksuspend_usbd]
 0.0  0.0     0      0 [ksoftirqd/1]
 0.0  0.0     0      0 [ksoftirqd/0]
 0.0  0.0     0      0 [kseriod]
 0.0  0.0     0      0 [krfcommd]
 0.0  0.0     0      0 [kpsmoused]
 0.0  0.0     0      0 [kondemand/1]
 0.0  0.0     0      0 [kondemand/0]
 0.0  0.0     0      0 [knodemgrd_0]
 0.0  0.0     0      0 [kjournald]
 0.0  0.0     0      0 [kjournald]
 0.0  0.0     0      0 [kjournald]
 0.0  0.0     0      0 [kjournald]
 0.0  0.0     0      0 [khubd]
 0.0  0.0     0      0 [khpsbpkt]
 0.0  0.0     0      0 [khelper]
 0.0  0.0     0      0 [kblockd/1]
 0.0  0.0     0      0 [kblockd/0]
 0.0  0.0     0      0 [kacpi_notify]
 0.0  0.0     0      0 [kacpid]
 0.0  0.0     0      0 [iwl3945/1]
 0.0  0.0     0      0 [iwl3945/0]
 0.0  0.0     0      0 [iwl3945]
 0.0  0.0     0      0 [events/1]
 0.0  0.0     0      0 [events/0]
 0.0  0.0     0      0 [btdelconn]
 0.0  0.0     0      0 [btaddconn]
 0.0  0.0     0      0 [ata_aux]
 0.0  0.0     0      0 [ata/1]
 0.0  0.0     0      0 [ata/0]
 0.0  0.0     0      0 [aio/1]
 0.0  0.0     0      0 [aio/0]
```

```
free
             total       used       free     shared    buffers     cached
Mem:       2061396    1999704      61692          0      25884     856672
-/+ buffers/cache:    1117148     944248
Swap:      2096440     569996    1526444
```

```
fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          18      144553+  de  Dell Utility
/dev/sda2   *          19        3934    31455270    7  HPFS/NTFS
/dev/sda3            3935        6010    16675470   83  Linux
/dev/sda4            6011       19457   108013027+   5  Extended
/dev/sda5            6011        6663     5245191   83  Linux
/dev/sda6            6664       16454    78646176   83  Linux
/dev/sda7           16455       19196    22025083+  83  Linux
/dev/sda8           19197       19457     2096451   82  Linux swap / Solaris
```

```
cat /proc/sys/vm/swappiness
10
```

My machine is a Dell Latitude D820 (Intel T5600, 2GB RAM, nVidia Quadro NVS110M with 256MB dedicated RAM) and as I said above I use Kubuntu 8.04 x64 with all the latest updates.

In case the problem is not going to be resolved, I am afraid I will install everything from scratch, but I really want to avoid this, since I am really short of time and also I have done some configuration for LaTeX and I don't really remember which things I have changed... In the worst scenario of reinstalling everything I think this time will go for 32bit? What's your opinion for that?

Thanx in advance and sorry for this huge post...

---

### Post by Belerophon on 2009-03-04
Well, I have solved my problem a few days ago.
Unfortunately, I can't say what was the solution:
- my first attempt was to lower even more the 'swappiness'. I changed it from 20 to 10;
- my second, was to disable some plugins in compiz :S

well, the fact is that I don't know which solved the problem because neither one seemed to work right way, on the moment. But now my ram needs to be totally filled before my swap gets used, unlike before when after a few hours turned on, my system got the swap 100% used. In fact, turning the computer off was a pain in the ***, as it took like a minute or more, because it was cleaning the swap I think.

The initiative to lower the swappiness is obvious! 
I also decided to change compiz plugins because top showed me that Xorg was using like 5% of ram. I know now that this is normal, because in this moment xorg is using the same amount of ram...but at the time I thought that it had something to do with the graphics, from graphics I thought in compiz, from compiz I thought in the numerous plugins that I had turned on...


As you can see, my method is not a good one, and you can see also that I'm not an expert. But still, the fact is that the problem came after updating fglrx and it went away after changing compiz configuration. It must mean something!

I have toshiba A100, with a ATI X1600 graphics card, and 2 GB of ram.

Thanks.

---

### Post by megahead13 on 2009-03-04
For me the problem is going on and on and as I said before, I have no idea what is causing it! I don't have any issues with Xorg and I don't use compiz, so not my case here. Because I am really pissed off with this, I will go for a format and maybe install Sidux, if I manage to resolve the problem with my webcam and Skype (new kernels have moved to v4l2, but Skype still uses v4l1), or else I will stick to Kubuntu 8.04, but 32bit this time, unless someone will give me a hint with my issue...

---

