---
title: "Removing an unremovable file?"
date: 2005-12-28
forum: General Help
---

### Post by shut on 2005-12-28
What to do when root rm -f doesn't work...

I have this file in the Trash, a large avi, which I would like to remove permanently.  Trash will not let me delete it, I can not delete it from the command line either.

I have tried chown-ing it to me and chmod-ing it to be completely removable but they also fail.  I've also rebooted into recovery mode and cannot remove the file.  When I do so I get this message :

```

$ sudo rm KMFAS\ CD1.avi
rm: remove write-protected weird file `KMFAS CD1.avi'? y
rm: cannot remove `KMFAS CD1.avi': Operation not permitted

```

```
$ sudo chown john KMFAS\ CD1.avi
chown: changing ownership of `KMFAS CD1.avi': Operation not permitted

```

```
$ sudo chmod 777 KMFAS\ CD1.avi
chmod: changing permissions of `KMFAS CD1.avi': Operation not permitted

```
What do I do to get rid of this?  Here are the permissions on the file :

```

?---------  17331 root 6387    0 1972-01-29 16:41 KMFAS CD1.avi
```

---

### Post by stuporglue on 2005-12-28
What does Linux think the file is? 

$ file filename

and what does ls say? 

$ ls -l filename

---

### Post by psusi on 2005-12-28
Wow.... that's... pretty jacked up.  You should fsck the volume, it looks like it may be damaged.

---

### Post by shut on 2005-12-28
[QUOTE=psusi]Wow.... that's... pretty jacked up.  You should fsck the volume, it looks like it may be damaged.[/QUOTE]

I just shutdown and I presume it is doing this to itself right now as a ton of stuff about inodes scroll up the screen.

---

### Post by psusi on 2005-12-28
Outch... what filesystem are you using?  ext3?  I wonder how it got hosed up?  Did you have a system crash or power failure?

---

### Post by shut on 2005-12-28
[QUOTE=psusi]Outch... what filesystem are you using?  ext3?  I wonder how it got hosed up?  Did you have a system crash or power failure?[/QUOTE]

No, actually, I just converted them over, it could be an issue with hdparm even though these are udma 6 drives.  

I can wait though, there wasn't much (if anything) on the drive the file was deleted from.

---

### Post by shut on 2005-12-28
How long does this typically take?

---

