---
title: "MicroSD ramps system load during copy"
date: 2007-09-16
forum: Desktop Environments
---

### Post by craftbrewer on 2007-09-16
Ubuntu 7.04 Desktop
Generic 6in1 Cardreader / Motorola A1200 
Kingston 2GB transflash/MicroSD
/home partition is NFS mounted.

Writing anything substantial to this card pushes my system load up to 10, crippling system response.
CPU is idle, memory is only 38% utilized, absolutely no errors being logged on desktop or from the nfs server.

The card is formatted as FAT16, no problems with mounting it or anything.  When using it through the phone, at times I have to delete what I copied as the phone cannot read it due to corruption.  When copy through the 6in1 using the SD adapter it just ramps the load up and frequently stalls during the copy.   No stall message, but when I sits on a 5MB file with no NFS network traffic for 5-10 minutes, then zips through the next few files like nobodies business, I'm pretty sure its stalled.  Also, it tends to be "Writing data to device" up to 10 minute after the copy completes.  This is nuts.

Anyone know what's going on?   Any resolution?

---

