---
title: "how to rsync with the mirrors?"
date: 2007-04-20
forum: Development CD/DVD Image Testing
---

### Post by ShirishAg75 on 2007-04-20
Hi guys,
     How do I rsync with the mirors now?

 rsync -zhhP rsync://cdimage.ubuntu.com/cdimage/daily-live/current/feisty-desktop-i386.iso 

this was my world, now the world has changed to 

[http://ftp.tcc.edu.tw/iso/Ubuntu/7.04/ubuntu-7.04-desktop-i386.iso]("http://ftp.tcc.edu.tw/iso/Ubuntu/7.04/ubuntu-7.04-alternate-i386.iso")

now how can I  use rsync to  update to this final build. There might be not many changes but still. Thanx in advance.

---

### Post by leibowitz on 2007-04-20
Are you sure you want to switch from the desktop image to the alternate one ?

It's not the same at all. You will be downloading a lot of changes, yes. I don't know exactly how rsync do his job. Maybe that's reasonable but it seems pointless to me.

You may try to rsync from scratch. And I don't really understand your question. Anyway, rsync is a special protocol and it have to be handled on the server. I don't know this one (tcc.edu.tw) but I can't find any rsync adress.

If you find one or know the exact URL, then you can use rsync with something like:
```
rsync rsync://adress.com/path/to/cdimage/
```

Do not put any file name, so you get a listing of the available file.

Then just use something like what you were using at first
```
rsync -avzP rsync://adress.com/path/to/cdimage/image.iso 
```

EDIT: I think I get it, you want to rsync a FTP/HTTP mirror but AFAIK it's just not possible.

---

### Post by ShirishAg75 on 2007-04-21
right, that was the idea

---

### Post by forger on 2007-06-27
I play today with it. Read the "man rsync"? :) pretty useful. Google search too!

Well, here you have a list of rsync mirrors: [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)
Get the domain's name, i.e. if the link in the mirror list is **rsync://mirror.etf.bg.ac.yu/ubuntu-archive/** you get **mirror.etf.bg.ac.yu** for the rsync to work.

And the way to do it is:
1) use mv to rename your file to match the **exact** name of the remote file.

2) to browse rsync modules you use (to get the module name):
```
rsync mirror.etf.bg.ac.yu::
```
part of the reply:
> 
gentoo-x86-portage      Gentoo Linux Portage tree
gentoo-portage  Gentoo Linux Portage tree mirror
gentoo-packages Gentoo Linux Packages Mirror
distributions   Linux distributions
full            Everything (~1TB)
kernel          Kernel
software        Linux software
**[COLOR="Red"]ubuntu[/COLOR]          Ubuntu archive**
**[COLOR="Green"]releases[/COLOR]        Ubuntu releases**
backup          backup


3)then you browse into its "directories" or whatever they're called (don't forget the trailing **slash /** at the end):
```
rsync mirror.etf.bg.ac.yu::releases/
```
notice the fancy directory-like names. continue to your liking:
```
rsync mirror.etf.bg.ac.yu::releases/feisty/
rsync mirror.etf.bg.ac.yu::releases/feisty/ubuntu-7.04-desktop-i386.iso ./ubuntu-7.04-desktop-i386.iso
```

No idea how to update/continue a file though

edit: you can also use CC.cdimage.ubuntu.com, where CC is your country code or just cdimage.ubuntu.com:
```
rsync cdimage.ubuntu.com::cdimage/releases/feisty/release/
```

the problem is that there you only have dvd versions :(

---

### Post by ShirishAg75 on 2007-08-22
Hi forger, 
           That was quite cool. I tried doing the same here with pretty good results. :-

```
rsync ftp.iitm.ac.in::
```output

```

wholetree       entire site (as seen by external users)
internaltree    entire site as seen by local users
debian          the iitm debian mirror site
centos          the iitm centos mirror site
ubuntu          the iitm ubuntu mirror site

```the only sad part it doesn't give as much details as the European mirror which was cool. 

browsing directories 

```
rsync ftp.iitm.ac.in::ubuntu/ 
```output 

```

drwxr-xr-x        4096 2007/08/22 01:38:40 .
-rw-rw-r--          29 2007/08/22 01:38:40 last-updated-on
-rw-r--r--     4952642 2007/08/22 00:08:55 ls-lR.gz
drwxrwsr-x        4096 2007/04/20 18:22:46 dists
drwxrwsr-x       24576 2007/08/22 00:05:54 indices
drwxrwsr-x        4096 2007/06/21 09:33:40 pool
drwxrwsr-x        4096 2004/06/15 19:51:17 project

```Going further 

```
rsync ftp.iitm.ac.in::ubuntu/dists/
```output 

```

drwxrwsr-x        4096 2007/04/20 18:22:46 .
drwxr-sr-x        4096 2006/08/08 18:11:26 dapper-backports
drwxr-sr-x        4096 2006/08/08 18:11:26 dapper-proposed
drwxr-sr-x        4096 2006/08/08 18:11:26 dapper-security
drwxr-sr-x        4096 2006/08/08 18:11:23 dapper-updates
drwxr-sr-x        4096 2006/08/08 18:11:18 dapper
drwxr-sr-x        4096 2006/08/08 18:11:17 edgy-backports
drwxr-sr-x        4096 2006/08/08 18:11:17 edgy-proposed
drwxr-sr-x        4096 2006/08/08 18:11:17 edgy-security
drwxr-sr-x        4096 2006/08/08 18:11:17 edgy-updates
drwxr-sr-x        4096 2006/10/25 21:22:55 edgy
drwxr-sr-x        4096 2006/11/01 18:54:13 feisty-backports
drwxr-sr-x        4096 2006/11/01 18:54:13 feisty-proposed
drwxr-sr-x        4096 2006/11/01 18:54:13 feisty-security
drwxr-sr-x        4096 2006/11/01 18:54:13 feisty-updates
drwxr-sr-x        4096 2006/11/27 18:05:24 feisty
drwxr-sr-x        4096 2007/04/20 18:55:58 gutsy-backports
drwxr-sr-x        4096 2007/04/20 18:55:59 gutsy-proposed
drwxr-sr-x        4096 2007/04/20 18:55:59 gutsy-security
drwxr-sr-x        4096 2007/04/20 18:55:59 gutsy-updates
drwxr-sr-x        4096 2007/05/06 09:31:38 gutsy

```Although I don't have an .iso yet but its still cool. ;)

---

### Post by forger on 2007-09-15
you just go one step more...
rsync ftp.iitm.ac.in::ubuntu/feisty/

you should also try something like:
```
rsync releases.ubuntu.com::releases/feisty/
```

---

### Post by chikaku on 2009-11-17
can i restrict rsync only the arch that i use
n also can i choose the binary one not the source?

thankyou in advance bro

---

