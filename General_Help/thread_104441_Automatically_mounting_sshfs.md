---
title: "Automatically mounting sshfs"
date: 2005-12-16
forum: General Help
---

### Post by Falc on 2005-12-16
I've looked all over the net but I can't seem to get a decent answer as to how I can automatically mount a folder from my Ubuntu server on this Ubuntu laptop.

By 'automatically' I mean as if it were listed in fstab with the 'auto' option. Right now I do have this
```
sshfs#falc@server:/home/falc        /home/falc/server        fuse        defaults        0        0
```
in my fstab, but that ain't working, during boot I get 'Mounting local filesystems: failed'.

The fuse mod is in /etc/modules, it loads fine because I have no problems doing ```
sshfs server: server
``` from a terminal afterwards.

So, does anyone have any working experience with sshfs in the fstab?

---

### Post by kosmic on 2005-12-16
have a look at this -> [http://ubuntuguide.org/#automountnetworkfolders]("http://ubuntuguide.org/#automountnetworkfolders") it should help you out

---

### Post by Falc on 2005-12-16
No, sorry, that's for Samba.

See here [http://ubuntuforums.org/showthread.php?t=102893]("http://ubuntuforums.org/showthread.php?t=102893") for the reason why I'm looking for an alternative to Samba.

I really like the concept of sshfs, now I'd just like it to mount the directory automatically...

---

### Post by schilcha on 2005-12-16
Here comes a really vague guess -- I've just learned from this thread that sshfs exists (the concept is appealing indeed!): I suggest to look at the script /etc/init.d/mountnfs.sh. It is obviously responsible from mounting networked filesystems. It seems that nfs, smbfs, cifs, coda, ncp, ncpfs, ocfs2 and gfs mounts are taken care of. 
I don't know how you installed sshfs, but you should check, if there is a similar mount-script included. If so, just add it to your runlevel-specs. If not try to add it to  mountnfs.sh or write your on script.

---

### Post by schdefan on 2006-02-13
Maybe the order is wrong. You have to make sure that first the module fuse is loaded and then the filesystem is mounted.
I am very interested in this topic too. Did make any steps forward?

schdefan

---

### Post by chantra on 2006-04-27
Falc, you might want to give a look at my how to [fuse,sshfs and fstab]("http://www.debuntu.org/2006/04/27/39-mounting-a-fuse-filesystem-from-etc-fstab").

The .deb package is compiled for dapper, hopefully it works the same with breezy.

---

