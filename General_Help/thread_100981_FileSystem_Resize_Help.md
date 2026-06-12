---
title: "FileSystem Resize Help"
date: 2005-12-08
forum: General Help
---

### Post by bananaman on 2005-12-08
Hi there...

I resized my linux partition through a windows partitioning software, the problem is that linux doesnt see the change and still shows the old size of the partition...

I was told it was because i did not resize the file system...

Can someone help me on how to do this?
Please...its killing me...
thanks...

---

### Post by tomchuk on 2005-12-08
What filesystem are you trying to resize?

Most filesystem tools include a utility to resize a filesystem. For example running resize2fs on an ext2 or ext3 filesystem will resize it to fill the partition. ie. run: `resize2fs /dev/hda1` and it will grow to fill the containing partition.

gparted, which is included on the breezy liveCD will give you a nice front end to the various filesystem and partition utils.

---

### Post by bananaman on 2005-12-09
thank you thats great advice!

only one thing...i cant resize the filesystem im using... so the question is
if i load the breezy live cd will it recognize and resize the filesystem? its an ext3

thank you for your help

---

### Post by Ocxic on 2005-12-09
[QUOTE=bananaman]thank you thats great advice!

only one thing...i cant resize the filesystem im using... so the question is
if i load the breezy live cd will it recognize and resize the filesystem? its an ext3

thank you for your help[/QUOTE]


If you can access all of the files on your partition by all means find the backup how-to in the forums and backup everything. then reformat the partition to the size you want, and restor you backup there. by reformatting you also save the trouble of any disk read problems cause something got messed up during the resizing, and from what you say i gather the resize failed

---

### Post by bananaman on 2005-12-09
ok...i did it...and it was a success...well, sort of

i couldnt do anything from the ubuntu live cd...neither with gparted nor with the terminal...

i loaded the slax live cd and tried the "resize2fs" command... this is what happened

```
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 371M  177M  194M  48% /
/dev/hda1              40G  4.8G   36G  12% /mnt/hda1
/dev/hda2             6.1G  2.3G  3.5G  40% /mnt/hda2
/dev/hda4              94G   33G   61G  36% /mnt/hda4
root@slax:~# resize2fs /dev/hda2
resize2fs 1.35 (28-Feb-2004)
/dev/hda2 is mounted; can't resize a mounted filesystem!

root@slax:~# umount /dev/hda2
root@slax:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 371M  177M  194M  48% /
/dev/hda1              40G  4.8G   36G  12% /mnt/hda1
/dev/hda4              94G   33G   61G  36% /mnt/hda4
root@slax:~# resize2fs /dev/hda2
resize2fs 1.35 (28-Feb-2004)
Please run 'e2fsck -f /dev/hda2' first.

root@slax:~# e2fsck -f /dev/hda2
e2fsck 1.35 (28-Feb-2004)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
UBUNTU: 95608/1636352 files (2.8% non-contiguous), 2606973/6538455 blocks
root@slax:~# resize2fs /dev/hda2
resize2fs 1.35 (28-Feb-2004)
Resizing the filesystem on /dev/hda2 to 15759764 (1k) blocks.
*** glibc detected *** double free or corruption (!prev): 0x080526a0 ***
Aborted
root@slax:~# mount /dev/hda2
root@slax:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 371M  177M  194M  48% /
/dev/hda1              40G  4.8G   36G  12% /mnt/hda1
/dev/hda4              94G   33G   61G  36% /mnt/hda4
/dev/hda2              15G  2.3G   12G  17% /mnt/hda2
root@slax:~# e2fsck -f /dev/hda2
e2fsck 1.35 (28-Feb-2004)
/dev/hda2 is mounted.

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

check aborted.
root@slax:~# umount /dev/hda2
root@slax:~# e2fsck -f /dev/hda2
e2fsck 1.35 (28-Feb-2004)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
UBUNTU: 95608/3940352 files (2.8% non-contiguous), 2995737/15759764 blocks
root@slax:~# 
```

so there you go...it worked...but gave an error, can someone explain what this is?
```
*** glibc detected *** double free or corruption (!prev): 0x080526a0 ***
Aborted
```

anyways, the importan thing is, the filesystem is resized which is what i wanted,
thank you very much for your help i really appreciate it and hopefully the error is nothing to worry about... hopefully

thank you very much again...

---

### Post by tomchuk on 2005-12-09
Looks like a bug in resize2fs or glibc, as long as your partition resized and your files are still there, nothing to worry about.

A little googleing turns up this error in every distro's bug tracker over the last few years. Apparently RedHat [hacked together a patch](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=132707) a while ago that fixed it, then the maintainer [fixed it on his own](http://thunk.org/hg/e2fsprogs/?cmd=filediff;node=a89929b46367c37a1e02b627548a44c4f3996ca9;file=lib/ext2fs/ChangeLog).

I can't seem to duplicate the bug on my own machine, but [this bug](http://bugzilla.ubuntu.com/show_bug.cgi?id=18201#c6) seems to suggest that it's a glibc problem. You should head over to [Ubuntu Bugzilla](http://bugzilla.ubuntu.com/enter_bug.cgi?product=Ubuntu) and file a bug with the output that you posted above.

---

### Post by bananaman on 2005-12-09
perfect...
thanks for the info and the help...
later!

---

### Post by Ocxic on 2005-12-09
thats not a bug, I know hardrives, it found something it didn't like on the drive during the resize, i can almost gerantee(sp?) that one day you're gonna find a couple of corrupt files. I suggest re-formatting your newly sized partition to be safe

---

### Post by linuxguiri on 2006-04-11
[QUOTE=bananaman]
I resized my linux partition through a windows partitioning software, the problem is that linux doesnt see the change and still shows the old size of the partition...

I was told it was because i did not resize the file system...[/QUOTE]

Just in case anyone else is searching the forums for help on resizing ext3 partitions (as I was):

Using the GParted LiveCD to expand an ext3 partition gave me resize errors and it said:
```
please run e2fsck -f /dev/hda#

```
I was finally able to force the resize by opening aterm (in the GParted LiveCD) and running the following two commands:

```
e2fsck -f /dev/hda#
resize2fs -f /dev/hda#

```
where # is the number of the harddrive partition you wish to resize.

---

