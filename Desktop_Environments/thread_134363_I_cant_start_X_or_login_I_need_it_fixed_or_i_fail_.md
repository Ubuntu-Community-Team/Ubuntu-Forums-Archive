---
title: "I cant start X or login I need it fixed or i fail school!!!!"
date: 2006-02-21
forum: Desktop Environments
---

### Post by shade11 on 2006-02-21
I try to startup and it will fail on Random number generator, creating module dependencies, and it hangs on Starting system log daemon. Until it starts XDM with says that I can not login due to some internal error. I cannot boot into recovery mode and i cant boot into another alternative kernel. I do not have any time to re-install, I have to work on my research paper, and I cannot backup either.

I despratley need to get this working. I have all my data and work on my harddrive and I cant get to it. If i cant get this fixed I fail school because that paper is worth like 60% or so of my grade. I need help and fast. :cry:

---

### Post by SuperBOB on 2006-02-21
Boot live CD

Mount partition

Salvage data

Attempt to fix problem

Finish paper

Graduate

Profit

---

### Post by shade11 on 2006-02-21
I cant mount it I dont know how. It is /dev/sda2 and it is not working on the live CD.](*,) How can I get back into gdm? My friend Ben Plaut did it before but he left school before he could fix it again.

---

### Post by cwaldbieser on 2006-02-21
[QUOTE=shade11]I cant mount it I dont know how. It is /dev/sda2 and it is not working on the live CD.](*,) How can I get back into gdm? My friend Ben Plaut did it before but he left school before he could fix it again.[/QUOTE]
Did you try the usual remedies?  E.g.
```

$ startx
$ /etc/init.d/gdm start
$ sudo dpkg-reconfigure xorg

```

From the command line, you can also ftp or scp your paper to another server, burn it to the CDRW drive, mail it to a web email account, etc.

Are any of those possibilities for you?

---

### Post by shade11 on 2006-02-21
doesnt work. I need to be able to mount it from the live disk. From there I can save it to a disk and then I can re-install another day.

---

### Post by cwaldbieser on 2006-02-21
[QUOTE=shade11]doesnt work. I need to be able to mount it from the live disk. From there I can save it to a disk and then I can re-install another day.[/QUOTE]
Well, from the LiveCD, can you
```

$ sudo fdisk -l

```
to list the partitions?  How have you tried mounting the drive, and what kind of error do you get when you do?

---

### Post by shade11 on 2006-02-21
I fixed it. I think.

I booted live

went into terminal

sudo -s
mkdir /media/sda2
mount /dev/sda2 /media/sda2
fsck

For now I am going to re-install to remove all my errors. Using an ext3 partition. But can someone please tell me what the errors for a jfs partition are. Becuase I was using jfs before.

---

### Post by RAOF on 2006-02-21
[QUOTE=shade11]...
For now I am going to re-install to remove all my errors. Using an ext3 partition. But can someone please tell me what the errors for a jfs partition are. Becuase I was using jfs before.[/QUOTE]
No idea.  But jfs_fsck should fix whatever problems there are.  Unless your filesystem was *really* broken (or, I suppose, if JFS was prone to catastrophic failure, as XFS seems to be on occasion).

Incidentally, why were you using jfs anyway?  I've not seen people running it :)
XFS for large-file performance, yes.  Reiserfs because it seems to have good all-round performance, and ext3 because it's the default.  Never JFS :)

---

### Post by shade11 on 2006-02-22
So then what is so specail about jfs then?

And what would be the best format discluding ext3?

---

### Post by RAOF on 2006-02-22
[QUOTE=shade11]So then what is so specail about jfs then?[/QUOTE]
I don't know - you're the one who chose to use it :cool: 

As to filesystems, I've been using resierfs.  It works, it's survived the many hardlocks, restarts, and general filesystem torturetest that is my general use :)

Aside from that, ext3.  Seriously.  It's mature and everyone's standard (= highly stable).  It's not particularly slow.  It works.

---

