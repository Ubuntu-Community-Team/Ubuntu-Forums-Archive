---
title: "fuse and &quot;Transport endpoint is not connected&quot;"
date: 2008-12-05
forum: General Help
---

### Post by Zorael on 2008-12-05
I have my local network mounted to a directory (/net) using fusesmb, but it's *VERY* fragile and buggy. If I try to copy a batch of files from a share to my local computer, it will copy the first few and then the mount will simply crash.

Excerpt:
```
cp: cannot stat `ship4reb.sgr': Transport endpoint is not connected
cp: cannot stat `shipani1.sgr': Transport endpoint is not connected
cp: cannot stat `shipani2.sgr': Transport endpoint is not connected
cp: cannot stat `shipani3.sgr': Transport endpoint is not connected
cp: cannot stat `shipani4.sgr': Transport endpoint is not connected
cp: cannot stat `shipdisp.sgr': Transport endpoint is not connected
```

If I mount in foreground/debug mode, it says the following in its dying breath:
```
LOOKUP /LAPPNET/SUNSPIRE/temp/Roketz/azrael1.pil
   NODEID: 13
   unique: 195, error: 0 (Success), outsize: 136
unique: 196, opcode: OPEN (14), nodeid: 13, insize: 48
   unique: 196, error: 0 (Success), outsize: 32
OPEN[138747992] flags: 0x28000 /LAPPNET/SUNSPIRE/temp/Roketz/azrael1.pil
unique: 197, opcode: READ (15), nodeid: 13, insize: 80
READ[138747992] 8192 bytes from 0
   READ[138747992] 4181 bytes
   unique: 197, error: 0 (Success), outsize: 4197
unique: 198, opcode: RELEASE (18), nodeid: 13, insize: 64
RELEASE[138747992] flags: 0x28000
unique: 199, opcode: LOOKUP (1), nodeid: 5, insize: 52
LOOKUP /LAPPNET/SUNSPIRE/temp/Roketz/azrael4.pil
   unique: 198, error: 0 (Success), outsize: 16
```
It stops there and returns terminal control to me. Trying to list the directory (/net/LAPPNET/SUNSPIRE/temp/Roketz), I get the same error message. I have to maneuver out of the directory tree and remount.
```
ls: cannot open directory .: Transport endpoint is not connected
```

I've had something similar happen with gvfs, but I can't reproduce that. THIS, on the other side, happens every time.


Any ideas?

---

### Post by Robsteranium on 2009-05-01
Zorael, did you ever solve this?  I'm stuck!

---

### Post by Zorael on 2009-05-01
I haven't really tried it since, gave up on it, will give it another go in the coming days.

---

### Post by Dr_Willis on 2009-05-05
fusesmb is sadly a bit.. err... less then reliable :(  

I was overjoyed when it started working for me properly on onemachine.. but now  on this other machine.. i cant get it to function at all. using exact same identical configs.

I have .smb/fusesmb.conf all set up same as the working box. But when i use the command

```
fusesmb -d /Network 

Error: /usr/bin/fusesmb.cache is already running
```


i get that message repeated over and over about every 20 sec.

I also notice that the .smb/fusesmb.cache file never gets created. It does get made on my working machine.

Also i Notice on the Working machine, the directory 'Network' is owned by my user. on the Non working machine. its owned by root after running the command.


Some other pasteing from the error log.

  unique: 14, error: 0 (Success), outsize: 112
unique: 15, opcode: READDIR (28), nodeid: 1, insize: 80
   unique: 15, error: -2 (No such file or directory), outsize: 16
unique: 16, opcode: RELEASEDIR (29), nodeid: 1, insize: 64
   unique: 16, error: 0 (Success), outsize: 16
Error: /usr/bin/fusesmb.cache is already running


I REALLY like how fusesmb works.. but sadly it just seems to be picky :(

If you need any more help in trouble shooting this let me know.
Im off to test it on some of my other ubuntu box's and see if i can find a pattern to the failures.

---

### Post by Zorael on 2009-05-06
I suggest you pop by launchpad and post a proper bug report; that way it'll (hopefully) get the attention of the maintaining developers.

---

### Post by Dr_Willis on 2009-05-12
Actually I have  posted bug reports on it. 
And theres also bug reports on  it by other people.  I still get an email about once a week on the bug reports.

I'm not sure what the actual problem is. but it seems rather hard to track down, other disrtos have also had similer issues.

---

### Post by albertomm on 2009-07-29
Try this:
```
fusesmb -s /path/to/mountpoint
```
it solved the problem for me (xubuntu jaunty)

It seems that some library on witch fusesmb depends isn't thread safe. The -s switch forces fusesmb to use only one thread.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=497572]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=497572")

---

### Post by Redsandro on 2009-08-21
> **albertomm said:**
> Try this:
```
fusesmb -s /path/to/mountpoint
```
it solved the problem for me (xubuntu jaunty)

It seems that some library on witch fusesmb depends isn't thread safe. The -s switch forces fusesmb to use only one thread.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=497572]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=497572")

**THIS WORKS!!** :P

Sorry about the caps, try to see them as joy.

A long while back (7.10), I couldn't get fusesmb to work, and I read [SIZE="1"](but couldn't find back)[/SIZE] about a used library that became buggy and has remained ever since. There was a how-to about how to reinstate an even older version of the library that shipped at the time, and fusesmb worked perfect.

Recently I tried to upgrade to 9.04, which failed, so now I have a partially upgraded 8.10, but apparently the (still) buggy library came back and I couldn't find that how-to anymore.

Now I tried the solution you mentioned, and it works so far! Wow this is even better than forcing installation of old components. :)

Thanks.

---

### Post by Difranco1911 on 2009-11-24
> **albertomm said:**
> Try this:
```
fusesmb -s /path/to/mountpoint
```
it solved the problem for me (xubuntu jaunty)

It seems that some library on witch fusesmb depends isn't thread safe. The -s switch forces fusesmb to use only one thread.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=497572]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=497572")

When I try this in terminal with sudo; I recieve an error message "Permission Denied"

---

### Post by albertomm on 2009-11-24
> **Difranco1911 said:**
> When I try this in terminal with sudo; I recieve an error message "Permission Denied"

Don't use sudo with fuse. Add your username to the group "fuse" and you will be able to use all the fuse mount programs like fusesmb, fuseiso and ntfs-3g.

---

### Post by fosheezy on 2009-12-03
I need some big help with this.

I just imported a zpool that was created in solaris. the import went fine. I got this transport endpoint error, rebooted.

now my zpool is nowhere to be found. it won't mount in solaris. i can see a mount point for it on ubuntu (/chuck) but nothing is in the folder.

I have tons of data on there. I'm going to lose a ton of work if I lose this.

I have no idea where to start.

---

