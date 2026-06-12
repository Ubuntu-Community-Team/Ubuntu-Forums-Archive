---
title: "Dell Inspiron b130 running Natty Narwhal w/2gbs ram runs slow"
date: 2012-06-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Da.itouch on 2012-06-25
Hi. New poster to the forums.

I recently got a a Dell Inspiron B130 and I installed Natty Narwhal. It had 256x2 ram (512ram total) and I upgraded to 1GB x 2 (2gb total) last night.

The OS runs exactly the same. When I booted up, the BIOS recognized the new ram, but there aren't any differences (save in the Linuxkart game).

Everything runs exactly the same - which is to say...SLOW. 

Is it my 1.4ghz celeron processor?

Please help. I am thinking of installing an XP partition so that I can at least see the 2gb's being used....;)

---

### Post by irv on 2012-06-25
> **Da.itouch said:**
> Hi. New poster to the forums.

I recently got a a Dell Inspiron B130 and I installed Natty Narwhal. It had 256x2 ram (512ram total) and I upgraded to 1GB x 2 (2gb total) last night.

The OS runs exactly the same. When I booted up, the BIOS recognized the new ram, but there aren't any differences (save in the Linuxkart game).

Everything runs exactly the same - which is to say...SLOW. 

Is it my 1.4ghz celeron processor?

Please help. I am thinking of installing an XP partition so that I can at least see the 2gb's being used....;)
Are you saying that Ubuntu is not seeing the memory? At the command line type this:
```
cat /proc/meminfo
```
then copy and paste here.

---

### Post by Da.itouch on 2012-06-25
Thank you. Here's the info:



MemTotal:        2052192 kB
MemFree:         1542596 kB
Buffers:           46824 kB
Cached:           302012 kB
SwapCached:            0 kB
Active:           154088 kB
Inactive:         309676 kB
Active(anon):     115712 kB
Inactive(anon):   115748 kB
Active(file):      38376 kB
Inactive(file):   193928 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:       1179476 kB
HighFree:         751924 kB
LowTotal:         872716 kB
LowFree:          790672 kB
SwapTotal:       1531900 kB
SwapFree:        1531900 kB
Dirty:                 0 kB
Writeback:             0 kB
AnonPages:        114968 kB
Mapped:            52296 kB
Shmem:            116516 kB
Slab:              19552 kB
SReclaimable:      10640 kB
SUnreclaim:         8912 kB
KernelStack:        2032 kB
PageTables:         4096 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     2557996 kB
Committed_AS:    1071256 kB
VmallocTotal:     122880 kB
VmallocUsed:       23460 kB
VmallocChunk:      93772 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       20472 kB
DirectMap4M:      888832 kB



It does read the ram, but it's still slow to boot, run processes, etc. That normal?

---

### Post by irv on 2012-06-25
I tried to compare my reading with your, but I have 2gig more memory in my Inspiron 1521, with a AMD 64 dual core processor.
I looked up the specs on your Inspiron b130, and it said it came with 512mb and was upgrade able to 1gb. I am not sure if this is right or not.
[ATTACH]220237[/ATTACH] 

It took me some time to post this because the forum is really running slow for some reason.

---

### Post by Da.itouch on 2012-06-25
You are quite right - it maxes out at 1GB. 

As for it's sluggishness, which appears in select areas (ex. launcher), is that as a result of my processor's power (or lack thereof)?

It's a 1.40GHz, Intel Celeron M. 
I have 2gb's (1gb functioning as you know)

Thanks again Irv.

---

### Post by irv on 2012-06-25
> **Da.itouch said:**
> You are quite right - it maxes out at 1GB. 

As for it's sluggishness, which appears in select areas (ex. launcher), is that as a result of my processor's power (or lack thereof)?

It's a 1.40GHz, Intel Celeron M. 
I have 2gb's (1gb functioning as you know)

Thanks again Irv.

It just so happens that I have a Intel Celeron M process in one of my older laptops that I use on a sound system for recording. I got Ubuntu Studio 12.04 running on it. I had to install and older version and then upgrade to get it installed but it works. A little on the slow side to get started but once it is going it runs OK. Studio comes with the Xfce desktop which is better for slower machines. You truly are at the low end with this hardward.

There are other options to try if you want. Like Xubuntu, Lubuntu, DSL, Puppy Linux, Mint, Peppermint, even some not supported one, gOS. The list goes on and on. Check out Distro Watch.

---

