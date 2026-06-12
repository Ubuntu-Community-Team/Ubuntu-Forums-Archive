---
title: "Hdparm don't work"
date: 2005-06-11
forum: Desktop Environments
---

### Post by Vurdak829 on 2005-06-11
I've a problem..i have a dvd writer and a dvd player (both LG's) and a Maxtor hard drive (ide). When i use hdparm i've this problem.

> vurdak@ubuntu:~$ sudo hdparm -d1 /dev/hdd


/dev/hdd:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off) 

My hdparm.conf 
Note: also with this hdparm, dma is not active yet..

> /dev/hda {
	dma = on
}

/dev/hdb {
	dma = on
}

/dev/hdd {
	dma = on
} 

hda and hdb are my dvd writers.

I have Ubuntu/Kubuntu hoary
Athlon 3400+
Motherboard: asus k8v se-delux
Hard disk: maxtor 120Gb 7200rpm

---

### Post by skoal on 2005-06-11
[QUOTE=Vurdak829]hda and hdb are my dvd writers.[/QUOTE]
I assume then that "hdd" is your Maxtor drive?  If so, does DMA work for both hda/hdb (your DVD writers)?  It's only the hard drive which DMA doesn't work?

\\//_

---

### Post by Vurdak829 on 2005-06-11
[QUOTE=skoal]I assume then that "hdd" is your Maxtor drive?  If so, does DMA work for both hda/hdb (your DVD writers)?  It's only the hard drive which DMA doesn't work?

\\//_[/QUOTE]

Sorry for the error. DMA don't work for hda, hdb and hdd :(

---

### Post by kleeman on 2005-06-11
Check out this thread

[http://www.ubuntuforums.org/showthread.php?p=93238#post93238](http://www.ubuntuforums.org/showthread.php?p=93238#post93238)

This kind of problem has occured often.....

---

### Post by Vurdak829 on 2005-06-11
[QUOTE=kleeman]Check out this thread

[http://www.ubuntuforums.org/showthread.php?p=93238#post93238](http://www.ubuntuforums.org/showthread.php?p=93238#post93238)

This kind of problem has occured often.....[/QUOTE]

Ok, thank you. I haven't seen this topic yet :D

---

