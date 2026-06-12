---
title: "100% CPU usage not show in process list"
date: 2009-02-05
forum: General Help
---

### Post by jasonmh on 2009-02-05
I have Ubuntu 8.10 Intrepid

**Symptoms**: For no apparent reason, my hard drive will become very active and sound as if I'm copying a huge file, everything will slow down as if 100% of my CPU is being used, and my internet activity will max out (mostly download bandwidth, but some upload as well).

**Attempts to find the issue**: When I open the System Monitor (under System->Administrator), the Resource tab will say my CPU is at 100% with most of my RAM being used, however the process list won't show any processes using over 10% and nowhere near the total RAM usage. In Terminal a ps -Al will show the same as in System Monitor.

Obviously, something is running under the surface, but I'm not sure how to find out what it is! Any help would be greatly appreciated please.

---

### Post by bff7755a on 2009-02-05
Maybe it's trackerd.

Try 

```
ps aux | grep trackerd
```

Try to kill process. If it is, you may remove it from your system:

```
sudo apt-get remove tracker
```

---

### Post by jasonmh on 2009-02-06
I removed trackerd and that has removed much of my lag, however I've now found the real culprit.  I have the latest version of Vuze (torrent downloader) installed, which hasn't been authorized/modified by the Ubuntu group.  When Vuze completes downloading a large file (+700mb type stuff), then some unknown process grabs a junk load of CPU power and won't release it. I still have to reboot, but at least now I know someone hasn't taken over my computer.

---

### Post by hyper_ch on 2009-02-06
vuze is bloat.... if you want to go really light-weight then use rTorrent. It's light, powerfull and works on the command line.

---

### Post by mb_webguy on 2009-02-06
I use Deluge as my torrent client, and have been very happy with it.  Of course, as hyper_ch said, if you want a really lightweight torrent client, go with rTorrent.

---

### Post by jasonmh on 2009-02-06
Fantastic :D Thank you all for the help. I'm trying real hard to make the Windows->Linux switch, but the learning curve can still be pretty steep at times.

I agree that Vuze is way bloated, but I do like many of its features. Such as the subscription, in-program searching, and their iTunes style homepage that shows me things I may be interested in.

---

