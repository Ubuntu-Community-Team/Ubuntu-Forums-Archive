---
title: "Full Read/Write NTFS in linux"
date: 2006-01-05
forum: Desktop Environments
---

### Post by cs378 on 2006-01-05
I am new to linux

I just did a search in this forum, and all i can see it that we can only mount the NTFS drive to read only.

So I did a google search on that topic and gave me the first link to

[http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/)

according to that site, by installing there application, it will enable full read/write NTFS drive

again I am new, I don't want to mess up again and have to reinstall Ubuntu :)

but, for fun i will install it anyway lol

---

### Post by audax321 on 2006-01-05
Just as a warning though, writing to NTFS is highly experimental and there is a real possibility of losing data on your NTFS partition or even corruption of the partition itself.... I've never done it and probably won't until it is officially confirmed to work without issues.

---

### Post by cs378 on 2006-01-05
thx for the warning

I am trying to install it, but gettin error

have mounted using captive but can write bcuz of the error

hmmm

don't know what to do, i guess ill wait till someone smart here can figure/or take the risk to try it

thx

---

### Post by HermanAB on 2006-01-06
You may be able to get limited write capability by simply changing the mount command from ro to rw.

The limitation is that you can write to existing files, but you cannot create new files.  You may be able to live with this limitation, by creating a pool of files with WinXP and renaming them as required from Linux.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

