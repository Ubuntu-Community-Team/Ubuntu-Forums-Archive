---
title: "Mini 9 claims disk full after update"
date: 2009-05-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by epb223 on 2009-05-08
I ran the update manager earlier tonight on my Mini 9, Ubuntu 8.04, and after the restart required by the update, the Mini 9 is claiming that the disk is 100% full and therefore it can't run any applications, etc. Needless to say, the hard drive is nowhere near full, I've only had the computer for a month and haven't added a thing it didn't come with out of the box.

Anybody have any idea what's the problem here, and what I can do?

Thanks,
Edward

---

### Post by Triptol on 2009-05-08
I don't know about the size and the partitions on your disc, but I guess your root partition is full.

You could check that by entering the following on a command line:
```
df -h
```
This will output something like the lines below:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             8.3G  6.9G  1.1G  88% /
```
If your output says 100% somewhere, it means that partition is full (above you'll see my statistics for my root '/' partition).

If root is full and it happened after an update you probably have a couple of old packages laying around. You could remove them by entering the following commands:
```
cd /var/cache/apt/archives/
sudo rm *deb
```
This will remove your downloaded packages, without touching the installed packages, so no worries. Those packages are only kept on your disc in case you want to reinstall them.

If this doesn't help, then you need to check what else is on the disc.

---

### Post by shiningkenmonster on 2009-05-08
I am assuming you are using a 4GB SSD. Running on Dell's factory pre-installed of Ubuntu 8.04 with the LPIA (Low Power Intel Architecture) 

Type in the terminal:

```
sudo apt-get autoremove
```

Say "Y" for yes to remove broken packages.

and do a

```
sudo apt-get clean
```

it will remove old cache of your updates that you have already installed.
When I did this command, it free me with 300 MB more space. (when i had dell's ubuntu 8.04.1 on the dell mini 9) - Dell always does a poor job with the Dell mini 9 Ubuntu updates.

You could switch to installing the Ubuntu 9.04 netbook remix, if you want too. I am using it, I think it is great. :)

I hope this helps

---

### Post by drs305 on 2009-05-08
I just posted an ubuntu documentation wiki this week on finding 'lost' disk space. Here is the link. 

[RecoverLostDiskSpace]("https://help.ubuntu.com/community/RecoverLostDiskSpace")

---

### Post by epb223 on 2009-05-09
> **Triptol said:**
> 

If root is full and it happened after an update you probably have a couple of old packages laying around. You could remove them by entering the following commands:
```
cd /var/cache/apt/archives/
sudo rm *deb
```
This will remove your downloaded packages, without touching the installed packages

When I did this, it said that there was no file '*deb'. 

The suggestions I got from the other responders enabled me to recover just enough space, apparently, to get my applications to run again. I am trying to figure out how to get a little more headroom, though. Obviously, 4GB isn't much; but I had no idea that I would be having these problems literally without having put a single application or document of any kind on the computer.

Edward

---

### Post by epb223 on 2009-05-09
> **shiningkenmonster said:**
> I am assuming you are using a 4GB SSD. Running on Dell's factory pre-installed of Ubuntu 8.04 with the LPIA (Low Power Intel Architecture) 

Type in the terminal:

```
sudo apt-get autoremove
```

Say "Y" for yes to remove broken packages.

and do a

```
sudo apt-get clean
```

it will remove old cache of your updates that you have already installed.
When I did this command, it free me with 300 MB more space. (when i had dell's ubuntu 8.04.1 on the dell mini 9) - Dell always does a poor job with the Dell mini 9 Ubuntu updates.

You could switch to installing the Ubuntu 9.04 netbook remix, if you want too. I am using it, I think it is great. :)

I hope this helps

This did help, thank you. It won me back enough space to get my applications running again. I am looking into getting the 9.04 netbook remix. Will it give me some more headroom? Also, I'm thinking about getting the RAM upgrade; would it be better to do that before, or after installing 9.04?

Thanks again,
Edward

---

### Post by epb223 on 2009-05-09
> **drs305 said:**
> I just posted an ubuntu documentation wiki this week on finding 'lost' disk space. Here is the link. 

[RecoverLostDiskSpace]("https://help.ubuntu.com/community/RecoverLostDiskSpace")

Thanks for the link. Some of it was a little complicated for me, as I'm awfully new to this. As you can see from other replies, I managed to get just enough space back to get my applications back up, but I'm going to have to get a lot better at this sort of housekeeping if I'm going to keep my head above water with this system.

Edward

---

### Post by drs305 on 2009-05-09
Edward,

I would like to make that wiki page as easy to use as possible. 

For the command line instructions, some of them are a bit long but "copy/paste" is the way to use any CLI instructions - fewer mistakes that way. 

If you have questions about any of it please send me a PM and I would be happy to answer them. I could then try to expand the explanations to make them easier for others to use.

dave
drs305

Added: [COLOR="DarkRed"]ugm6hr[/COLOR] thanks for sharing that tip. I've put it on the wiki page. Since wiki inputs are open to everyone's ideas and have no attribution, I'll give you credit here.

---

### Post by ugm6hr on 2009-05-09
4GB is not really enough to be able to run Ubuntu satisfactorily.

Thankfully, the minimum spec in UK is 8GB (which I have).

The introduction of multiple updates at one time will always cause problems for you.

If there are multiple updates, download them first from Terminal:
```
sudo apt-get upgrade -d
```

This will download updates to /var/cache/apt/archives without trying to install them.

Then copy them to a USB stick (or SD card) manually (using the Nautilus File Explorer).

Then delete them from the internal HD to free space to install:
```
sudo apt-get clean
```

Then install updates from USB stick (assuming USB is /media/disk)
```
sudo dpkg -i /media/disk/*.deb
```

I currently have Symlinks to my SD card for all files within my Home directory (hence everything is saved on my SD card instead of the internal SD).

---

### Post by epb223 on 2009-05-09
> **ugm6hr said:**
> 
If there are multiple updates, download them first from Terminal:
```
sudo apt-get upgrade -d
```

This will download updates to /var/cache/apt/archives without trying to install them.

Then copy them to a USB stick (or SD card) manually (using the Nautilus File Explorer).

Then delete them from the internal HD to free space to install:
```
sudo apt-get clean
```

Then install updates from USB stick (assuming USB is /media/disk)
```
sudo dpkg -i /media/disk/*.deb
```

I currently have Symlinks to my SD card for all files within my Home directory (hence everything is saved on my SD card instead of the internal SD).

Thanks for sharing this strategy with me; I'm saving it to use the next time I get any kind of update.

Edward

---

