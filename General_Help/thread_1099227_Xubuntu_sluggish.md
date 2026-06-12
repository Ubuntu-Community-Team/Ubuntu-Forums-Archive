---
title: "Xubuntu sluggish"
date: 2009-03-17
forum: General Help
---

### Post by burnoutbob on 2009-03-17
Hello all.

I'm not sure if this is the right place for this, or if it should be in the Dell forum.

Ive been given an old Dell Latitude C400 laptop,specs as follows;

1.2Ghz P4 Mobile
256mb Ram
Intel i830 gfx
20Gb HDD

I also have a Belkin wireless card (pcmcia)

It apparently used to run Win2K, and when I got it, it was running XP Pro SP3. However, I decided to get rid of Windows and install Linux. After much research, I opted for Xubuntu 8.10 as a balance between speed and features. However, despite having a half decent cpu, I'm having severe speed issues. Programs and windows take forever to open. SYnapic Package Manager can cripple the system for up to 20 minutes just loading up. And multitasking is out completely!

My prime use for this machine is word processing and basic internet use (research etc - I'm an author, so my internet needs aren't very demanding).

Can anyone shed some light as to what's going on? I've read articles where people have this OS running on much lower spec machines with no problems. I have a feeling it may be graphic card related as I also get blurring and blockiness around windows occasionaly. But that just might be a by product of something else. 

Thanks for your help in advance.

Bob.

---

### Post by lisati on 2009-03-17
> **burnoutbob said:**
> Hello all.

I'm not sure if this is the right place for this, or if it should be in the Dell forum.

Ive been given an old Dell Latitude C400 laptop,specs as follows;

1.2Ghz P4 Mobile
256mb Ram
Intel i830 gfx
20Gb HDD

I also have a Belkin wireless card (pcmcia)

It apparently used to run Win2K, and when I got it, it was running XP Pro SP3. However, I decided to get rid of Windows and install Linux. After much research, I opted for Xubuntu 8.10 as a balance between speed and features. However, despite having a half decent cpu, I'm having severe speed issues. Programs and windows take forever to open. SYnapic Package Manager can cripple the system for up to 20 minutes just loading up. And multitasking is out completely!

My prime use for this machine is word processing and basic internet use (research etc - I'm an author, so my internet needs aren't very demanding).

Can anyone shed some light as to what's going on? I've read articles where people have this OS running on much lower spec machines with no problems. I have a feeling it may be graphic card related as I also get blurring and blockiness around windows occasionaly. But that just might be a by product of something else. 

Thanks for your help in advance.

Bob.

I noticed a change on my other laptop (similar specs) when upgrading from Ubuntu 7.04 to 8.10, which resulted in it appearing sluggish by comparison. So far I haven't found a solution: it works well enough for occasional use.

---

### Post by burnoutbob on 2009-03-18
Thanks for your reply.

I've just finished installing all the updates etc, and there's been a marginal improvement. It's not too bad once a program is loaded, the program works and runs fine. 

If you've noticed a difference after upgrading, I may opt for an older version instead, unless I can find a solution. I don't want to move to DSL or Puppy as others have suggested on other websites. 

If anyone else has any suggestions, it'd be much appreciated. Although I have no data on this laptop, it's still a pain to install another OS if I can get around it!!! :)

Thanks

---

### Post by kerry_s on 2009-03-18
xubuntu is a slow xfce4 setup, i would suggest a base install with xfce4 or trying a different distro's xfce4.

try debian's new lxde setup, it will also do xfce4 if you want to try that.
[http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/debian-testing-i386-xfce+lxde-CD-1.iso](http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/debian-testing-i386-xfce+lxde-CD-1.iso)

---

### Post by fieroboom on 2009-03-18
I have to disagree on this one...

root@paul-desktop:~# cat /proc/meminfo|grep MemTotal
MemTotal:      2006860 kB

root@paul-desktop:~# cat /proc/cpuinfo|egrep 'processor|name|MHz|cache|bogomips'
processor       : 0
model name      : AMD Sempron(tm) Processor 2800+
cpu MHz         : 1599.967
cache size      : 256 KB
bogomips        : 3199.93

root@paul-desktop:~# lspci|grep -i vga
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)

root@paul-desktop:~# uname -a
Linux paul-desktop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

...it's a pretty basic Xubuntu install, and I'm 100% happy with it's speed. How much memory do you guys have?
:D
-Paul

---

### Post by kerry_s on 2009-03-18
> **fieroboom said:**
> I have to disagree on this one...

root@paul-desktop:~# cat /proc/meminfo|grep MemTotal
MemTotal:      2006860 kB

root@paul-desktop:~# cat /proc/cpuinfo|egrep 'processor|name|MHz|cache|bogomips'
processor       : 0
model name      : AMD Sempron(tm) Processor 2800+
cpu MHz         : 1599.967
cache size      : 256 KB
bogomips        : 3199.93

root@paul-desktop:~# lspci|grep -i vga
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)

root@paul-desktop:~# uname -a
Linux paul-desktop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

...it's a pretty basic Xubuntu install, and I'm 100% happy with it's speed. How much memory do you guys have?
:D
-Paul


i don't use xubuntu no more, arch+jwm on 450mhz 256mb ram
```

[Command @ ~]
$ cat /proc/meminfo|grep MemTotal
MemTotal:         255104 kB

[Command @ ~]
$ cat /proc/cpuinfo|egrep 'processor|name|MHz|cache|bogomips'
processor       : 0
model name      : Pentium III (Coppermine)
cpu MHz         : 446.677
cache size      : 256 KB
bogomips        : 893.57

[Command @ ~]
$ lspci|grep -i vga
01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20)

[Command @ ~]
$ uname -a
Linux vaio 2.6.28-ARCH #1 SMP PREEMPT Sun Mar 8 10:18:28 UTC 2009 i686 Pentium III (Coppermine) GenuineIntel GNU/Linux

[Command @ ~]
$ free -m
             total       used       free     shared    buffers     cached
Mem:           249        224         24          0         33         88
-/+ buffers/cache:        102        146
Swap:          956          1        955



```

---

### Post by lisati on 2009-03-18
My "Ubuntu only" Toshiba A100 laptop is:

  CPU: Celeron M, 1.4GHz
  RAM: 222MB available (not sure why, thought it was 256Mb)
  HD: Can't remember, 40Gb? (possibly not relevant)

---

