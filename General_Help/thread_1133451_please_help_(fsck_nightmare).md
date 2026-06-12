---
title: "please help (fsck nightmare)"
date: 2009-04-22
forum: General Help
---

### Post by Th3Professor on 2009-04-22
Okay, I'm worried about something here... my system started behaving odd, locked up while running, had to force a reboot, then had to get the bios to boot into the system, well then it put me into the "maintenance" mode (had to log into root). I did what it said, fsck, and "i.e. no -a or -p", so I just did a plain fsck on the / but (which is /dev/sda5 in this case), only I didn't catch the ext2 default, and mine is ext3. I went ahead and ran it:

fsck /dev/sda5

And I selected "yes" to everything.

Now I suspect it's even worse, since it was expecting ext2 with the command I used.

Can I fix it?

I want my *nix back. I had to resort to Windows (right now), only I'm hoping this is only temporary.

My /home is in the / partition. It is very important that I recover that data, as well as actually getting the system running again.

Please help. Thank you!

---

### Post by codeseer on 2009-04-23
Did it say that it corrected anything? I thought fsck, when ran without parameters iterates the /etc/fstab for devices but doesn't actually correct anything.

---

### Post by DagMan on 2009-04-23
You can boot into the live cd and run fsck from there. In fact, I think you can open the partition editor, right click on a partition and choose to run fsck or 'check for errors'.  Unmount your swap parttion for good measure first though, which you can also do by right clicking on it in the partition editor. If that does not help things out, then see if you can mount your partition from the live cd and copy the data to an external drive, or if you don't have one then you can mount your windows partition at another location and create a folder in the root of where c: would be then copy the files over.
so to mount your linux partion for example to mount both and copy your entire home folder excluding hidden files, which you likely don't want, though think about this and be thourough.
```
mount /dev/sda5 /mnt
```
and then assuming windows is at /dev/sda1 (change it if it isn't
```
/mount /dev/sda1 /media
mkdir /media/linux-files
cp -a /mnt/home/* /media/linux-files
```
however I would myself rather use an external drive if I had one.

Good luck

---

### Post by Th3Professor on 2009-04-23
ok all turned out ok
i loaded livecd
mounted sda5 (EDIT: mounted -t ext3 -ro) (and tried -t ext2 -ro, in ro both worked) (did tune2fs -l /dev/sda5 and it showed journal system, aka ext3... so my previous fsck didn't mess up the fs, but wanted to double check anyway...)
checked files/dirs (nothing wrong, thankfully)
unmounted
fsck'd sda5 (just to be sure)
i did this:
fsck.ext3 -fv /dev/sda5
...and all is well...
and i'm back in my system again.
weird, dunno why it acted up like that.

---

### Post by formol on 2009-04-23
i got the same problem.  i suspect that the reboot option in jaunty cause problem to the mount/unmount status of a partition. 

/dev/sda1 is my / and seems to be okay
when I reboot, /dev/sda6 (/home) is always "unclean mounted" or something like that. 

sda1 = ext4
sda6 = ext3

---

### Post by Th3Professor on 2009-04-24
> **formol said:**
> i got the same problem.  i suspect that the reboot option in jaunty cause problem to the mount/unmount status of a partition. 

/dev/sda1 is my / and seems to be okay
when I reboot, /dev/sda6 (/home) is always "unclean mounted" or something like that. 

sda1 = ext4
sda6 = ext3

This is basically what I did, I'll put your sda6 in there, otherwise just replace "stuff" with whatever directory name you want, and you'll need either root access or sudo:

1. Boot into a livecd
2. mkdir /mnt/stuff
3. mount -t ext3 -o ro /dev/sda6 /mnt/stuff
4. if it works, take a look throughout /mnt/stuff (hopefully everything is in there)
5. if not, then umount /mnt/stuff and mount -t ext2 -o ro /dev/sda6 /mnt/stuff
6. see 4.
7. go ahead and check if it's still ext3 (journalling fs) with: tune2fs -l /dev/sda6 (look for "has_journal" within "Filesystem features:"), if you see it, it's still ext3
8. you might also want to inspect your "lost+found" (the files/etc. from home may have been moved into that location)
9. unmount it (umount /dev/stuff)
10. fsck.ext3 -fv /dev/sda6

Going back to 7., if you find that it's no longer ext3, you can try:
tune2fs -j /dev/sda6
(I haven't done that yet so you might want to double-check, perhaps test it to be sure)

But anyway, this is assuming you did the same silly mistakes I made with my file system. lol

You might need to do nothing more than:

fsck.ext3 -fv /dev/sda6

(that's with force and verbose)

---

### Post by Blackpegaz on 2009-04-25
Hi, 

I had the same (umount) problem.

[Yesterday] I tried to add "defaults" option to /etc/fstab like that (for all partitions) :

# / was on /dev/sdb9 during installation
UUID=9618c3fc-a858-4408-85e4-5cb1ceeca22c /        ext4            **defaults**,relatime,errors=remount-ro 0       

Several restarts before, it SEEMS to work. Perhaps it's just a coincidence.

---

### Post by Th3Professor on 2009-04-25
I don't think ext4 is solid yet... I'm really looking forward to using it, though, when it's in better shape.

---

### Post by geirha on 2009-04-25
ext3 is ext2 with journaling. You can use a ext3 as ext2 with no real danger; the journal just won't be used. Additionally, a filesystem check on an ext3 filesystem is exactly the same as a filesystem check on an ext2 filesystem, so there is no danger of an ext3 being converted to ext2 (it already is ext2). The commands fsck.ext3 and fsck.ext2 are really just (hard)links to the same command as you can see if you list the files' inodes:

```
$ ls -i /sbin/e2fsck /sbin/fsck.ext3 /sbin/fsck.ext2
928809 /sbin/e2fsck  928809 /sbin/fsck.ext2  928809 /sbin/fsck.ext3

```

The fsck command looks at the start of the given partition(s) to figure out what filesystem it contains, then calls the proper command for that filesystem. In the case of ext3, it will use /sbin/e2fsck.

In the future, if there's a filesystem error on /, boot a liveCD and run fsck on it when it's not mounted. Running fsck on a mounted filesystem should work, but its safer to run it on an unmounted filesystem.

---

