---
title: "RAID 1, Samba, Streaming issue"
date: 2009-04-24
forum: General Help
---

### Post by buck2825 on 2009-04-24
I tried posting this under Multimedia and got no response.  

help please!!!

my file server is a ubuntu desktop 8.04 with samba and mdadm installed i have three hard disks one 40 for os and configuration and two 1.5 tb for storage the 1.5 tb are mirrored and mounted at /mnt/storage.

clients:
xbox softmod xbmc(original)
laptop ubuntu 8.10 (wired or wireless)

player software:
VLC (laptop)
mplayer (laptop)
xbmc (laptop and xbox)

when I play a video over the network the movie will play for a period of time. The time seems to change randomly. the movie will pause for about 5 sec. then resume, play for about 1/4 sec then crash. this only happens with the file on my raid. if i move the file to ~/Desktop/ (on 40gb hd) then everything is fine. please help.

Thanks in advance

---

### Post by fjgaude on 2009-04-24
Is your CPU and memory fast enough to support the software raid? This could be the issue you face.

---

### Post by buck2825 on 2009-04-27
CPU is an AMD 2.8 GHz (single core), with 2 GB of ram. 

do I really need to worry about, speed.  

how do i monitor the utilization of my raid or any other hard drive?

---

### Post by fjgaude on 2009-04-27
Worry about speed, perhaps. If you do other things while you are streaming there could be an issue with only one CPU.

The only monitors for drives I use are **iotop** (CLI) and **gkrell**. The latter takes some setup for a system but is well worth the effort.

You can always test your read thru-put using **hdparm**:

```
sudo hdparm -tT /dev/md0
```

Or whatever your array is called.

---

### Post by buck2825 on 2009-05-01
did some preliminary testing last night looks like one of my hard disks is hitting 100 utilization while I play movies from the RAID.  I will run down some specifics but for now does anyone have any tips on tweaking mdadm or other set-up items to maybe help with this issue.

---

