---
title: "DMA issue"
date: 2005-09-17
forum: Desktop Environments
---

### Post by dylanknightrogers on 2005-09-17
Hi everyone!

I have 2 optical drives:  a DVD+R DL drive and a CD-R/RW drive.

I am a Linux noob, so bear with me.  Thanks in advance.

OK, here's the issue:  On Windows, the drives run really really fast.  I then did a hdparm on both the drives (/hdd and /hdc) and found that they both had DMA turned off.

I edited my hdparm.conf file and attempted to turn DMA on, rebooted, etc. but still nothing happened in my favor.

Then, I edited /etc/init.d/bootmisc.sh and added

hdparm -d1 /dev/hdd /dev/hdc

before the END line and found that it turned the using_dma option to 1 on a reboot.

However, the drives still ran slower than they did on Windows.  The DVD drive is 8x, and the CD-R/RW drive is 52x for read and 52x/32x for CD-R and RW respectively.

What the heck is wrong here?

Thanks a googl.  Keep up the great work!

-Dylan

---

### Post by mlomker on 2005-09-17
> 
hdparm -d1 /dev/hdd /dev/hdc


Try 

```

hdparm -d1c1 /dev/hdc

```

---

### Post by dylanknightrogers on 2005-09-17
In the bootmisc.sh file or just in the terminal right now?

I did it in the terminal and Sound Juicer still only runs at 3.5x.

Hmmmm...


EDIT:  I edited the bootmisc.sh file with the code you specified and alas, nothing.

---

### Post by mlomker on 2005-09-17
I'm not familiar with Sound Juicer.  I added that combination to my bootmisc.sh and the speed of my CDR burns doubled.

I suppose I should look for a performance testing application of some kind and experiment with settings...

---

### Post by dylanknightrogers on 2005-09-17
[QUOTE=mlomker]I'm not familiar with Sound Juicer.  I added that combination to my bootmisc.sh and the speed of my CDR burns doubled.

I suppose I should look for a performance testing application of some kind and experiment with settings...[/QUOTE]
 Its dylanknightrogers again:

Um, maybe the reason Sound Juicer doesnt write as fast is because it must encode/decode the songs before it actually writes?

Who knows?

Im hoping my DMA issues are resolved.

---

