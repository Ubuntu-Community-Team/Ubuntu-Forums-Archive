---
title: "Using the command hdparm ......"
date: 2006-08-03
forum: Desktop Environments
---

### Post by Ausus on 2006-08-03
Hi All

I wnat to install K3b on my system.
From K3b web-site I looked at the general Question ask.
When I run this command on PC I get the following.
hdparm -v /dev/dvd

/dev/dvd:
 IO_support   =  1 (32-bit)  ok from k3b
 unmaskirq    =  1 (on)      ok from k3b
 using_dma    =  1 (on)      ok from k3b
 keepsettings =  0 (off)     ok from k3b
 readonly     =  0 (off)     ok from k3b
 readahead    = 256 (on)     ok from k3b
 HDIO_GETGEO failed: Invalid argument ](*,) This is what I'm worried about. What is the meaning of this. Will I be able to use k3b software or not. Or is this a Hardware problem.

---

### Post by orb9220 on 2006-08-03
Yes the hdparm is a command to list out the settings for the drive. Don't worry about invalid argument at the end everyone gets that.

the only thing is to make sure using_dma =1 that sometimes dosn't get turned on. And sometimes programs will for no reason turn it off.

sudo hdparm -d1 /dev/hdc for me will reenable dma if it gets turned off.
But otherwise it looks good to go.

---

### Post by orb9220 on 2006-08-03
Deleted

---

### Post by Ausus on 2006-08-03
Hi Orb9220,

Tnx for the reply.

---

### Post by Lord Illidan on 2006-08-03
About the hdio error it's hdparm trying to determine your drive's capacity, but since your DVD-ROM doesn't necessarily have media mounted, that operation fails. You can safely ignore it.

---

