---
title: "need a little help with NFS"
date: 2005-12-16
forum: General Help
---

### Post by cooldudejz on 2005-12-16
ok everything is working except for when i try to mount it. i hvae been using this website for help [http://www.linux.org/docs/ldp/howto/NFS-HOWTO/client.html#REMOTEMOUNT](http://www.linux.org/docs/ldp/howto/NFS-HOWTO/client.html#REMOTEMOUNT).
this is the command i am using to try to mount it. sudo mount ip address /mnt -t nfs.
this does not work and i get this message <directory to mount not in host:dir format>
what am i doing wrong, any help

---

### Post by ape on 2005-12-16
When mounting NFS exports, the syntax should be like this:

 `mount -t nfs <host>:/<export> /<local mount point>`

Looks like you aren't giving it an export that you want to mount on the NFS host.

---

### Post by wylfing on 2005-12-16
You shouldn't have to use the "-t nfs" switch. The examples in the page linked to seem quite clear to me, but I'll try to be even clearer.

Suppose that on a computer named "borphee" you are sharing the folder "photos" using NFS. Then you want to connect to this shared folder from a different computer called "pheebor." Before issuing any mount commands, you have to decide where in the filesystem of "pheebor" you are going to mount this remote folder. A common technique is to use subfolders of /mnt. So, for example, on the computer named pheebor, you could create a folder called /mnt/remote_photos.

Then issue the command:
```
sudo mount borphee:/photos /mnt/remote_photos
```

This connects the folder "photos" on borphee to the folder "/mnt/remote_photos" on pheebor. If you're sitting at pheebor, you can simply browse into /mnt/remote_photos and it acts exactly like any other folder on your hard drive, except that its contents are actually on borphee.

Does that make things clear?

---

### Post by Daiver on 2006-06-19
[QUOTE=ape]When mounting NFS exports, the syntax should be like this:

 `mount -t nfs <host>:/<export> /<local mount point>`

Looks like you aren't giving it an export that you want to mount on the NFS host.[/QUOTE]

You helped me solve something that I have been avoiding forever.  Thanks :)

---

