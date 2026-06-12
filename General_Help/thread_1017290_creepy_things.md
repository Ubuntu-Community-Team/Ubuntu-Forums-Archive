---
title: "creepy things"
date: 2008-12-20
forum: General Help
---

### Post by jazott3 on 2008-12-20
so i dual boot ubuntu and windows xp and i tried booting into xp and it said go to startup repair, missing \WINDOWS\system32\drivers\pci.sys and i figured great now i have to go get the file and drop it in under /media/sda2 in ubuntu.... well.... Went there, in the terminal went to the drivers directory under /media/sda2/WINDOWS/....... and tried the ls command. i got a general i/o error. before that I was getting ata errors but I haven't gotten any of those anymore yet. Now, I startup firefoxx to get help and the title bar is GONE!!! there is nothing in the task-bar-panel on the bottom of the screen, the panel at the top of the screen is gone, and the (normally orange) bar is GONE. I am n00b1sh so i need lots of help.... Thnx for all you nice guys out there!

PS these smilies are cool
[:guitar:]

---

### Post by jerome1232 on 2008-12-20
Sounds like either:

A) Your HDD (Hard Disk Drive) is dieing.

or

B) The cable for your HDD is bad or the connection is loose.

or

C) The Hard Disk controller on the motherboard is dieing.

Most likly A, or B ( I had C happen to me recently)

---

### Post by jazott3 on 2008-12-20
THANK YOU!!!
I hope it's B, although I have my doubts cause it's a laptop... I think my hard drive's dying because I've accidentally dropped my machine a couple of times lately, the pci.sys wasn't missing till i had a BSOD at the welcome screen, and my machine's 2 years old and been through multiple reformats (i do a lot of reinstalling xp every 3 months or so, and ubuntu too, i dunno why)


What can I do to see if it IS dying?

---

### Post by jerome1232 on 2008-12-20
> **jazott3 said:**
> THANK YOU!!!
I hope it's B, although I have my doubts cause it's a laptop... I think my hard drive's dying because I've accidentally dropped my machine a couple of times lately, the pci.sys wasn't missing till i had a BSOD at the welcome screen, and my machine's 2 years old and been through multiple reformats (i do a lot of reinstalling xp every 3 months or so, and ubuntu too, i dunno why)


What can I do to see if it IS dying?

edit: Read the question wrong; I thought you asked if it is dying

Well not much; if you have any large external hard drives or another computer on the network with extra space I would use Partimage or dd to try and image the thing to external storage so that you still have your data.

[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

or maybe use a live cd to simply copy as much data off as you can.

---

### Post by albinootje on 2008-12-20
> **jazott3 said:**
> THANK YOU!!!
I hope it's B, although I have my doubts cause it's a laptop... I think my hard drive's dying because I've accidentally dropped my machine a couple of times lately, the pci.sys wasn't missing till i had a BSOD at the welcome screen, and my machine's 2 years old and been through multiple reformats (i do a lot of reinstalling xp every 3 months or so, and ubuntu too, i dunno why)


What can I do to see if it IS dying?

In Ubuntu do this in a terminal :
```

sudo apt-get install smartmontools

```
After that run this, assuming that your hard disk "is" /dev/sda :
```

sudo smartctl -s on --test=long -d ata /dev/sda

```

---

### Post by albinootje on 2008-12-20
You can also try the GUI for smartmontools :
[http://gsmartcontrol.berlios.de/home/index.php/en/Downloads](http://gsmartcontrol.berlios.de/home/index.php/en/Downloads)
by installing the Debian package.

---

### Post by jazott3 on 2008-12-21
Thanks a bunch, but smartmontools doesn't work.... here's what i've got:


```
joe@JoesMachine:~$ sudo apt-get install smartmontools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package smartmontools is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package smartmontools has no installation candidate
joe@JoesMachine:~$ 

```


I've had problems with manypackages before, for example Wine won't install and neither will apache. My firefox problem was all fixed when I restarted, and all of the windows did their normal thing instead of wiping out all but one panel and not showing up in the window list. Haven't yet tried booting to windows but it's probably not any better. when i issue the [ls] command in /media/sda2/WINDOWS/system32 I hear my hdd spinning as if there was sand on the surface of the disks, just sort of grindy... again, my error with windows was in \WINDOWS\system32\drivers\pci.sys, and if I try to issue [ls] inside the /media/sda2/WINDOWS/system32/drivers directory I get this message:

```
joe@JoesMachine:/media/sda2/WINDOWS/system32/drivers$ ls
ls: reading directory .: Input/output error
joe@JoesMachine:/media/sda2/WINDOWS/system32/drivers$ 

```

...
I think windows is still fried and I'll have to do startup repair.

---

### Post by albinootje on 2008-12-21
> **jazott3 said:**
> Thanks a bunch, but smartmontools doesn't work.... here's what i've got:
```
joe@JoesMachine:~$ sudo apt-get install smartmontools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package smartmontools is not available, but is referred to by another package.

```


I think you should *first* concentrate on finding out whether your disk is broken. And only then (after finding out the disk is fine) fix your (possible) file-system or installation problems.

And smartmontools should be available :
[http://packages.ubuntu.com/search?keywords=smartmontools](http://packages.ubuntu.com/search?keywords=smartmontools)
Can you post the output of :
```

cat /etc/apt/sources.list

```
There are also live cd which have smartmontools installed :
[http://smartmontools.sourceforge.net/faq.html](http://smartmontools.sourceforge.net/faq.html)
This is one which is not so much (filesize) to download :
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

But you can also use the Ubuntu desktop installation cdrom,
and install smartmontools (in RAM).

---

