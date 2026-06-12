---
title: "Server to Server Synchronization"
date: 2009-02-18
forum: General Help
---

### Post by thegodfaza on 2009-02-18
I am looking for a command line tool that will let me sync files between hard drives and servers. The tool has to be able to tell if the files have changed since the last sync to avoid unnecessary syncing. I would like the tool to sync between two different hard drives within an Ubuntu 8.10 Server and also between the server and a Windows Home Server over smbfs(doesn't have to support it since I could just mount the shares). Microsoft's sync toy would do the job perfectly but I would like a tool that runs on the Linux box and sync toy leaves some not so hidden files that look quite messy on a unix file system.

---

### Post by heindsight on 2009-02-18
it's called rsync. 
have a look at the manual with
```
man rsync
```
or
[http://manpages.ubuntu.com/manpages/intrepid/en/man1/rsync.1.html](http://manpages.ubuntu.com/manpages/intrepid/en/man1/rsync.1.html)

---

### Post by tmcmulli on 2009-02-18
Does rsync keep two directory the same?  I've used it for a while and found that it will over write newer files on the receiving side unless I use the right directive.

Like the original poster, I'd like a way to keep BOTH directories in sync, not just a backup, or mirror of one or the other.

I've been using rsync -avuz source dest, which I then repeat switching the source and dest dirs... would love to know if there's a better way.

---

### Post by crokett on 2009-02-18
I sync w/rysnc between a Windows XP machine and a Linux machine. I haven't found a better way. Rsync is fast, it tracks changes and I can tunnel it over ssh.   There is a GUI front end to rsync in Windows called DeltaCopy, but I honestly prefer the command line.  It is much more descriptive when something breaks.    

You can script or schedule the sync.  I wrote a very basic perl script to run mine. If you sync between a Windows and Linux machine, run the DeltaCopy server on Windows and run the rsync command on your Linux box.  I found out the hard way that if you sync from Windows it seriously screws up your permissions on both ends.  You lose all rights to files on both OSes.

---

### Post by heindsight on 2009-02-19
> **tmcmulli said:**
> Does rsync keep two directory the same?  I've used it for a while and found that it will over write newer files on the receiving side unless I use the right directive.

Like the original poster, I'd like a way to keep BOTH directories in sync, not just a backup, or mirror of one or the other.

I've been using rsync -avuz source dest, which I then repeat switching the source and dest dirs... would love to know if there's a better way.

Say A and B are the dirs you want to sync. As I understand, what you want is to sync from A to B but not overwrite files that are newer on B than on A, and simultaneously sync from B to A but not overwrite file that are newer on A than B.

rsync doesn't quite do simultaneous syncing in both directions, but you can achieve the same effect by first syncing A->B (but skip files newer on B) then sync B->A(skipping files newer on A, though there shouldn't be any).

You can do this quite easily as follows:
```
rsync -auv A/ B/
rsync -auv B/ A/
```

---

