---
title: "Sharing an extant /home by mounting in $HOME/mnt"
date: 2009-02-19
forum: General Help
---

### Post by Piraja on 2009-02-19
Dear all!

Yesterday I installed CrunchBang 8.10 on a spare 50G partition of my 500G external HDD plugged onto an old desktop PC, in order to try it out. So far so good — the first few hours with CrunchBang have been really promising. 

On the external 500GB USB drive I have also Ubuntu 8.10 installed with Gnome & Openbox, and a separate /home partition of ca. 200GB (to mention just the relevant stuff — let's call it home@sdb2), one which I have been using with Ubuntu so far, and will probably be using it once in a while in the future, too (not to mention my kids & wife, who will want to stick with Gnome). Now I have a question about the mentioned /home partition (home@sdb2) or, more specifically, my home folder there (home@sdb2:piraja) and using it with the new #! install, i.e. sharing it among the "basic" Ubuntu (let's call its location ubuntu@sdb1) and the new CrunchBang system partition (crunchbang@sdb3). 

In order to work with files in the old /home (home@sdb2 a.k.a. /media/disk-1), I have mounted /media/disk-1/piraja in my new ~/mnt (with "sudo mount --bind /media/disk-1/piraja /home/piraja/mnt/"). This seems to work pretty well: I can e.g. edit my existing ODF files with OpenOffice and save them in the old location with no hassle whatsoever.* And I would not like to use the old /home (now in /media/disk-1) as my new /home partition, except via mounting it as described, because I don't want the inconveniencies of using the same dotfiles in both distros, sharing the old /home between the old Ubuntu 8.10 installation (ubuntu@sdb1) and the new CrunchBang partition (crunchbang@sdb3). 

My question is if you could think of any *caveat*, i.e. any reason why I should *not* mount the old /home partition in my new #! /home/piraja/mnt. I remember having been warned against mounting remote file systems in my $HOME (such as WebDAV), but I don't know if that warning applies to this case or not, having the mounted stuff on a single HDD.

I would gladly receive further tips & advice with regard to the described situation & the goal of using the stuff in the old /home in both crunchbang@sdb3 and ubuntu@sdb1. For example, would it be reasonable to add an item in fstab for the old /home/piraja, with the partition's UUID and the mount point /home/piraja/mnt, or should the mount point rather be e.g. /mnt/tmp or something like that?

I hope I'm making a point here, and a clear one too.

Thanks in advance and best regards,

Piraja


*) Well, I have not tried using the same files on the old Ubuntu partition yet, after editing them at the #! partition — could it be that this sharing of a /home partition messes up permissions? That remains to be seen... I'm pretty ignorant about these matters, as you see, but learning bit by bit, I guess — sometimes the hard way of trial and error, too.

---

### Post by Piraja on 2009-02-21
I also mount my old $HOME's Music dir in my new music dir:
```
sudo mount --bind /media/disk/piraja/Music /home/piraja/music/
```
All this seems to work pretty well, but is there some reason why I should e.g. use symlinks instead of mounting the directories of the old home partition at the new one?

I try to be cautious with these things, because I have once deleted a zillionbillion bytes of data when I thought I was just removing a symlink (but it was a hard link instead, an important distinction I discovered a bit too late &#8212; heh)...

---

### Post by Piraja on 2009-02-24
I'll bump this thread, because I do believe this is a good question or a bunch of questions, at least if I try to rephrase a bit.

It is a little bit inconvenient to use 

```
sudo mount --bind /media/disk/piraja/ /home/piraja/mnt
```

every time, for example because the mountpoint of the old /home partition tends to vary between /media/disk and /media/disk-1 at each reboot. Therefore, I wonder if it's somehow possible to mount the partition (or, more *verbatim*, its *fs*) with its UUID, preferably at the CrunchBang startup...? I *have* tried to find this information but haven't yet succeeded &#8212; I suppose this is either an unusual situation or a very trivial one.

Does this make any sense? Am I trying to kick down an open door? Should I use symlinks instead? Should I stop asking such silly questions? Should I just copy my working directories to the new smaller home partition and stop fooling around?

Actually, I have not been able to make MPD work with symlinks, in spite of following several how-tos, but mounting the old /media/disk/Music dir at the new mountpoint ~/music works like a charm.

Quite a few open questions are entangled with these, but this is where I would start...

---

### Post by handy on 2009-02-24
You may find what you need in this excellent how-to:

*_[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)_*

---

### Post by Piraja on 2009-02-24
> **handy said:**
> You may find what you need in this excellent how-to:

*_[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)_*
Thanks — that's one how-to I'm actually already pretty familiar with, done it a few times... Actually the point is that I'd like to share the data in an extant separate /home partition (which I created following exactly the mentioned tutorial several months ago) between two root partitions, one of them running Ubuntu and another one running CrunchBang, without using the same dotfiles, etc., and without messing up permissions. However, after doing some studying on this, I think my initial solution of using "mount --bind ..." was not such a bad idea after all, just binding the directories and not for instance mounting the whole (old) home partition in /mnt/homesweethome or something (which I tried today, but which causes some permissions issues: the OOo.org files I edited got locked by my #! identity...). 

Sorry if this seems confused and complicated, but I think I'm getting nearer of sorting it out. Thanks again for your suggestion, handy. I like your avatar, by the way.

---

### Post by Piraja on 2009-02-25
OK, here's what I decided to do after these confused ramblings: I labeled the big old separate /home partition "torppa" (Finnish for "croft" or "crofter's cottage": "sudo e2label /dev/sdb2 torppa") and now its mount point is easily identifiable as /media/torppa (I don't really know why I wanted to mount it anywhere else &#8212; maybe just because I'm a simpleton). Then I made a symlink pointing to /media/torppa/piraja in my /home dir ("sudo ln -s /media/torppa/piraja /home/piraja"). As simple as that. So far so good &#8212; I guess I won't run into any trouble with this decision.*

Thanks for reading and sorry for taking your time &#8212; maybe I should read and think for awhile before I act and post...

* Well, I quess I cannot be *removing* files via the symlink, but that's almost like a security feature,  so who cares &#8212; the 200 GiB crofter's cottage can wait for occasional cleanups...

---

### Post by vanadium on 2009-02-25
Your approach is the good one.

> Well, I quess I cannot be removing files via the symlink, but that's almost like a security feature, so who cares — the 200 GiB crofter's cottage can wait for occasional cleanups...

You can, provided you have the permission. For practical purposes, a symlink behaves just like a directory.

---

### Post by Piraja on 2009-02-25
Thank you, Vanadium. I guess I had misunderstood something about deleting files via the symlink.

---

