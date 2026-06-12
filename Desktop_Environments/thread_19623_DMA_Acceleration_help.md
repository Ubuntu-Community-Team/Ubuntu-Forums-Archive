---
title: "DMA Acceleration help?"
date: 2005-03-12
forum: Desktop Environments
---

### Post by bored2k on 2005-03-12
> NeroLinux has detected that DMA acceleration is disabled. It provides faster throughput for the IDE recording devices.

You should enable it for /dev/hdb (DVDR/RW DX162D-A)
 

Anyone knows how to do this ?

thanks in advance.

---

### Post by dtessier on 2005-03-12
sudo hdparm /dev/hda (or whathever device your HD is) ought to do the trick.

---

### Post by bored2k on 2005-03-12
[QUOTE=dtessier]sudo hdparm /dev/hda (or whathever device your HD is) ought to do the trick.[/QUOTE]
 Thanks  a lot. This worked:
$ sudo hdparm -d1 -X /dev/hdb 

/dev/hdb:
 setting using_dma to 1 (on)
 setting xfermode to 0 (default PIO mode)
 using_dma    =  1 (on)
8846-2670-6597-3706-7147

---

### Post by phvash on 2005-03-13
You can also have that done at that boot time by adding the appropriate entries to /etc/hdparm.conf

---

### Post by bored2k on 2005-03-13
[QUOTE=phvash]You can also have that done at that boot time by adding the appropriate entries to /etc/hdparm.conf[/QUOTE]
 Can you tell me how?

---

### Post by bobmitch on 2005-03-13
[QUOTE=bored2k]Can you tell me how?[/QUOTE]

Had the same problem - solution and implementation details provided by a useful guy in [this](http://www.ubuntuforums.org/showthread.php?t=17071&highlight=hdparm.conf)  thread.

Good luck.

---

### Post by fluideye on 2005-05-13
> Thanks a lot. This worked:
$ sudo hdparm -d1 -X /dev/hdb 

Worked for me too!

---

