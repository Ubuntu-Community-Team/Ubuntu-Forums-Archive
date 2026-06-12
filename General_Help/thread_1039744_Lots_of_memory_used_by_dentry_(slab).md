---
title: "Lots of memory used by dentry (slab)"
date: 2009-01-14
forum: General Help
---

### Post by Chig00 on 2009-01-14
Hi,

I am running ubuntu 8.10, system is updated (proposed updates enabled)

output of uname -a:
Linux dennis-laptop-IBM 2.6.27-11-generic #1 SMP Thu Jan 8 08:38:38 UTC 2009 x86_64 GNU/Linux

uptime
 01:43:15 up 3 days, 10:39,  4 users,  load average: 0.45, 0.30, 0.21

The problem is that after few days of uptime system uses most of memory even without runing big apps:

output of free -k:
```
             total       used       free     shared    buffers     cached
Mem:       1990460    1754704     235756          0      24392     333388
-/+ buffers/cache:    1396924     593536
Swap:      4803392     583948    4219444
```

And non of applications uses that much memory,
output of ps -eo pid,ppid,rss,vsize,pcpu,pmem,cmd -ww --sort=pid :
```

  PID  PPID   RSS    VSZ %CPU %MEM CMD
    1     0   528   4100  0.0  0.0 /sbin/init
    2     0     0      0  0.0  0.0 [kthreadd]
    3     2     0      0  0.0  0.0 [migration/0]
    4     2     0      0  0.0  0.0 [ksoftirqd/0]
    5     2     0      0  0.0  0.0 [watchdog/0]
    9     2     0      0  0.0  0.0 [events/0]
   11     2     0      0  0.0  0.0 [khelper]
   49     2     0      0  0.0  0.0 [kintegrityd/0]
   52     2     0      0  0.0  0.0 [kblockd/0]
   55     2     0      0  0.0  0.0 [kacpid]
   56     2     0      0  0.0  0.0 [kacpi_notify]
  152     2     0      0  0.0  0.0 [cqueue]
  156     2     0      0  0.0  0.0 [kseriod]
  207     2     0      0  0.0  0.0 [kswapd0]
  253     2     0      0  0.0  0.0 [aio/0]
 1304     2     0      0  0.0  0.0 [ksuspend_usbd]
 1308     2     0      0  0.0  0.0 [khubd]
 1438     2     0      0  0.0  0.0 [ata/0]
 1440     2     0      0  0.0  0.0 [ata_aux]
 1462     2     0      0  0.0  0.0 [khpsbpkt]
 2311     2     0      0  0.0  0.0 [scsi_eh_0]
 2312     2     0      0  0.0  0.0 [scsi_eh_1]
 2345     2     0      0  0.0  0.0 [knodemgrd_0]
 2937     2     0      0  0.0  0.0 [kjournald]
 2976     2     0      0  0.0  0.0 [pdflush]
 3522     1   420  17348  0.0  0.0 /sbin/udevd --daemon
 3887     2     0      0  0.0  0.0 [kmmcd]
 3975     2     0      0  0.0  0.0 [btaddconn]
 3979     2     0      0  0.0  0.0 [btdelconn]
 4532     2     0      0  0.0  0.0 [migration/1]
 4533     2     0      0  0.0  0.0 [ksoftirqd/1]
 4534     2     0      0  0.0  0.0 [watchdog/1]
 4535     2     0      0  0.0  0.0 [rpciod/1]
 4536     2     0      0  0.0  0.0 [kondemand/1]
 4537     2     0      0  0.0  0.0 [iwlagn/1]
 4538     2     0      0  0.0  0.0 [ata/1]
 4539     2     0      0  0.0  0.0 [aio/1]
 4540     2     0      0  0.0  0.0 [kblockd/1]
 4541     2     0      0  0.0  0.0 [kintegrityd/1]
 4542     2     0      0  0.0  0.0 [events/1]
 4762  8208  1008   6480  0.0  0.0 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-wlan0.pid -lf /var/run/dhclient-wlan0.lease -cf /var/run/nm-dhclient-wlan0.conf wlan0
 4782     2     0      0  0.0  0.0 [kpsmoused]
 4884     2     0      0  0.0  0.0 [pccardd]
 4969     2     0      0  0.0  0.0 [ktpacpid]
 5005     2     0      0  0.0  0.0 [iwlagn/0]
 5009     2     0      0  0.0  0.0 [iwlagn]
 5434     1  7908 389928  0.0  0.3 /usr/lib/evolution/2.24/evolution-alarm-notify --oaf-activate-iid=OAFIID:GNOME_Evolution_Calendar_AlarmNotify_Factory:2.24 --oaf-ior-fd=52
 5961     1   440   8172  0.0  0.0 /sbin/portmap
 5988     1   528  10288  0.0  0.0 /sbin/rpc.statd
 6172     1   400   3940  0.0  0.0 /sbin/getty 38400 tty4
 6173     1   400   3940  0.0  0.0 /sbin/getty 38400 tty5
 6176     1   400   3940  0.0  0.0 /sbin/getty 38400 tty2
 6177     1   400   3940  0.0  0.0 /sbin/getty 38400 tty3
 6178     1   400   3940  0.0  0.0 /sbin/getty 38400 tty6
 6437     1  2332   6972  0.0  0.1 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
 6471     2     0      0  0.0  0.0 [kondemand/0]
 6585     1   616  12364  0.0  0.0 /sbin/syslogd -u syslog
 6641     1   384   8204  0.0  0.0 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 6643     1   484   8072  0.0  0.0 /sbin/klogd -P /var/run/klogd/kmsg
 6684     1  1624  22152  0.0  0.0 /bin/dbus-daemon --system
 6709     1  1476  29912  0.0  0.0 avahi-daemon: running [dennis-laptop-IBM.local]
 6710  6709   248  29680  0.0  0.0 avahi-daemon: chroot helper
 7163     1 19776 332468  0.2  0.9 empathy
 7288     1  3420  51116  0.0  0.1 /usr/lib/telepathy/mission-control
 7361     1   576  47968  0.0  0.0 /usr/sbin/exim4 -bd -q30m
 7472     1   316   4332  0.0  0.0 /usr/sbin/hddtemp -d -l 127.0.0.1 -p 7634 -s | /dev/sg0 /dev/sda
 7535     1  2012 109052  0.0  0.1 /usr/sbin/console-kit-daemon
 7539     1  4416 542300  0.0  0.2 /usr/lib/jvm/java-6-sun/bin/java -Xmx256m -Djava.awt.headless=true -Djava.io.tmpdir=/var/cache/jetty -Djava.library.path=/usr/lib -DSTART=/etc/jetty/start.config -Djetty.home=/usr/share/jetty -jar /usr/share/jetty/lib/start.jar /etc/jetty/jetty.xml
 7654     1   248  27324  0.0  0.0 /usr/sbin/chipcardd4 --pidfile /var/run/chipcard/chipcardd4.pid --exit-on-error
 7655  7654  1168  27704  1.0  0.0 /usr/sbin/chipcardd4 --pidfile /var/run/chipcard/chipcardd4.pid --exit-on-error
 7895     1   712  60864  0.0  0.0 /usr/sbin/winbindd
 7924  7895   580  60864  0.0  0.0 /usr/sbin/winbindd
 7928     1  3084  36296  0.0  0.1 /usr/sbin/hald
 7929  7928  1060  17932  0.0  0.0 hald-runner
 7975  7929  1100  20076  0.0  0.0 hald-addon-input: Listening on /dev/input/event2 /dev/input/event6 /dev/input/event3 /dev/input/event4 /dev/input/event1 /dev/input/event10
 7994  7929   848  20060  0.0  0.0 /usr/lib/hal/hald-addon-cpufreq
 7997  7929   852  16752  0.0  0.0 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
 8055  7929   996  20052  0.0  0.0 hald-addon-storage: polling /dev/scd0 (every 2 sec)
 8126     1  1480  30452  0.0  0.0 /usr/sbin/bluetoothd
 8174     2     0      0  0.0  0.0 [krfcommd]
 8208     1  2552  63000  0.0  0.1 /usr/sbin/NetworkManager
 8216     1  1704  21088  0.0  0.0 /sbin/wpa_supplicant -u -f /var/log/wpa_supplicant.log
 8218     1  2476  66796  0.0  0.1 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf
 8307     1   828 118240  0.0  0.0 /usr/sbin/gdm
 8311  8307  1960 137172  0.0  0.0 /usr/sbin/gdm
 8316  8311 167764 278380 10.0  8.4 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
 8387     1   860  35384  0.0  0.0 /usr/bin/system-tools-backends
 8440     1   268  16512  0.0  0.0 /usr/sbin/atd
 8483     1   816  19920  0.0  0.0 /usr/sbin/cron
 8715  8311  5360 150132  0.0  0.2 x-session-manager
 8770  8715   232  35916  0.0  0.0 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
 8773     1   476  25868  0.0  0.0 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
 8775     1  1868  22496  0.0  0.0 //bin/dbus-daemon --fork --print-pid 6 --print-address 9 --session
 8786     1  6236  48168  0.0  0.3 /usr/lib/libgconf2-4/gconfd-2
 8851  8715  4564 144816  0.0  0.2 /usr/bin/seahorse-agent --execute x-session-manager
 8861     1   400   3940  0.0  0.0 /sbin/getty 38400 tty1
 8865     1  3996  50492  0.0  0.2 /usr/lib/gvfs/gvfsd
 8871     1  1796 136428  0.0  0.0 /usr/lib/gvfs//gvfs-fuse-daemon /home/dennis/.gvfs
 8876  8715  3000 115884  0.0  0.1 /usr/lib/gnome-session/helpers/gnome-keyring-daemon-wrapper
 8881     1  2196 144328  0.0  0.1 /usr/bin/gnome-keyring-daemon
 8883     1 11012 306056  0.0  0.5 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
 8884  8715   328   4020  0.0  0.0 /bin/sh /usr/bin/compiz
 8946  8884 38496 360348  4.0  1.9 /usr/bin/compiz.real --ignore-desktop-hints --replace --loose-binding core ccp
 8952     1  5344 198556  0.0  0.2 gnome-screensaver
 8957  8946   312   4020  0.0  0.0 /bin/sh -c gtk-window-decorator --replace
 8958  8957 13432 196728  0.0  0.6 gtk-window-decorator --replace
 8959  8715 40484 510728  0.3  2.0 gnome-panel
 8960  8715 86200 658000  0.1  4.3 nautilus --no-desktop --browser
 8963     1  4316 153496  0.0  0.2 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=17
 8969     1  2708  56088  0.0  0.1 /usr/lib/gvfs/gvfs-hal-volume-monitor
 8971     1  1792  36916  0.0  0.0 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
 8975     1 11356 233792  0.0  0.5 /usr/lib/gnome-applets/gweather-applet-2 --oaf-activate-iid=OAFIID:GNOME_GWeatherApplet_Factory --oaf-ior-fd=20
 8979     1  8416 217588  0.0  0.4 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=26
 8982     1  9472 204076  0.5  0.4 /usr/lib/gnome-applets/multiload-applet-2 --oaf-activate-iid=OAFIID:GNOME_MultiLoadApplet_Factory --oaf-ior-fd=32
 8985     1  1656  44924  0.0  0.0 /usr/lib/gvfs/gvfsd-burn --spawner :1.5 /org/gtk/gvfs/exec_spaw/0
 8991     1  2544 129476  0.0  0.1 /usr/lib/gvfs/gvfsd-trash --spawner :1.5 /org/gtk/gvfs/exec_spaw/2
 9007  8715  6240 209440  0.0  0.3 python /usr/share/system-config-printer/applet.py
 9010  8715  2292  75068  0.0  0.1 trackerd
 9013  8715  4888 126148  0.0  0.2 tracker-applet
 9016  8715 10516 236404  0.0  0.5 update-notifier
 9025  8715  9496 175620  0.0  0.4 bluetooth-applet
 9028  8715 13620 236244  0.0  0.6 nm-applet --sm-disable
 9093     1 11244 314568  0.0  0.5 python /usr/lib/gnome-panel/debian-bts-applet --oaf-activate-iid=OAFIID:GNOME_PyDebianBTSApplet_Factory --oaf-ior-fd=28
 9095     1 13280 321480  0.4  0.6 /usr/lib/link-monitor-applet/link-monitor-applet --oaf-activate-iid=OAFIID:GNOME_LinkMonitorApplet_Factory --oaf-ior-fd=34
 9097     1 17352 458052  0.1  0.8 python /usr/lib/timer-applet/timer-applet --oaf-activate-iid=OAFIID:TimerApplet_Factory --oaf-ior-fd=40
 9099     1 11724 219248  0.0  0.5 /usr/lib/fast-user-switch-applet/fast-user-switch-applet --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=48
 9101     1  9896 227456  0.0  0.4 /usr/lib/gnome-applets/gnome-keyboard-applet --oaf-activate-iid=OAFIID:GNOME_KeyboardApplet_Factory --oaf-ior-fd=54
 9103     1 10764 270360  0.0  0.5 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=66
 9105     1 14012 297812  0.0  0.7 /usr/bin/python /usr/bin/service-discovery-applet --oaf-activate-iid=OAFIID:GNOME_ServiceDiscoveryApplet_Factory --oaf-ior-fd=74
 9107     1 10748 228372  0.1  0.5 /usr/lib/netspeed/netspeed_applet2 --oaf-activate-iid=OAFIID:GNOME_NetspeedApplet_Factory --oaf-ior-fd=62
 9109     1  7484 194456  0.0  0.3 /usr/lib/gnome-panel/gspot --oaf-activate-iid=OAFIID:GNOME_gspotApplet_Factory --oaf-ior-fd=60
 9111     1  7384 190112  0.0  0.3 /usr/lib/gnome-panel/grandr --oaf-activate-iid=OAFIID:GrandrApplet_factory --oaf-ior-fd=82
 9183     1 13684 198484  0.0  0.6 /usr/lib/notification-daemon/notification-daemon
 9189     1  8516 333356  0.0  0.4 /usr/lib/evolution/evolution-data-server-2.24 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2 --oaf-ior-fd=41
 9300     1  3244  86232  0.0  0.1 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
 9520     2     0      0  0.0  0.0 [rpciod/0]
 9530     2     0      0  0.0  0.0 [nfsiod]
 9759     1  7068 376508  0.0  0.3 /usr/lib/evolution/2.24/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution_Exchange_Connector_CalFactory:1.2 --oaf-ior-fd=36
10786     1  3128  91972  0.0  0.1 /usr/lib/gvfs/gvfsd-http --spawner :1.5 /org/gtk/gvfs/exec_spaw/3
11883     1  2972 136692  0.0  0.1 kdeinit4: kdeinit4 Running...
11884 11883  6384 146088  0.0  0.3 klauncher
11886     1  8340 189988  0.0  0.4 kded4
11890 11883  3428 148524  0.0  0.1 kdeinit4: kio_file [kdeinit] file local:/tmp/ksocket-dennis/klauncherT1188
11906     1  8260 147996  0.0  0.4 /usr/bin/knotify4
11915     1  5424 174504  0.0  0.2 /usr/bin/kwalletd
13028     1  6992 429232  0.0  0.3 vlc
13061     1  6732 372372  0.0  0.3 vlc
25074     1 39072 304516  0.1  1.9 gnome-terminal
25077 25074   880  19452  0.0  0.0 gnome-pty-helper
25078 25074  4500  21640  0.0  0.2 bash
25206 25074  4640  21740  0.0  0.2 bash
25519 25074  4632  21740  0.0  0.2 bash
26330     1 31016 373016  0.0  1.5 gedit
26582     1 129148 621736 4.1  6.4 epiphany-browser
26604     1  6424  48452  0.0  0.3 /usr/lib/telepathy/telepathy-gabble
26757     2     0      0  0.0  0.0 [pdflush]
27012  8208  1080   6480  0.0  0.0 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/run/dhclient-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
28623 25078   992   6884  0.0  0.0 ps -eo pid,ppid,rss,vsize,pcpu,pmem,cmd -ww --sort=pid
32655     1   960  72808  0.0  0.0 /usr/sbin/cupsd

```

Apparently memory is consumed by slab:
cat /proc/meminfo
```
MemTotal:      1990460 kB
MemFree:        238124 kB
Buffers:         24296 kB
Cached:         333264 kB
SwapCached:     279908 kB
Active:         735320 kB
Inactive:       192536 kB
SwapTotal:     4803392 kB
SwapFree:      4219444 kB
Dirty:              28 kB
Writeback:           0 kB
AnonPages:      514620 kB
Mapped:          85188 kB
Slab:           718356 kB
SReclaimable:   671496 kB
SUnreclaim:      46860 kB
PageTables:      26980 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
WritebackTmp:        0 kB
CommitLimit:   5798620 kB
Committed_AS:  1773076 kB
VmallocTotal: 34359738367 kB
VmallocUsed:    110776 kB
VmallocChunk: 34359626747 kB
HugePages_Total:     0
HugePages_Free:      0
HugePages_Rsvd:      0
HugePages_Surp:      0
Hugepagesize:     2048 kB
DirectMap4k:   1966784 kB
DirectMap2M:    129024 kB
```

output of cat /proc/slabinfo

```

slabinfo - version: 2.1
# name            <active_objs> <num_objs> <objsize> <objperslab> <pagesperslab> : tunables <limit> <batchcount> <sharedfactor> : slabdata <active_slabs> <num_slabs> <sharedavail>Investigating slab,
fat_inode_cache       12     24    648   12    2 : tunables    0    0    0 : slabdata      2      2      0
fat_cache            102    204     40  102    1 : tunables    0    0    0 : slabdata      2      2      0
nfs_direct_cache       0      0    128   32    1 : tunables    0    0    0 : slabdata      0      0      0
nfs_inode_cache       32     32    992   16    4 : tunables    0    0    0 : slabdata      2      2      0
rpc_inode_cache       19     38    832   19    4 : tunables    0    0    0 : slabdata      2      2      0
TCPv6                 36     36   1792   18    8 : tunables    0    0    0 : slabdata      2      2      0
nv_stack_t            28     28  12288    1    4 : tunables    0    0    0 : slabdata     28     28      0
ext3_inode_cache   10147  16107    768   21    4 : tunables    0    0    0 : slabdata    767    767      0
ext3_xattr             0      0     88   46    1 : tunables    0    0    0 : slabdata      0      0      0
journal_handle       340    340     24  170    1 : tunables    0    0    0 : slabdata      2      2      0
journal_head          84     84     96   42    1 : tunables    0    0    0 : slabdata      2      2      0
revoke_table         258    512     16  256    1 : tunables    0    0    0 : slabdata      2      2      0
revoke_record        256    256     32  128    1 : tunables    0    0    0 : slabdata      2      2      0
kmalloc_dma-512       16     32    512   16    2 : tunables    0    0    0 : slabdata      2      2      0
fuse_request          26     39    608   13    2 : tunables    0    0    0 : slabdata      3      3      0
fuse_inode            24     69    704   23    4 : tunables    0    0    0 : slabdata      3      3      0
cfq_io_context       176    240    168   24    1 : tunables    0    0    0 : slabdata     10     10      0
cfq_queue            182    240    136   30    1 : tunables    0    0    0 : slabdata      8      8      0
mqueue_inode_cache      1     18    896   18    4 : tunables    0    0    0 : slabdata      1      1      0
hugetlbfs_inode_cache      1     14    584   14    2 : tunables    0    0    0 : slabdata      1      1      0
dquot                  0      0    256   16    1 : tunables    0    0    0 : slabdata      0      0      0
shmem_inode_cache   5464   5640    792   20    4 : tunables    0    0    0 : slabdata    282    282      0
nsproxy              146    146     56   73    1 : tunables    0    0    0 : slabdata      2      2      0
UNIX                 982   1196    704   23    4 : tunables    0    0    0 : slabdata     52     52      0
xfrm_dst_cache         0      0    384   21    2 : tunables    0    0    0 : slabdata      0      0      0
ip_dst_cache         140    684    320   12    1 : tunables    0    0    0 : slabdata     57     57      0
TCP                  159    228   1664   19    8 : tunables    0    0    0 : slabdata     12     12      0
blkdev_integrity      36     72    112   36    1 : tunables    0    0    0 : slabdata      2      2      0
blkdev_queue          33     51   1896   17    8 : tunables    0    0    0 : slabdata      3      3      0
blkdev_requests       34     39    304   13    1 : tunables    0    0    0 : slabdata      3      3      0
sock_inode_cache    1041   1308    640   12    2 : tunables    0    0    0 : slabdata    109    109      0
file_lock_cache       46     66    184   22    1 : tunables    0    0    0 : slabdata      3      3      0
Acpi-ParseExt       5469   5936     72   56    1 : tunables    0    0    0 : slabdata    106    106      0
taskstats             36     48    328   12    1 : tunables    0    0    0 : slabdata      4      4      0
page_cgroup       221109 439110     40  102    1 : tunables    0    0    0 : slabdata   4305   4305      0
proc_inode_cache    7934   7943    616   13    2 : tunables    0    0    0 : slabdata    611    611      0
sigqueue              50     50    160   25    1 : tunables    0    0    0 : slabdata      2      2      0
radix_tree_node    13724  15624    560   14    2 : tunables    0    0    0 : slabdata   1117   1117      0
bdev_cache            27     42    768   21    4 : tunables    0    0    0 : slabdata      2      2      0
sysfs_dir_cache    16497  16728     80   51    1 : tunables    0    0    0 : slabdata    328    328      0
inode_cache         1150   1246    568   14    2 : tunables    0    0    0 : slabdata     89     89      0
dentry            3049855 3049899    208   19    1 : tunables    0    0    0 : slabdata 160521 160521      0
buffer_head        14263  14292    112   36    1 : tunables    0    0    0 : slabdata    397    397      0
mm_struct            140    171    832   19    4 : tunables    0    0    0 : slabdata      9      9      0
vm_area_struct     23178  28819    176   23    1 : tunables    0    0    0 : slabdata   1253   1253      0
files_cache          144    189    768   21    4 : tunables    0    0    0 : slabdata      9      9      0
signal_cache         186    221    960   17    4 : tunables    0    0    0 : slabdata     13     13      0
sighand_cache        179    210   2112   15    8 : tunables    0    0    0 : slabdata     14     14      0
task_struct          307    425   5744    5    8 : tunables    0    0    0 : slabdata     85     85      0
anon_vma            6178   8320     32  128    1 : tunables    0    0    0 : slabdata     65     65      0
shared_policy_node    170    170     48   85    1 : tunables    0    0    0 : slabdata      2      2      0
numa_policy          170    340     24  170    1 : tunables    0    0    0 : slabdata      2      2      0
idr_layer_cache      629    686    552   14    2 : tunables    0    0    0 : slabdata     49     49      0
kmalloc-4096         125    152   4096    8    8 : tunables    0    0    0 : slabdata     19     19      0
kmalloc-2048         666    704   2048   16    8 : tunables    0    0    0 : slabdata     44     44      0
kmalloc-1024        1355   1712   1024   16    4 : tunables    0    0    0 : slabdata    107    107      0
kmalloc-512         5304   5616    512   16    2 : tunables    0    0    0 : slabdata    351    351      0
kmalloc-256         1396   1568    256   16    1 : tunables    0    0    0 : slabdata     98     98      0
kmalloc-128         2039   2592    128   32    1 : tunables    0    0    0 : slabdata     81     81      0
kmalloc-64          7210  15040     64   64    1 : tunables    0    0    0 : slabdata    235    235      0
kmalloc-32          8803  12544     32  128    1 : tunables    0    0    0 : slabdata     98     98      0
kmalloc-16          3945   5376     16  256    1 : tunables    0    0    0 : slabdata     21     21      0
kmalloc-8           7372   7680      8  512    1 : tunables    0    0    0 : slabdata     15     15      0
kmalloc-192        10089  14973    192   21    1 : tunables    0    0    0 : slabdata    713    713      0
kmalloc-96          1191   1764     96   42    1 : tunables    0    0    0 : slabdata     42     42      0
kmem_cache_node        0      0     72   56    1 : tunables    0    0    0 : slabdata      0      0      0

```

and output of slabtop -s c
```

 Active / Total Objects (% used)    : 3435891 / 3688439 (93.2%)
 Active / Total Slabs (% used)      : 172191 / 172191 (100.0%)
 Active / Total Caches (% used)     : 61 / 66 (92.4%)
 Active / Total Size (% used)       : 675170.23K / 694203.87K (97.3%)
 Minimum / Average / Maximum Object : 0.01K / 0.19K / 12.00K

  OBJS ACTIVE  USE OBJ SIZE  SLABS OBJ/SLAB CACHE SIZE NAME                   
3049994 3049929  99%    0.20K 160526       19    642104K dentry
439110 224886  51%    0.04K   4305      102     17220K page_cgroup
 16107  10166  63%    0.75K    767       21     12272K ext3_inode_cache
 15624  13771  88%    0.55K   1117       14      8936K radix_tree_node
 28819  23487  81%    0.17K   1253       23      5012K vm_area_struct
  7982   7956  99%    0.60K    614       13      4912K proc_inode_cache
  5640   5462  96%    0.77K    282       20      4512K shmem_inode_cache
 14973  10223  68%    0.19K    713       21      2852K kmalloc-192
  5616   5314  94%    0.50K    351       16      2808K kmalloc-512
   425    311  73%    5.61K     85        5      2720K task_struct
  1712   1350  78%    1.00K    107       16      1712K kmalloc-1024
 14580  14527  99%    0.11K    405       36      1620K buffer_head
   704    666  94%    2.00K     44       16      1408K kmalloc-2048
 16728  16497  98%    0.08K    328       51      1312K sysfs_dir_cache
 15040   7183  47%    0.06K    235       64       940K kmalloc-64
  1308   1057  80%    0.62K    109       12       872K sock_inode_cache
  1196    978  81%    0.69K     52       23       832K UNIX
  1246   1150  92%    0.55K     89       14       712K inode_cache
   152    128  84%    4.00K     19        8       608K kmalloc-4096
   210    179  85%    2.06K     14       15       448K sighand_cache
    28     28 100%   12.00K     28        1       448K nv_stack_t
  5936   5469  92%    0.07K    106       56       424K Acpi-ParseExt
 12544   9249  73%    0.03K     98      128       392K kmalloc-32
  1568   1399  89%    0.25K     98       16       392K kmalloc-256
   686    625  91%    0.54K     49       14       392K idr_layer_cache
   228    172  75%    1.62K     12       19       384K TCP
  2592   2041  78%    0.12K     81       32       324K kmalloc-128
  8320   6251  75%    0.03K     65      128       260K anon_vma
   684    165  24%    0.31K     57       12       228K ip_dst_cache
   221    184  83%    0.94K     13       17       208K signal_cache
  1764   1167  66%    0.09K     42       42       168K kmalloc-96
   189    144  76%    0.75K      9       21       144K files_cache
   171    139  81%    0.81K      9       19       144K mm_struct
    51     33  64%    1.85K      3       17        96K blkdev_queue
  5376   3945  73%    0.02K     21      256        84K kmalloc-16
    36     36 100%    1.75K      2       18        64K TCPv6
  7680   7372  95%    0.01K     15      512        60K kmalloc-8
    69     24  34%    0.69K      3       23        48K fuse_inode
   240    176  73%    0.16K     10       24        40K cfq_io_context
    42     27  64%    0.75K      2       21        32K bdev_cache
   240    182  75%    0.13K      8       30        32K cfq_queue
    38     19  50%    0.81K      2       19        32K rpc_inode_cache
    32     32 100%    0.97K      2       16        32K nfs_inode_cache
    39     26  66%    0.59K      3       13        24K fuse_request
    48     36  75%    0.32K      4       12        16K taskstats
    18      1   5%    0.88K      1       18        16K mqueue_inode_cache
    32     16  50%    0.50K      2       16        16K kmalloc_dma-512
   168     92  54%    0.09K      4       42        16K journal_head
    24     12  50%    0.63K      2       12        16K fat_inode_cache
    66     46  69%    0.18K      3       22        12K file_lock_cache
    39     34  87%    0.30K      3       13        12K blkdev_requests
   340    170  50%    0.02K      2      170         8K numa_policy
   170    170 100%    0.05K      2       85         8K shared_policy_node
    50     50 100%    0.16K      2       25         8K sigqueue
    72     36  50%    0.11K      2       36         8K blkdev_integrity
   146    146 100%    0.05K      2       73         8K nsproxy
    14      1   7%    0.57K      1       14         8K hugetlbfs_inode_cache
   256    256 100%    0.03K      2      128         8K revoke_record
   512    258  50%    0.02K      2      256         8K revoke_table
   340    340 100%    0.02K      2      170         8K journal_handle
   204    102  50%    0.04K      2      102         8K fat_cache
     0      0   0%    0.07K      0       56         0K kmem_cache_node
     0      0   0%    0.38K      0       21         0K xfrm_dst_cache
     0      0   0%    0.25K      0       16         0K dquot
     0      0   0%    0.09K      0       46         0K ext3_xattr


```

On forum I found two simillar topics:
[http://ubuntuforums.org/showthread.php?t=944281](http://ubuntuforums.org/showthread.php?t=944281)
[http://ubuntuforums.org/showthread.php?t=996182](http://ubuntuforums.org/showthread.php?t=996182)
but there was a problem expirienced with real-time kernel, and i never used it.

As far as I understood dentry used 642MB of memory. With 2GB of RAM this is not critical but with other applications running I have 600MB of free memory left and I cannot use more than one memory-hungry application (system starts to swap even when IDE and firefox launched together). I am wondering is this expected behavior, or some kind of bug?
Does anyone know how to free memory used by dentry (slab) without rebooting system, and is it possible to adjust memory used by dentry (slab)?

---

### Post by nutznboltz on 2010-02-04
*Does anyone know how to free memory used by dentry (slab) *

Why do you want to lose the contents of you file system cache?

---

### Post by Chig00 on 2010-02-04
> **nutznboltz said:**
> *Does anyone know how to free memory used by dentry (slab) *

Why do you want to lose the contents of you file system cache?
Is it file system cache?
I don't know what used the memory, what i see is -/+ buffers/cache free is only 593MB, and i didn't see any particular program which used that much memory, so i assumed kernel is responsible for this.
And i don't know kernel internal structure very well, only one memory-consuming part i found at first glance was dentry, so i thought it causes the problem.

---

