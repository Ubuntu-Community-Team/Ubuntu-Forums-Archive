---
title: "Lost Files after mv, space still taken"
date: 2009-03-18
forum: General Help
---

### Post by JessT on 2009-03-18
Hello,

I was following the steps on [this]("http://po-ru.com/diary/linux-liposuction-or-xubuntu-in-under-a-gig-on-the-eee-pc/") blog to compress /usr on my eeepc.

When backing up my /usr directory, I decided to do it on an external USB, so the final command as su was;
mv /usr /media/disk/usr

This failed with an error along the lines of "Not able to copy file: Permission denied" and something to do with a link.

When I looked, nothing had been moved to /media/disk/usr, and /usr was gone.
However, checking the free disk space shows that the 1.4GB of /usr is still there... somewhere.

I checked for log files, but there didn't seem to be any.

Is there any way to get it back, or even completely free it (I have the compressed filesystem, so I don't mind losing the original /usr if need be).

Thanks for all the help you can provide.

---

### Post by JessT on 2009-03-26
Bump.

This is still an issue for me.
Infact, I've almost completely filled the meager 400MB it left me with.

Please, any help at all is appreciated!

---

### Post by mrsteveman1 on 2009-03-26
I would make sure the directory is actually gone with ls -a, also run du -h / to see if the files in the system actually match the used space listed by the other tools in the system.

Then i would run fsck on the filesystem from a livecd or single user mode, if there are no hard links pointing to the inodes anymore the space should have been freed.

Worst case you can remake the filesystem :)

---

### Post by dandnsmith on 2009-03-26
A further comment: it used to be the case that space didn't always get recognised as freed off after an effective deletion until a reboot.

---

### Post by JessT on 2009-03-26
Thanks for your comments, guys.


mrsteveman1;
ls -a shows that the files are definately not there.
du -h shows that the space has been freed.

A right-click >> properties in Nautilus shows that the space is still in use.

When I try to use more space than is shown as free from right-click >> properties, I get an out of space error.

e2fsck -f -p as a live user reported a few errors (inode counts not matching mostly - all fixed, 1.7% fragmentation), but the state of free space is still the same.


dandnsmith;
That's a useful tip to keep in mind - given that next to nothing on a *nix system really needs a restart it could have been a while before I noticed, however, I have rebooted a number of times, with no difference.


Any more ideas? Or possibly commands I could run to give the output if that would help?

Cheers guys.

---

### Post by mrsteveman1 on 2009-03-26
What does the df command tell you? Not much help i'm sure, if you get two different answers from 2 different programs its hard to say what the problem is.

---

### Post by apmcd47 on 2009-03-26
Have you looked in */lost+found*? The contents of */usr* could have been dropped in there after the directory had been lost. It might be a nightmare trying to figure out which file is which, as the names in */lost+found* will be randomly generated.

Andrew

---

### Post by JessT on 2009-03-26
df shows that the space is still taken! Which is contradictory to the results of du! What the..?

lost+found only contains about 24MB in two files - way off from the 1.8GB I'm missing.

I get the feeling it's something along the lines of the inodes have been unlinked, but not marked as free.

I ran debugfs from a live user, used the internal command lsdel to list all the deleted files, then went through and called kill_file on each "deleted" inode from that date- That freed up about 50MB (again, nowhere near the 1.8GB I'm after). However, when I remounted the filesystem (still under the live user) the space went away again!

Cheers for your continual help guys & gals, it's appreciated.

---

