---
title: "Mounting new EXT3 partition"
date: 2006-03-20
forum: Desktop Environments
---

### Post by pwrstick on 2006-03-20
Hey again.  I know this is easy, but I can't seem to find anything on this (probably because it's so easy).  Searches seem to bring up only things to do with Windows partitions.  Anyway:

I just formated one of my hard drives as EXT3 using gparted.  Real easy once I found that I had to *unmount* the hard drive I wanted to change (an NTFS formatted drive).

So now it appears to be created as:
/dev/sda1

Now I know I have to edit fstab (then mount -a right?), but I'm not sure what options to use.

Thanks!

---

### Post by krusbjorn on 2006-03-20
I dont really know what the dump and pass columns are for, but my entries look like this:

/dev/sda1       /path/to/mountpoint/           ext3    defaults        0       2

---

### Post by pwrstick on 2006-03-20
Good good now it's mounted.  Thank you!  That was my main question, what the 0  2 or 0  0 stuff was supposed to be.

OK, I can't write to the drive.  Do I have to chmod it?  Or set it up in fstab to be writeable?  (Did I mention I was a nub?! lol)

EDIT: It appears I can write to it in SU mode (i.e. writing a file like "sudo vi test will" work, but I can't just save to it).

EDIT2: **FIXED.**  Leaving this around for searching purposes.
The sda1 drive was mounted to /media/sda1

An ls -l command showed me that only the su had write privs, i.e.:
drwxr-xr-x  4 root root 4096 2006-03-20 13:50 sda1

So a chmod was in order:
sudo chmod ugo+rw sda1

This then gave me write priviledges.  I'm curious why it didn't get write privs by default.  Anyway, I'm glad no one responded to my write problem because it forced me to get to thinking about it, and I think I learned a few things along the way (like chmod!) \\:D/

---

### Post by pbaehr on 2006-03-20
Hmm... That's the same type of entry I have for my other drive and I can write to it fine.

I've never been entirely sure if the permissions for the mount point affect the permissions for the device mounted to it but I would check that just to be on the safe side.

I do know that those permissions will be overridden if they are less restrictive than the permissions set up in fstab but I don't know if that door swings both ways.

While we're at it, can someone who knows confirm if the permissions on the mount point affect the mounted media?

---

### Post by TLE on 2006-03-20
This [link]("http://www.tuxfiles.org/linuxhelp/fstab.html") should help explain the fstab including the last two collums. Also have a look at this [thread]("http://www.ubuntuforums.org/showthread.php?t=146060"), the guy there has a similar problem

EDIT. Oh you figured it out, just skimmed the thread *G*.

---

### Post by pwrstick on 2006-03-20
OK well I can write to it, copied over some stuff, and every thing copied into that folder has a new set of permissions.  I gotta figure out a way to make it so that anything copied in there will have rwxrwxrwx

---

### Post by pwrstick on 2006-03-20
OK, perhaps this is the conclusion of my interesting mounting experience.

After chmod'ing the newly mounted partition, I started copying files form an NTFS drive.  Apparently, since NTFS doesn't support the same kind of ugo (rwxrwxrwx) permission scheme, my files were writeable only if I was a root user.

I guess this is because the drive was originally mounted as a su?  And since there are no permissions on the ntfs partition, when it copies over it tags them in terms of the original state of the drive?

Anyway, once everything is copied over I'm going to recursively set the permissions and then call it a day.

I think.

And this (perhaps) concludes my mounting dilemma.

Edit: thanks for all the help everyone!

---

