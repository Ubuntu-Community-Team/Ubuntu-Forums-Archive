---
title: "Using Rsync to mirror a live, remote server"
date: 2006-06-15
forum: Desktop Environments
---

### Post by Amon_Re on 2006-06-15
Does anyone know if it's possible to use rsync to mirror a remote server to a dedicated hard drive in another machine preserving the whole system?

Basicly, my goal is to have my desktop at home connect to the remote server and to maintain a local mirror of the server's hard drive, so that, incase a hard disk failure occurs, i can just toss grub onto the new drive in my system & screw it into the server.

I assume that copying things like open mysql dbases could be troublesome, so an alternative to that will also be needed.

Any pointers, howto's or alternatives are welcome :cool:

---

### Post by MJN on 2006-06-15
Sure - like many that's exactly what I do (but the other way round if you see what I mean). It works very very well - encrypted transfer, only transfers those *parts* of files that have changed, good logging, straightforward (yet powerful) command syntax etc etc
 
Best place to start is [http://samba.org/rsync/]("http://samba.org/rsync/") (of course) - it's surprisingly simple when you start learning about how to use it.
 
My setup is pretty much the standard - rsync available at both ends, SSH tunnel in between and something along the lines of
 
**rsync -av --exclude=/various/directories/I/don't/want/like/proc / remoteuser(likely-root)@remote.server.name::/location/on/remote/server**
 
running periodically. Yours would be the other way round (i.e. [email]remoteuser@remote.server.name[/email]::/ /local/backup/directory/)
 
As I said, give the rsync site (including the man pages) a good read and then you can post back with more specific queries.
 
Mathew

---

### Post by asmanian on 2008-06-23
I'm currently thinking about this, too. But I have serious fear that rsync may copy a somehow corrupt state of the FS.
(Ie the files might change during transfer/comparsion/whatever).

Note that I'm thinking about mirroring a system whose home-directories are exported via NFS to lots of machines, so theres nearly always write access going one.

Does anybody know how risky it really is to use rsync in such a situation? 
Did rsync developers think of it and made rsync somehow clever with respect to this?
Is there any (free) tool you know that is specifically designed to mirror running systems?

TIA,
Henning

---

### Post by MJN on 2008-06-23
Rsync will happilly cope in such situations. By default, it is very mindful of the fact that source files can change mid-transfer (or even pre-transfer but post-analysis) as well as being aware that destination files could be written to by other process at the same time. Hence, it accomodates this by writing destination files to a temporary file until its backup/restore is complete and then overwriting the 'old' file in one step (as opposed to modifying the old file in situ)[1]. To cope with source changes it also computes a post-transfer checksum on the source/destination and if different will either try again or give up (with that file).

The bottom line is that rsync is designed to work on a live system. Indeed its file-by-file methodology makes it ideally suited to working in this way (as opposed to, say, disk imaging backup tools).

Mathew

[1] See rsync's **--inplace** option modifier for details of the effects of not working in this way.

---

### Post by asmanian on 2008-06-23
Thanks for that fast and helpful answer :)

---

