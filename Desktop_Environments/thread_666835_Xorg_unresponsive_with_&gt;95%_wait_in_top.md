---
title: "Xorg unresponsive with &gt;95% wait in top"
date: 2008-01-13
forum: Desktop Environments
---

### Post by mathisdermaler on 2008-01-13
When browsing some web pages in firefox, the desktop becomes almost completely unresponsive (minutes for each keystroke/mouse click to register.)  This is quite annoying because I have to wait minutes just to open a terminal window to kill a process or run top.

This problem seems to be caused by loading "tall" web pages with lots of images in firefox, such as the perpetual photography thread on ArsTechnica:  [http://episteme.arstechnica.com/eve/forums/a/tpc/f/67909965/m/6380951884](http://episteme.arstechnica.com/eve/forums/a/tpc/f/67909965/m/6380951884)

When I finally waited for a terminal I found that the process usage is usually around .2% user, 4 % system, and 95% wait.  Basically, all the user process (Xorg included) are being starved for CPU time.  Why is the system spending so much time in a wait state?

To prevent it from waiting on disk activity because of swap, I disabled my swap partition, but it made no difference.  My video card is an onboard nvidia 6150 series in case anyone is interested. 

Any ideas?

Thanks
Paul

Sample 'top' output:
```

top - 18:53:30 up 12 days, 19:18,  4 users,  load average: 1.53, 5.67, 10.30
Tasks: 126 total,   1 running, 124 sleeping,   0 stopped,   1 zombie
Cpu(s):  1.7%us,  3.9%sy,  0.0%ni,  0.0%id, 93.9%wa,  0.0%hi,  0.6%si,  0.0%st
Mem:   1002088k total,   990988k used,    11100k free,      172k buffers
Swap:        0k total,        0k used,        0k free,    51152k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
29416 paul      15   0  280m 138m 3084 S  2.0 14.1 135:40.69 mozilla-bin
 3522 paul      16   0  188m  35m 1516 D  1.4  3.7   0:18.61 firefox-bin
 3555 paul      16   0  2364  640  352 R  0.6  0.1   0:00.28 top
29047 root      15   0  425m 389m  828 S  0.6 39.8  90:56.22 Xorg
29174 paul      15   0 16960 2420 1060 S  0.6  0.2   1:01.99 gnome-screensav
  195 root      10  -5     0    0    0 D  0.3  0.0   0:12.76 kswapd0
 3463 paul      15   0  2368  544  252 S  0.3  0.1   0:04.06 top
29125 paul      15   0 98448  12m 1080 S  0.3  1.3   1:02.95 gnome-panel
    1 root      16   0  2948 1352   32 S  0.0  0.1   0:01.55 init

```

---

### Post by mathisdermaler on 2008-01-13
So I tried running vmstat also.  If I read this right, it's reading between 28 and 115 megabytes per sample (supposed to be once a second but it slowed down a lot) in the stats shown below.  Anyone know of a utility similar to top or vmstat that will show me what process is responsible for this, what files are actually being read, etc?

```

procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 1 29      0  10800    128  47812    0    0 28880     0 1255 2688  0 13  0 87
 0 31      0  10920    112  47128    0    0 93460     0 3906 8808  0 18  0 82
 0 28      0  11004    120  47248    0    0 115296    16 2323 5182  0 17  0 83
 0 24      0  11164    128  47068    0    0 29264    32 5852 12324  0 13  0 87
 0 25      0  11020    136  47128    0    0 18628     0 1144 2496  0 15  0 85
 1 23      0  11352    116  47092    0    0 19652     0 1409 3048  0 15  0 85
 0 25      0  11032    148  47428    0    0 30900    16  904 1929  0 16  0 84
 0 19      0  10784    140  47852    0    0 84340     0 3750 7979  0  9  0 91
 0 21      0  10796    132  47248    0    0 32536     0 2948 6505  0 11  0 89
 0 27      0  11116    108  47056    0    0 29796     0 1619 3553  0 12  0 88

```

---

