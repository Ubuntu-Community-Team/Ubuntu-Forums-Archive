---
title: "my laptop crashed after updating"
date: 2009-02-21
forum: General Help
---

### Post by mefistofeles666 on 2009-02-21
using ubuntu 8.04.2 on a toshiba.

I just installed all the updates and when i restarted it asked me for the user name and password as usual, but when I hit enter it went black and restarted itself, after the "ubuntu loading" screen the orange bar stops right at the end and after a minute it starts giving me and error over and over and over. it reads as follow

doing wacom set up
(whole lot of crap that I can read bc it goes away very fast)

in
[ 56.some-numbers] ata1.00:status: {DRDY ERR}
[ 56.some-numbers] ata1.00: error: {UNC}
[ 56.some-numbers] ata1.00:exception Emask 0x0 SAct 0x0 SErr 0x0 action 0c0
[ 56.some-numbers] ata1.00:BMDMA stat 0x24
[ 56.some-numbers] ata1.00: CMD c:c0:7d/00:00:00:00:00/e5 tag 0 dma 4096 i


and then it keeps giving me the same lines nonstop.

any ideas? is there a way to fix it without losing my files? using dpkg safemode doesn't work.  could I upgrade maybe to the new 8.10 version  without losing my files?


thanks

---

### Post by Peter09 on 2009-02-22
That looks like a Hard Disk problem. Try using a LiveCD and when that comes up have a look at the drive.

---

### Post by mefistofeles666 on 2009-02-22
im somewhat new to ubuntu, how would I go about checking my hard drive? and if it is the hard drive, is there a way to fix it?

---

### Post by Peter09 on 2009-02-23
If your hard drive has gone then fixing it is not really possible. If you boot from the LiveCD and then in a terminal type

```
lshw -C storage
```


and

```
df -h
```



the output will tell you more about you hard disk state

---

