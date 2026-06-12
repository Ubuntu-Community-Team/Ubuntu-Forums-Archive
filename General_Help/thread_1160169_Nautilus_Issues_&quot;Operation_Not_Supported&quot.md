---
title: "Nautilus Issues &quot;Operation Not Supported&quot;"
date: 2009-05-15
forum: General Help
---

### Post by coldReactive on 2009-05-15
Here's what terminal says:

```
** (nautilus:6240): WARNING **: Unable to add monitor: Operation not supported

--- Hash table keys for warning below:
--> file:///
--> file:///var
--> file:///var/log
--> file:///var/log/bootchart
--> file:///root

(nautilus:6240): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 5 elements at quit time (keys above)

(nautilus:6240): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 5 elements at quit time
```

---

### Post by kanikilu on 2009-05-15
I'm not sure about the other warnings below that, but it seems the "unable to add monitor" is not something to worry about:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/223782](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/223782)

---

### Post by coldReactive on 2009-05-15
> **kanikilu said:**
> I'm not sure about the other warnings below that, but it seems the "unable to add monitor" is not something to worry about:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/223782](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/223782)

Why would it be warning me about [GVFS]("http://en.wikipedia.org/wiki/GVFS")? I use ext3 on my filesystem.

---

### Post by kanikilu on 2009-05-15
I'm no expert, but a virtual filesystem is different than the filesystem of your physical media (ext3, NTFS, etc.).

I think GVFS has been in Gnome for a while now, but you can see if you're using it with: ```
ps -ef | grep gvfs
```

---

### Post by coldReactive on 2009-05-15
Apparently I am:
```
ian       3645     1  0 08:51 ?        00:00:00 /usr/lib/gvfs/gvfsd
ian       3651     1  0 08:51 ?        00:00:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/ian/.gvfs
ian       3684     1  0 08:51 ?        00:00:00 /usr/lib/gvfs/gvfs-hal-volume-monitor
ian       3687     1  0 08:51 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
ian       3692     1  0 08:51 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
ian       3743     1  0 08:52 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.4 /org/gtk/gvfs/exec_spaw/1
ian       5698     1  0 09:48 ?        00:00:00 /usr/lib/gvfs/gvfsd-computer --spawner :1.4 /org/gtk/gvfs/exec_spaw/2
ian       7260  7242  0 10:20 pts/0    00:00:00 grep gvfs
```

---

