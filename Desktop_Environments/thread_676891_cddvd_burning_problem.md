---
title: "cd/dvd burning problem"
date: 2008-01-24
forum: Desktop Environments
---

### Post by Selmi on 2008-01-24
i have strange problem with burning of dvds and cds on one of pc's i am work with. burning starts well, but while cpu usage is always shown almost 0% average load is getting bigger and bigger and computer doesn't respond at all. also burning is extremely slow

i checked that dma is enabled for drive (udma2 is used). in /var/log/* i noticed noting special mentioned, only this:

```
Jan 24 14:11:08 seligovci kernel: [11897.568135] cdrom: hdb: mrw address space DMA selected                                                                  
Jan 24 14:11:08 seligovci kernel: [11897.591316] cdrom open: mrw_status 'not mrw'                                                                            
Jan 24 14:11:08 seligovci kernel: [11897.789104] cdrom: hdb: mrw address space DMA selected                                                                  
Jan 24 14:11:08 seligovci kernel: [11897.793026] cdrom open: mrw_status 'not mrw'                                                                            

```

i don't know what it means but it can be related to loading empty cd so its not big help

this also happens when i blank cdrw, but it eventually ends, burning dvd works with little of patience only it takes about 40-60 minutes, with burning of cds i never had enough patience to wait for finish. 

also when copying to dvd-ram it says that 4gb will be copied in 54 hours or so (and again, pc is almost not responding and load is terrible)

it all happens with gutsy, cd writer TSSTcorpCD/DVDW SH-S182M 

with reading of cd/dvd/dvdrw/cdrw/ etc there is not problem at all

any idea what can be wrong?

i already tried another dvd burner (some NEC), it behaved the same....

---

### Post by metalheart on 2008-01-24
How much RAM you have installed on the PC? If you have little RAM the recording buffer will be set small and recording is slow. Try to close all other programs before recording.

What software you use for recording?

Are you recording compilation of individual files or iso images? Try to build image first and transfer it to the disk.

---

### Post by Selmi on 2008-01-24
> **metalheart said:**
> How much RAM you have installed on the PC? If you have little RAM the recording buffer will be set small and recording is slow. Try to close all other programs before recording.

What software you use for recording?

Are you recording compilation of individual files or iso images? Try to build image first and transfer it to the disk.

memory is 768mb of which ~50% was occupied by user programs and rest is for cache. also lot of swap is available (4gb) of which max 5-10% is used in normal conditions. i tried burning with everything else switched off and it dedint helped

for recording i tried k3b and gnomebaker and nautilus burning. results are much worse with k3b which stops responding almost immediately. gnomebaker and nautilus behave better

when i tried burning with isoimage burning worked much better, thanks for idea. but still, on same pc i had before versions 6.06 and it behaved much better with burning then gutsy - i just forgot to mention it in first post

---

### Post by metalheart on 2008-01-24
I think you can set some recording options in K3B for growisofs program (K3B is using it for recording). One undocumented option is setting the buffer size

```
-use-the-force-luke=bufsize:XXX
```

Replace XXX with 32M for start and try again, although I am not sure if it will work in Ubuntu.

FYI: The default buffer size for growisofs is 1/4 of free available RAM. I suspect the lack of free RAM is the problem.

---

