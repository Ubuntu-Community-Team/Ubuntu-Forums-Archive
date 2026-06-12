---
title: "backup from one system and restore to another"
date: 2009-05-27
forum: General Help
---

### Post by knottshawk on 2009-05-27
I want to move my junk from one ubuntu 8.04 install to another. I thought I could use sbackup but when I try to restore on the new system it just sits there saying "restoring" with nothing happening. I watch for changes, new files, etc and after 30 minutes there is nothing. So... what's an alternative way to do this?

---

### Post by lindsay7 on 2009-05-27
If you do not have it download Remastersys for synaptic. It will show up under system/ administration. Just run this and it will make an ISO file you can burn to a cd and then use to restore any computer to that burned system image. The only thing that is a slight problem is that Remastersys will only do about 4 gigs so if you home director is large then to use Remastersys you would need to move all the info in you home directory out of it and do the Remastersys. once you set up the new computer with the Remastersys cd then you can copy back everything that was in the other home directory.

---

### Post by piratebill on 2009-05-27
if you have a spare hard driv cp works great.

```
cp -Ruv /home/username /media/hard_drive
```


the R is recursive, the u is incremental update, the v is for verbose.

---

### Post by lindsay7 on 2009-05-27
To, piratebill,

Interesting, can you tell me what the differences are between, Recursive, verbose, and incremental are. How does that change this type of backup?

---

### Post by dstempfley on 2009-05-27
Recursive: will traverse the directory structure. 

Incremental/update: will only overwrite files when the source file is newer then the destination file.  Be aware that if you've booted the new system and logged in, then you may not get all the configuration options from your old system.  In that case you may want to drop the -u flag.

Verbose: just tell you what it's doing as it does it.

I have always been partial to using tar or cpio, in part because they give more options for moving the stuff across systems/directories. 

For example a simple tar could look like:

    cd /origdir
    tar cf - . | (cd /destdir; tar xvBpf - )

You could also just dump archive to a tarfile and extract it later:

    On orig system:
    cd /origdir
    tar zcf /media/device/outfile.tgz .
    
    On dest system:
    cd /destdir
    tar zxfp /media/device/outfile.tgz

If the two systems are networked and you can ssh between them:

     cd /origdir; tar cf - . | ssh -C remote_system "cd /destdir; tar xvBpf - "


And since I mentioned cpio:

    cd /origdir
    find . -print | cpio -dumpv /destdir

Hope it helps.

/Dion

---

### Post by lindsay7 on 2009-05-27
Thanks a lot. My education continues!

---

