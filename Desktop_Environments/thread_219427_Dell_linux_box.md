---
title: "Dell linux box"
date: 2006-07-20
forum: Desktop Environments
---

### Post by Unreallinux on 2006-07-20
Ok I want to get into linux but not spend an arm and a leg. I want to get a cheap pc to run ubuntu on but I don't want it to be unbearably slow. Yes I know that a $300 wont play doom 3, thats not what I'm looking for. I want a system that will just allow me to familierize myself with linux for a year or two and just do thing like browse internet,use openoffice, ect. 

What I'm thinking about doing is buying this dell computer and installing ubuntu on it. 
[http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=04&fb=1&kc=6W300&l=en&oc=dim11n&s=bsd](http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=04&fb=1&kc=6W300&l=en&oc=dim11n&s=bsd)

Basically I want this computer just to use for a little while to familiarize myself with linux and then maybe in the future I might use linux as the primary OS on my main pc. What I want to know is will that computer run ubuntu smoothely.(I would have at least 512mb ram probably 1gig)

My other option is to buy another hard drive and dual boot. The only problem with this is I don't know how to do it and I'm worried about loosing my data. Is this a hard thing to do?

---

### Post by Omnios on 2006-07-20
I started using Ubuntu about a year and a half ago and had an old hard drive when I upgraded to a 120gig drive. Anyways counting on how big of a hard drive you have a dual system would be a lot more affordable. RIght now I have my main hard drive partitioned into 3x 39 gig partitions and a seperate 40 gig drive with Ubuntu on it. I found my 40 gig drive more than anouph for Ubuntu and have one of my 39 gig drives as a vfat32 partition that acts as my windows My document drive and also as a Linux document drive which allows me to share my music etc with both os's. 

 Anyways you might want to research your hard drive needs and using partitions you might save a lot of money

---

### Post by jstueve on 2006-07-20
Probably work pretty good, Intel Graphic board is well supported, might even be able to run AIGLX on the system.  I've never run a Celeron processor, but I'm sure they are supported...

---

### Post by scxtt on 2006-07-20
[quote=Unreallinux]Basically I want this computer just to use for a little while to familiarize myself with linux and then maybe in the future I might use linux as the primary OS on my main pc.[/quote]if you already have a "good" PC, to me, it doesn't make any sense to spend $$$ on another box when EXCELLENT virtualizing software exists which you could install ubuntu on -- check out VMware.com to begin with ...

---

### Post by Unreallinux on 2006-07-20
My current HD on my main system is 80gb and I'm running out of room. I was going to buy a new HD soon anyway. How hard is it to partition a hard drive the way you did it?(I have never done it all before.) Does the ubuntu installer do this on its own?

---

### Post by Omnios on 2006-07-20
Partitioning the hard drive is rather simple but a lot of people have seemed to have a hard time partitioning the hard drive with the install cd on install. Think this has to be done with manual partitioning. Anyways the first thing you will want to do is defrag your hard drive even possibly a couple times to make partitioning easier and possibly avoid probmems that some have had withy fraged drives. Anyways I installed Ubuntu on a seperate 40 gig drive which was very easy. One note most people install Windows first then Ubuntu because the way grub sets up otherwise you may have to add windows to grub manualy.
 
 Here are a few links to oldr threads when I partitioned my harddrives.
[http://ubuntuforums.org/showthread.php?t=45605&highlight=partition](http://ubuntuforums.org/showthread.php?t=45605&highlight=partition)
[http://ubuntuforums.org/showthread.php?t=45868&highlight=partition](http://ubuntuforums.org/showthread.php?t=45868&highlight=partition)

 Anyways there are a few inportant things that I learnt by trial and error. First you will have to partition your Ubuntu drive with the installer , take your time and research this. Now once Ubuntu is installled you can use QTparted with the ntfs plug in to resize your partitions shrink windows etc. Now the thing I did differently was to use win xp disk manager to make the partitions to enshure windows compatability wich worked good for the My DOcuments/document drive. For the vfat my documents partition I used sudo mkfs.vfat -F 32 ....drive...mountpoint. Vfat kind of fakes permitions in Linux and found it worked very well. 

 Anyways I suggest you do a lot of reading on the forum about this as it may help eleviate a lot of possible problems

---

### Post by hotani on 2006-07-20
We use dells at work and I've installed Ubuntu on 5 Dell machines so far. On one of those, the windows install bit the Big One during partitioning, so it ended up being an "ubuntu-only" laptop. One of the others was a server (GX260), and the others have been set up successfully as dual boot machines. 

I have *never* had the graphical 'slider' partitioning method work. This is the point in the install process where you move a slider to determine what percentage of the hard drive you want to use for Ubuntu, and how much to leave alone for your existing Windows installation. Maybe I'm just not lucky. 

You can resize your windows partition and install Ubuntu on the extra space, but you could lose everything so keep that in mind. If you are doing this on a fresh system, as others have said, do windows first then Ubuntu. That way the install detects windows and sets up the boot menu correctly without you having to go in and edit some file.

My advice is to do this on a fresh hard drive, with a fresh install of windows. And don't get too attached to it either. Just install windows, then do Ubuntu. If all goes well, then go back and configure your windows installation the way you want it. 

BTW, I'm typing this on a Dell latitude D810. I've never had a problem with compatability on Dells, and everything has 'just worked' so far. On all but the server, I've successfully (well, that's debatable - but it is a shortcoming of Compiz, not the machine) run XGL or AIGLX and Compiz. Perhaps I'm just a big dummy, but I can never get it configured the way I like it and always end up using metacity anyway. I'd say "don't waste your time," but it wouldn't do any good so I won't.

Having installed XGL/AIGLX/Compiz on 4 machines, then eventually giving up and going back to metacity, I did it again today on this laptop. Guess I'll never learn. :)

---

### Post by adam.tropics on 2006-07-20
I can't see any problem with the spec, though a bit more memory might be nice. Contrary to some peoples' opinion, Celerons, whilst not the best, are just fine for Ubuntu..at least mine is! I think if you're looking to familiarise yourself, and can afford it, then the extra machine is a much better idea, as you can get more networking experience, which is always a good thing. Plus I guess it's a slightly safer environment while you're learning.

---

### Post by Blutack on 2006-07-20
Have you thought about installing ubuntu to an external hard disk?  My 1 year old dell can boot from a usb hard disk.  The setup should be the same, just pick sda1 instead of hda1.

---

### Post by Saibot on 2006-07-20
I vote for dual booting with a separate hard drive also.  I'm doing this with two of my computers and it works very well.  I have both systems set to boot from the Linux drive and that's where GRUB resides - that way you don't risk hosing your Windows install.  I also set a small FAT32 partition on the Linux drive just to use as an easy way to swap files from Ubuntu to Windows safely.

---

### Post by thomasr on 2006-07-20
Can you install a removable drive caddy in the box and just swap drives when tou want to boot to linux?.

something like this. [http://www.geeks.com/details.asp?invtid=GN210-BLK&cat=HDD](http://www.geeks.com/details.asp?invtid=GN210-BLK&cat=HDD)

Available lots of places.

---

### Post by indytim on 2006-07-20
Another approach (if you don't want to shell out the $300) might be to put it on an old P3.  That's how I started out just to get the feel of Ubuntu.  If you don't have one handy, probaby pretty easy to pick one up for a lot less than $300.  Recommendation if you go this approach... make sure you've got ethernet and a hd of at least 10-15g.  Also if the RAM is low, watch the iso you use to load Dapper.

IndyTim

---

### Post by scxtt on 2006-07-20
this is exactly what virtualization is good for, experimenting - yet somehow the idea of a throw-away 'it has to be just good enough' box is prevailing - seems like such a waste to me ... if you've got a main box that has decent specs (mainly ~1gb of RAM and a decent proc.) VMs will run fine - and it's just like having another box ...

save yourself some $$$ ...

---

### Post by az on 2006-07-20
> **Unreallinux said:**
> Ok I want to get into linux but not spend an arm and a leg. I want to get a cheap pc to run ubuntu on but I don't want it to be unbearably slow. Yes I know that a $300 wont play doom 3, thats not what I'm looking for. I want a system that will just allow me to familierize myself with linux for a year or two and just do thing like browse internet,use openoffice, ect. 

What I'm thinking about doing is buying this dell computer and installing ubuntu on it. 
[http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=04&fb=1&kc=6W300&l=en&oc=dim11n&s=bsd](http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=04&fb=1&kc=6W300&l=en&oc=dim11n&s=bsd)

Basically I want this computer just to use for a little while to familiarize myself with linux and then maybe in the future I might use linux as the primary OS on my main pc. What I want to know is will that computer run ubuntu smoothely.(I would have at least 512mb ram probably 1gig)

I beleive that everything works out-of-the-box for a Dell 1100.

> **Unreallinux said:**
> 

My other option is to buy another hard drive and dual boot. The only problem with this is I don't know how to do it and I'm worried about loosing my data. Is this a hard thing to do?

I would think that most people who still use windows dual boot.  It's very safe.  Back up your data, though, just because....

---

