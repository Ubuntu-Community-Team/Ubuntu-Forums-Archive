---
title: "Mounting NTFS partition and more?"
date: 2005-07-30
forum: Desktop Environments
---

### Post by happogiri on 2005-07-30
Hello,

how does it go (mount -t ntfs /dev/hdWHAT /mnt/windows)? Where can I see information about my partitions (hda, hdb,...)? SOLVED! (I found it in the 'starters guide') NOT quite...

And one more totally newbie question...:
If I install some new programs in my new Ubuntu, how do I get them to show in 'Applications' -menu in gnome? Thank You!

---

### Post by bored2k on 2005-07-30
[QUOTE=happogiri]Hello,

how does it go (mount -t ntfs /dev/hdWHAT /mnt/windows)? Where can I see information about my partitions (hda, hdb,...)? SOLVED! (I found it in the 'starters guide')

And one more totally newbie question...:
If I install some new programs in my new Ubuntu, how do I get them to show in 'Applications' -menu in gnome? Thank You![/QUOTE]
 You solved your ntfs problem ? Right on.

Menu editor ? You need SMEG.
[http://ubuntuguide.org/#smeg](http://ubuntuguide.org/#smeg)

---

### Post by happogiri on 2005-07-30
[QUOTE=bored2k]You solved your ntfs problem ? Right on.

Menu editor ? You need SMEG.
[http://ubuntuguide.org/#smeg](http://ubuntuguide.org/#smeg)[/QUOTE]
 Uhhh... I only managed to mount one partition (the first one that I appended to fstab).

First I made /media/windows directory, then backed up the fstab and wrote:
```

/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

```
I also wrote three similar lines to fstab, just that I changed hda1 to hdb1 etc... Yet only the contents of hda1 are there?

---

### Post by bored2k on 2005-07-30
[QUOTE=happogiri]Uhhh... I only managed to mount one partition (the first one that I appended to fstab).

First I made /media/windows directory, then backed up the fstab and wrote:
```

/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

```
I also wrote three similar lines to fstab, just that I changed hda1 to hdb1 etc... Yet only the contents of hda1 are there?[/QUOTE]
 Try to be verbose and explain. If you're trying to mount all three partitions on a same point moint (media/windows), I think you know what your problem is (you can't).

We need your fdisk -l and for you to tell wich drives you want mounted. Your df -h wouldn't hurt either.

---

### Post by paper-sith on 2005-07-30
Just a thought,

I created separate media/windows mount points for each of the different partitions.

ie:  hdb1 = media/windows
      hdb2 = media/windows2

hope this helps.

---

