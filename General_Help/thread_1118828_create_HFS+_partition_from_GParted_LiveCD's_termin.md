---
title: "create HFS+ partition from GParted LiveCD's terminal"
date: 2009-04-07
forum: General Help
---

### Post by afrodeity on 2009-04-07
I am trying to create an HFS+ partition, but none of the online links are up. Anyone know how to create HFS+ partition from GParted LiveCD's terminal? 

The Gparted in the repositories for Ubuntu Hardy have HFS+ greyed out. This might be something to do with a legal issue because HFS+ is an Apple file system. However, many Macusers duel boot with Ubuntu, so there is no intrinsic reason not to allow this kind of support. 

Anybody with a work around?

---

### Post by kanikilu on 2009-04-07
If you're just trying to create a partition, it should work. It looks like the only thing you can't do with HSF+ in gparted is "grow":

[http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php)

If you want to do it from the command line, you'll probably at least need the hfsprogs package...

---

### Post by afrodeity on 2009-04-08
I found this on the [gparted forum]("http://gparted-forum.surf4.info/")

> the link you gave does say hfs+ is supported, after installing hfsprogs.
i did so, now i can detect, read, shrink, move and copy hfs+, but not create, grow, check and read label!

but somewhere i red hfsprogs is actually the commands mkfs and fsck for hfs and hfs+ filesystems.
so i tried this:

mkfs.hfsplus /dev/hdb1(or whatever your hd is)

and it worked!!!
so, install hsfprogs and format with the terminal.
i guess gparted just does not detect hfsprogs properly.


HFSsprogs is installed. I can created HFS+ in terminal, but it greyed out in Gparted. Need to use Gparted, because the label is now "untitled" and am having trouble copyying stuff over to the partition.

---

### Post by Beef Eater on 2013-01-20
> **afrodeity said:**
> I found this on the [gparted forum]("http://gparted-forum.surf4.info/")

HFSsprogs is installed. I can created HFS+ in terminal, but it greyed out in Gparted. Need to use Gparted, because the label is now "untitled" and am having trouble copyying stuff over to the partition.

hfs+ partition label can be set while making the partition in terminal:

```
sudo mkfs.hfsplus -v LABEL /dev/sdaN
```

---

### Post by oldos2er on 2013-01-20
Closed, please don't bump old threads.

---

