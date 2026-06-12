---
title: "Burning dual-layer DVD sometimes fails."
date: 2008-04-19
forum: Dell  Ubuntu Support
---

### Post by ACGarland on 2008-04-19
I'm using a Dell Inspiron 1420n with preinstalled Ubuntu 7.1 which contains a dual-layer DVD read/write device.

lshw produces the following:
```

           *-cdrom
                description: DVD writer
                product: DVD+-RW DS-8W1P
                vendor: PBDS
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: BD1B
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=ready
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom


```

The drive works great using regular CD or DVD media, but my ability to write dual-layer DVD media is 'hit and miss.'  I've made a few successfully, but I've also had to throw a number away. 

I've seen the same problem both when using k3b and nautilus: the recording gets most of the way through (maybe to the point where it switches layers?) but then a write error failure is reported and I have yet another $2 coaster. :-(

Are there known issues with Ubuntu/nautilus/k3b (or underlying layers) not writing dual layer DVDs reliably?  I'm using Memorex DVD+R DL media--I've always found the Memorex media (in other formats) to be reliable.

This is the only DVD DL device I have so I don't have another drive to try these media in to see whether the problem follows the media or the drive, but I'm assuming it is specific to this laptop/drive/OS.

If anyone else has a Dell Inspiron 1420n and has been reliably cranking out DL DVDs, I'd be interested in hearing about it. Also, if you are experience a similar problem to what I'm seeing.

---

### Post by mannheim on 2008-05-06
I have a different drive but a similar experience:
```
                product: DVD+-RW TS-H653B
                vendor: TSSTcorp

```
This is in a Dell Precision workstation with Ubuntu 8.04. Dual-layer DVDs from Memorex appear to burn okay using k3b, but trying to read them again I tend to get "Input/Output Error" at some point. I haven't investigated this very far.

---

