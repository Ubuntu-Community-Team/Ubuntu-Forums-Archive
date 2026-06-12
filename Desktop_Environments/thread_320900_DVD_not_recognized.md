---
title: "DVD not recognized"
date: 2006-12-18
forum: Desktop Environments
---

### Post by fdimmling on 2006-12-18
I cannot open the recently available (German) Wikipedia DVD on three different computers, 2 running Dapper, one Breezy. Error message: Unknown file system oder bad superblock. On a Windows XP computer the DVD opens without problems. The people from Wikimedia told me that it was tested with SuSE 10.1 and another Linux brand I dont remember. The filesystem is standard ISO.

Any idea what's wrong and how to fix it? 

Friedrich](*,)

---

### Post by gunthr on 2006-12-18
You may just be missing the dvd codecs.

sudo apt-get install libdvdcss2

I quess these are illegal in the United States, so you may want to look into it.

Here's a link for installing Automatix2, which displays a warning regarding this on startup.

[http://www.debianadmin.com/install-automatix2-in-ubuntukubuntuxubuntu.html](http://www.debianadmin.com/install-automatix2-in-ubuntukubuntuxubuntu.html)

You may need to add repositories to your sources.list. Take a look at this link.

[http://www.ubuntugeek.com/install-and-enable-dvd-playback-and-w32codecs-in-ubuntu-system.html](http://www.ubuntugeek.com/install-and-enable-dvd-playback-and-w32codecs-in-ubuntu-system.html)

---

### Post by fdimmling on 2006-12-18
> **gunthr said:**
> You may just be missing the dvd codecs.


It's a data DVD not a movie. No encryption at all. It is just an offline version of the wikipedia encyclopedia. I never had any problem with any other DVD - data or movie - before.

Friedrich

---

### Post by _Martin_ on 2006-12-19
I bought the Wikipedia DVD yesterday and experienced the same problem.

My quick solution was to copy the Zeno-files and the ZenoReader via Network from a Windows-PC to my Ubuntu-machine. I think, it should be possible to burn a new DVD with these files that is recognized by Ubuntu.

---

### Post by fdimmling on 2006-12-19
> **_Martin_ said:**
> I bought the Wikipedia DVD yesterday and experienced the same problem.

My quick solution was to copy the Zeno-files and the ZenoReader via Network from a Windows-PC to my Ubuntu-machine. I think, it should be possible to burn a new DVD with these files that is recognized by Ubuntu.

Hi Martin,

I have already downloaded the data and installed it on my computer. I just would like to know how this can happen, because I never had any problem with DVDs before.

Friedrich

---

