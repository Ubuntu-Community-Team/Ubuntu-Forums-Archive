---
title: "Xorg Memory Leak"
date: 2005-11-24
forum: Desktop Environments
---

### Post by endersshadow on 2005-11-24
My Xorg leaks like I just hit an iceburg, and I can't figure out why.  I'm running Breezy on a laptop that needs the 855resolution patch for my Intel driver, but it shouldn't be leaking like this. It starts at about 150megs and goes to about 180 or so of ram.  I've got 512, and that should be more than enough.  Here's my xrestop:

```
xrestop - Display: localhost:0
          Monitoring 25 clients. XErrors: 0
          Pixmaps:   31397K total, Other:     102K total, All:   31500K total

res-base Wins  GCs Fnts Pxms Misc   Pxm mem  Other   Total   PID Identifier
2000000    93   46    1  725   35    18537K      5K  18542K   ?   Ubuntu Forums - Post New Thread - Mozilla Firefox
3600000     0    0    0    1    0     5742K      0B   5742K   ?   <unknown>
1e00000    32  186    1  170   33     1267K      6K   1274K  8038 gdesklets-daemon
0c00000    12   27    2    4  720      780K     19K    799K  7990 metacity
2200000    20   31    0    4   36      780K      2K    782K  8038 wnck-applet
2400000    19   32    1    5   15      421K      2K    423K  8038 trashapplet
2800000   138   33    1    6   50      397K      6K    403K   ?   Buddy List
2c00000    27   29    1    4   31      393K      3K    396K   ?   eric@homesteadgrays: ~
3000000    41   32    1    4   45      386K      3K    390K   ?   System Monitor
1000000    21   34    1    4   17      386K      2K    389K  7995 Bottom Edge Panel
1200000     9   34    1    5   15      386K      2K    388K  7997 Desktop
1c00000     3   27    1    2   11      384K      1K    385K 13674 mail-notification
1800000     2    2    1    2   27      384K      1K    385K  8020 notification-daemon
2600000    12   33    0    2   13      384K      1K    385K  8038 mixer_applet2
1400000    10   26    0    2   11      384K      1K    385K  7995 hook-notifier
0600000     2    2    0    2   10      384K    336B    384K  7867 gnome-session
0a00000     1  558    1    0  467        0B     25K     25K   ?   screensaver
0800000     4    1    0    0  535        0B     12K     12K  7947 gnome-settings-daemon
1600000    10   26    0    1    8        4B      1K      1K  7995 notification-area-applet
0200000     0    1    1    0    0        0B      1K      1K   ?   <unknown>
0e00000     4   25    0    1    5        4B    816B    820B  7999 gnome-volume-manager
2a00000     3   25    0    1    3        4B    744B    748B  8460 evolution-exchange-storage
1a00000     3   25    0    1    3        4B    744B    748B  8018 gnome-cups-icon
2e00000     1    1    0    0    0        0B     48B     48B   ?   xrestop
0400000     0    1    0    0    0        0B     24B     24B   ?   <unknown>
```

Thanks in advance for any help.

I forgot to mention, Happy Turkey Day!!

---

