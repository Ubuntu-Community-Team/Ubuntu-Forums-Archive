---
title: "NTFS read/write"
date: 2006-06-08
forum: Desktop Environments
---

### Post by morequarky on 2006-06-08
Has anyone gotten this to work in Ubuntu!?!?

A lot of people want this ability.  The article says linux-ntfs is too complicated for newbies.  I have no clue what 'mount(8 )' means, so the software below might be better for newbies.

[good article]("http://www.linux-watch.com/news/NS8947869272.html")

[source website]("http://www.jankratochvil.net/project/captive/")

[package download]("http://www.jankratochvil.net/project/captive/dist/captive-static-1.1.7.tar.gz")

Personally I use a fat32 partition and don't really need this ability, but others seem to be salivating at this kind of stuff.

---

### Post by murataht on 2006-06-08
it would be great, if this is included in dapper!!!

---

### Post by morequarky on 2006-06-09
Wow the board is SO busy these days.  So many post.  So many qustions, like this one.

---

### Post by morequarky on 2006-06-14
Is there a howto on this somewhere that I don't now about?

---

### Post by Fatjoint on 2006-06-15
[QUOTE=morequarky]Is there a howto on this somewhere that I don't now about?[/QUOTE]


[http://www.ubuntuforums.org/showthread.php?t=142481](http://www.ubuntuforums.org/showthread.php?t=142481)

---

### Post by xwipeoutx on 2006-06-15
I used Captive NTFS back in the days - it was super super slow (like 50kb/s), and comes with lots of warnings so my advice there is to not use it.

I think Linux-NTFS can read/write if you play around with it enough, but again, it's experimental and I wouldn't (and haven't) risked it.

I'd recommend, if you're trying to share files between linux and windows, to partition your shared drive as fat32 or ext2/3 (there's ext2/2 readers for windows out there if you look around)

For the record, 'mount' is a linux command that mounts devices (usually drives) to a location... type "man mount" at the command line to read about it

---

### Post by cbaumann on 2006-06-15
I've mounted it using: 

```
sudo mkdir /media/windows
```

then

```
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```

If you want it to be mounted on startup, just add this line to your /etc/fstab.

---

### Post by Lorkki on 2006-06-15
[QUOTE=xwipeoutx]I think Linux-NTFS can read/write if you play around with it enough, but again, it's experimental and I wouldn't (and haven't) risked it.
[/QUOTE]

There's also an alternative [userland driver]("http://wiki.linux-ntfs.org/doku.php?id=ntfsmount") using FUSE, with partial but relatively safe write support. Not everything is implemented properly yet, so it'll work in some cases and silently fail in others, but it seems to be made so as to not do anything dangerous.

I've been using it without problems (besides sometimes not actually writing) for about a week now, but don't take that as an assurance. It's included in Dapper in the package **ntfsprogs**.

I also agree that Captive should only be touched with a very long stick, if at all. I've seen reports of people having their file systems completely hosed through its use.

[QUOTE=cbaumann]
```
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```

If you want it to be mounted on startup, just add this line to your /etc/fstab.[/QUOTE]

To pick a few nits, the fstab line should be:

```
/dev/hda1 /media/windows/ ntfs nls=utf8,umask=0222 0 0
```

---

