---
title: "poor performance with nautilus"
date: 2006-06-11
forum: Desktop Environments
---

### Post by fallencan on 2006-06-11
hi
i'm sort of new to linux. i've been using ubuntu about 1 months and desktop performance is too bad. when i try to copy some files from one partition to another it takes ages to complete it. and while copying file my system is kinda unusable. starting apps takes about 30 seconds. and top shows about 40.xx load average.
is there any thing to speed up my computer?

my specs
pentium m 1.6
768mb ddr333 ram
40gb hdd
128mb ati9700se

edit: i tried kubuntu and xubuntu and nothing changed. and dma is on.

---

### Post by glotz on 2006-06-11
Any special boot parameters, like hdd cylinder translation? That'd bog you right down. Your setup is somehow borked, my old puter is a lot faster.

---

### Post by kaamos on 2006-06-11
You should check if you have working [dma](http://en.wikipedia.org/wiki/Direct_memory_access).

Open a terminal and use
```
sudo hdparm -d /dev/*hda*
```
to check. The hda part could be something else for you, use "sudo fdisk -l" to list your drives.

---

### Post by fallencan on 2006-06-11
nothing special with with config files or boot parameters. just a clean install and ati fglrx drivers. by the way to copy 2.5gb of data took about 50 minutes. something is terrible wrong with my computer.

---

### Post by fallencan on 2006-06-11
it look like dma is on

```
$ sudo hdparm -d /dev/hda

/dev/hda:
 using_dma    =  1 (on)
```

[QUOTE=kaamos]You should check if you have working [dma](http://en.wikipedia.org/wiki/Direct_memory_access).

Open a terminal and use
```
sudo hdparm -d /dev/*hda*
```
to check. The hda part could be something else for you, use "sudo fdisk -l" to list your drives.[/QUOTE]

---

### Post by kaamos on 2006-06-11
[QUOTE=fallencan] by the way to copy 2.5gb of data took about 50 minutes. something is terrible wrong with my computer.[/QUOTE]

Yea, that doesn't sound right.. Did you check that the partition that you are copying to also has dma?

---

### Post by fallencan on 2006-06-11
both partitions are on the same drive (hda1 and hda3) so dma is on for both of them. must be something else.

---

### Post by fallencan on 2006-06-12
i did a clean installation. and installed only updates and 686 kernel. but nothing changed. any other sugestions about this problem?

---

