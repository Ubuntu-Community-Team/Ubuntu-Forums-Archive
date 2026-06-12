---
title: "Updated Hardy---now plagued with problems... :("
date: 2009-03-02
forum: General Help
---

### Post by kbfromvt on 2009-03-02
Hello all.  I'm not new to IT, been in the field for over 12 years now, but sadly am a little Windows boy as that is what corporate America raised me to be.  I decided about 6 months ago I wanted to make the switch to Kubuntu on my home computer and have never looked back.  Unfortunately, I'm still not very good with it and rely heavily on GUI.  

I was worried that my system was not getting updated properly and I could possibly be vulnerable to something, what I don't know exactly.  So I reconfigured my Adept to automatically alert me to when only system updates are available.  I was alerted the first time after not updating anything in 6 months and it installed a LOT of packages.  Now my system is nearly unusable.  It's like it just spikes on CPU usage and stays there for 5 minutes before unfreezing.  Then things work ok, then freeze again.  

Help me please, is there ANYthing I can do?  Such as revert to an system state prior to that update I did?  I'm going to have to rebuild at this point unless I get some other advice that works.  

I can tell you it's a 64bit version of Kubuntu, I believe version 8.10? Hardy Heron I think they call it.  I have 2GB of RAM, fairly new AMD processor.

---

### Post by taurus on 2009-03-02
Open a terminal and see which app that spikes your CPU.

```
top
```
or
```
htop
```
if you want a GUI.  (Install it if you don't have it.)

And by the way, hardy is 8.04 while intrepid is 8.10.

```
lsb_release -a
```

---

### Post by kbfromvt on 2009-03-02
I do that and watch and firefox is the only thing that ever gets above 1 on "%CPU" and it goes up to "12" but only for a short burst.

---

### Post by kbfromvt on 2009-03-02
```
top - 18:56:29 up  1:29,  1 user,  load average: 0.05, 0.01, 0.01
Tasks: 113 total,   1 running, 112 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.4%us,  0.2%sy,  0.0%ni, 98.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2062940k total,  1984732k used,    78208k free,  1010076k buffers
Swap:  5911880k total,      172k used,  5911708k free,   539964k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 8842 kyle      20   0  588m 125m  30m S    2  6.2   1:14.52 firefox
 7481 root      20   0  390m  51m 4148 S    1  2.6   0:40.23 Xorg
 8303 kyle      20   0  119m  11m 7920 S    0  0.6   0:00.73 artsd
    1 root      20   0  4020  880  592 S    0  0.0   0:00.78 init
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1
    9 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/0
   10 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/1
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper
   44 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0
   45 root      15  -5     0    0    0 S    0  0.0   0:00.04 kblockd/1
   48 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid
   49 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify
  148 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod
  198 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush
  199 root      20   0     0    0    0 S    0  0.0   0:00.22 pdflush
  200 root      15  -5     0    0    0 S    0  0.0   0:00.10 kswapd0
  243 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0
  244 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1
 1526 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd
 1527 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd
 1560 root      15  -5     0    0    0 S    0  0.0   0:00.00 khpsbpkt
 1588 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/0
 1600 root      15  -5     0    0    0 S    0  0.0   0:00.36 ata/1
 1616 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux
 2367 root      15  -5     0    0    0 S    0  0.0   0:00.00 knodemgrd_0
 2370 root      15  -5     0    0    0 S    0  0.0   0:00.56 scsi_eh_0
 2374 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1
 2403 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_2
 2406 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_3
 2716 root      15  -5     0    0    0 S    0  0.0   0:00.40 kjournald
 2929 root      16  -4 17148 1264  384 S    0  0.1   0:00.40 udevd
 3377 root      15  -5     0    0    0 S    0  0.0   0:00.00 kpsmoused
 7005 root      20   0  3864  588  492 S    0  0.0   0:00.00 getty
 7006 root      20   0  3864  588  492 S    0  0.0   0:00.00 getty
 7008 root      20   0  3864  584  492 S    0  0.0   0:00.00 getty
 7011 root      20   0  3864  588  492 S    0  0.0   0:00.00 getty
 7012 root      20   0  3864  588  492 S    0  0.0   0:00.00 getty
```

---

### Post by taurus on 2009-03-02
You have 2GB of RAM.  How large is your swap partition?

```
free -m
```

p.s.  I see that you have about 6GB of swap space.  Does it only free when you have something running like firefox or does it still freeze (for a moment) even if there is nothing running after you've logged in?

---

### Post by kbfromvt on 2009-03-02
total       used       free     shared    buffers     cached
Mem:          2014       1958         56          0        986        529
-/+ buffers/cache:        442       1572
Swap:         5773          0       5773

---

### Post by kbfromvt on 2009-03-02
> **taurus said:**
> You have 2GB of RAM.  How large is your swap partition?

```
free -m
```

p.s.  I see that you have about 6GB of swap space.  Does it only free when you have something running like firefox or does it still freeze (for a moment) even if there is nothing running after you've logged in?

The problems seem to arise when running a web browser like firefox or Konqueror. For example I will open Firefox and it will half load my google homepage, then freeze for 3-4 minutes before finishing to load the page.  When I say freeze, i mean the whole computer locks up.

---

### Post by kbfromvt on 2009-03-02
This is insane, I need to do something because this Kubuntu box is unusable at this point.  I have three hard disks in this particular system, I can wipe this partition on this disk and lose nothing. I'm thinking I'm just going to wipe and rebuild but hate to do so if it's not that critical.   What about updating my current version of Kubuntu?  Is that an option I could try?

---

