---
title: "Ubuntus performance is bad compared to windows"
date: 2009-03-04
forum: Desktop Environments
---

### Post by KhaaL on 2009-03-04
Here's the scoop

I have since exactly 3 years ago been using ubuntu exclusively and been happy with it. except with its performance... A while ago i thought it was my harddisk that was faulty somehow because no matter which ubuntu distro or desktop enviorment i used.

Now lately I switched to another harddisk and in order to test performance, i also had windows installed. Now belive me when i realized the sad fact that two crossplatform applications I use works better in windows that in linux. I'm speaking of firefox and savage2. and to be fair, its not that i have higher graphic settings on S2 on ubuntu and lower in windows, its the contrary, S2 works smoothly with maxed graphics on windows. eventually i'm to also install enemy territory and try a replay benchmark in order to compare it to linux. 

besides lower fps/performance, i also get something best described as "hiccups". Savage/firefox freezes for about 1/5 of a second before becoming responsive again. And honestly, i dont know if this is something that can be measured by any test suite considering its best percieved by the human eye.

Now I know ubuntu is always modern compared to windows XP, but there is no excuse for such huge performance drops. linux is supposed a rocket compared to windows in performance since it supports 64bits better. and seriously, who would choose a OS if it makes your computer run slower compared to the one its shipping with? 


The computer and its hardware is [listed here]("http://h10025.www1.hp.com/ewfrf/wc/prodinfoCategory?lc=en&cc=se&dlc=sv&product=3387690&lang=sv&"). using Nvidia 180.35 with 2.6.28-8-generic kernel (64bit)

my fstab:
```
UUID=8576d217-bfd4-4310-a6ad-8992b1537ac1 /               ext4    relatime,noatime,nodiratime,errors=remount-ro 0       1

UUID=2cc37ff1-d84a-4fbc-a5eb-3feb1ed232bb /home           ext4    relatime,noatime,nodiratime,        0       2

UUID=98e694d8-4a12-4b1f-a6dd-e4ace504fa1e none            swap    sw              0       0


```


sdparm output:
```

khaal@Xeraphim:~$ sudo sdparm -a /dev/sda
    /dev/sda: ATA       ST3320820AS       3.AH
Read write error recovery mode page:
  AWRE        1
  ARRE        0
  TB          0
  RC          0
  EER         0
  PER         0
  DTE         0
  DCR         0
  RRC         0
  COR_S       0
  HOC         0
  DSOC        0
  WRC         0
  RTL         0
Caching (SBC) mode page:
  IC          0
  ABPF        0
  CAP         0
  DISC        0
  SIZE        0
  WCE         1
  MF          0
  RCD         0
  DRRP        0
  WRP         0
  DPTL        0
  MIPF        0
  MAPF        0
  MAPFC       0
  FSW         0
  LBCSS       0
  DRA         0
  NV_DIS      0
  NCS         0
  CSS         0
Control mode page:
  TST         0
  TMF_ONLY    0
  D_SENSE     0
  GLTSD       1
  RLEC        0
  QAM         0
  QERR        0
  RAC         0
  UA_INTLCK   0
  SWP         0
  ATO         0
  TAS         0
  AUTOLOAD    0
  BTP        -1
  ESTCT      30

```

If someone has suggestions and ideas on identifying the bottleneck, its most appriciated.

---

### Post by woodenbrick on 2009-03-04
I haven't used savage2, but I can agree with you on firefox being a lot slower on ubuntu than xp and have seen many people complaining about it.  I don't know if ubuntu or firefox is to blame, but I'm too reliant on extensions to change browsers.

---

### Post by arrancaru on 2009-03-04
Firefox is slower in Ubuntu than in Windows because the compilation for Windows includes more optimizations, according to general opinion around the web. Try using swiftfox for a better compiled firefox, but IMHO it makes no huge difference.

---

### Post by KhaaL on 2009-03-04
Note that i'm not only strictly speaking of firefox here, ubuntu in general feels sluggish and it was most noticable with this mentioned game. And to think of it, I think that I experience the same kind of "hiccups" on my eeepc. 

The best thing to do would be to measure the desktop responsiveness - unfortunatly i dont know of any such application that could do it on both windows and linux.

---

### Post by JECHO on 2009-03-04
> **KhaaL said:**
> Here's the scoop

I have since exactly 3 years ago been using ubuntu exclusively and been happy with it. except with its performance... A while ago i thought it was my harddisk that was faulty somehow because no matter which ubuntu distro or desktop enviorment i used.

Now lately I switched to another harddisk and in order to test performance, i also had windows installed. Now belive me when i realized the sad fact that two crossplatform applications I use works better in windows that in linux. I'm speaking of firefox and savage2. and to be fair, its not that i have higher graphic settings on S2 on ubuntu and lower in windows, its the contrary, S2 works smoothly with maxed graphics on windows. eventually i'm to also install enemy territory and try a replay benchmark in order to compare it to linux. 

besides lower fps/performance, i also get something best described as "hiccups". Savage/firefox freezes for about 1/5 of a second before becoming responsive again. And honestly, i dont know if this is something that can be measured by any test suite considering its best percieved by the human eye.

Now I know ubuntu is always modern compared to windows XP, but there is no excuse for such huge performance drops. linux is supposed a rocket compared to windows in performance since it supports 64bits better. and seriously, who would choose a OS if it makes your computer run slower compared to the one its shipping with? 

The computer and its hardware is [listed here]("http://h10025.www1.hp.com/ewfrf/wc/prodinfoCategory?lc=en&cc=se&dlc=sv&product=3387690&lang=sv&").


If someone has suggestions and ideas on identifying the bottleneck, its most appriciated.

The problem is obvious... Youre using an HP. :-p


...seriously though:rolleyes:

---

### Post by Monsieur Gonzalez on 2009-03-05
Well, it could be many things, so :

1- I assume the Nvidia restricted drivers are installed, right?

2 -Are you talking about performance on Jaunty Jackalope or just any previous version?

3 - I found that tweaking ext3 filesystem (see step 2 in [this guide]("http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml") ) gave the system better performance (be aware of the price to pay in case of failure/crash). I feel ext3 is behind NTFS, and hope ext4 will fix that.

4 - Depending on the amount of Ram on your system, you might want to play [with swappiness]("http://ubuntuforums.org/showthread.php?t=834264") 

5 - You may check if desktop indexing gets in the way of other processes.

---

### Post by KhaaL on 2009-03-05
> **Monsieur Gonzalez said:**
> Well, it could be many things, so :

1- I assume the Nvidia restricted drivers are installed, right?

2 -Are you talking about performance on Jaunty Jackalope or just any previous version?

3 - I found that tweaking ext3 filesystem (see step 2 in [this guide]("http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml") ) gave the system better performance (be aware of the price to pay in case of failure/crash). I feel ext3 is behind NTFS, and hope ext4 will fix that.

4 - Depending on the amount of Ram on your system, you might want to play [with swappiness]("http://ubuntuforums.org/showthread.php?t=834264") 

5 - You may check if desktop indexing gets in the way of other processes.


Thanks for the detailed post. 

I'm using Nvidia 180.35 with 2.6.28-8-generic 64bit, Got 2 gigs of ram and no indexing is running.

Additionally since something might be haywire with my harddisk configuration i decided to post my fstab settings:

```
UUID=8576d217-bfd4-4310-a6ad-8992b1537ac1 /               ext4    relatime,noatime,nodiratime,errors=remount-ro 0       1

UUID=2cc37ff1-d84a-4fbc-a5eb-3feb1ed232bb /home           ext4    relatime,noatime,nodiratime,        0       2

UUID=98e694d8-4a12-4b1f-a6dd-e4ace504fa1e none            swap    sw              0       0


```


And finally, sdparm:
```

khaal@Xeraphim:~$ sudo sdparm -a /dev/sda
    /dev/sda: ATA       ST3320820AS       3.AH
Read write error recovery mode page:
  AWRE        1
  ARRE        0
  TB          0
  RC          0
  EER         0
  PER         0
  DTE         0
  DCR         0
  RRC         0
  COR_S       0
  HOC         0
  DSOC        0
  WRC         0
  RTL         0
Caching (SBC) mode page:
  IC          0
  ABPF        0
  CAP         0
  DISC        0
  SIZE        0
  WCE         1
  MF          0
  RCD         0
  DRRP        0
  WRP         0
  DPTL        0
  MIPF        0
  MAPF        0
  MAPFC       0
  FSW         0
  LBCSS       0
  DRA         0
  NV_DIS      0
  NCS         0
  CSS         0
Control mode page:
  TST         0
  TMF_ONLY    0
  D_SENSE     0
  GLTSD       1
  RLEC        0
  QAM         0
  QERR        0
  RAC         0
  UA_INTLCK   0
  SWP         0
  ATO         0
  TAS         0
  AUTOLOAD    0
  BTP        -1
  ESTCT      30

```

---

### Post by KhaaL on 2009-03-06
I think my issue is related to [this old bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094"). I'm going away over the weekend so I'll have to dig into this once I return home. In worst case I'll have to try my luck with another distro.

---

### Post by shankru85 on 2009-03-06
Honestly, i feel the opposite that is felt in this thread. I feel firefox is much faster in linux than in windows especially the first time i start firefox from quick launch button. In linux, it fires up faster than windows. But i am not sure about Savage2. I havent played it. And speaking of general performance, My ubuntu boot time is twice smaller than windows and i dont feel any sluggishness even i had about 10-12 different applications open at the same time.

Whereas windows becomes slower and slower on each reboot.. Btw, i dont have this NVIDIA graphics card.

---

### Post by linux_tech on 2009-03-07
You could try swiftfox [http://getswiftfox.com/](http://getswiftfox.com/)
or try some optimizations for firefox, there are many suggestions on the web for firefox optimization.

---

### Post by KhaaL on 2009-03-08
Alright, I've been digging deeeep in order to find something useful on this. it seems that I'm affected by these bugs:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131094](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131094)
[http://bugzilla.kernel.org/show_bug.cgi?id=12309](http://bugzilla.kernel.org/show_bug.cgi?id=12309)

In short, speculation is that the I/O Scheduler makes the system crawl during heavy disk activity. you can try this yourself by running 
**dd if=/dev/zero of=~/test bs=1M count=1500**
(warning: this will write a 1,5 GB file to your home folder!)

Of course this can be set by setting the scheduler to as (anticipatory) but it will only perform well because it *anticipates* the null data. combine dd if=/dev/zero of=~/test bs=1M count=1500 and dd if=/dev/urandom of=~/test bs=1M count=1500 and the system will crawl again.

I'll keep diggin and posting on this issue...

---

