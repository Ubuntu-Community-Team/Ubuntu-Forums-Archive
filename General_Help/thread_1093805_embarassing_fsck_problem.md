---
title: "embarassing fsck problem"
date: 2009-03-11
forum: General Help
---

### Post by Psyphre on 2009-03-11
Hi,
Ive been telling my friends how great linux is and one of them is interested in giving it a try. So I was gonna let her try it out on my computer, but when I turned it on it came up with an error (I was so embarrased, especially since I kept claiming linux to be rock solid :shock:).

I have no idea what could possibly have caused this since the last time I used the computer I didnt do anything that could have broken it, nor do I remember installing updates.

Anyway here's what I get at startup:
[COLOR="DimGray"]
activating swap...
checking root file system...
fsck 1.41.3 (12-oct-2008 )
/dev/sda3 contains a file system with errors, check forced.
/dev/sda3:
Inode 1163301 has illegal block(s).

/dev/sda3: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p option)
fsck died with exit status 4
	[FAIL]
*An automatic file system check (fsck) of the root filesystem failed.
A manual fsck must be performed, then the system restarted.
The fsck must be performed in maintanence mode with the root filesystem mounted in read-only mode.

*The root filesystem is currently mounted in read-only mode.
A maintanence shell will now be started.
After performing system maintanence, press CONTROL-D
to terminate the maintanence shell and restart the system.
bash: no job control in this shell
root@ed-desktop:~#[/COLOR]


So I tried typing 'fsck' and i get this next:

[COLOR="DimGray"]fsck 1.41.3 (12-Oct-2008 )
e2fsck 1.41.3 (12-Oct-2008 )
/dev/sda3 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Inode 1163301 has illegal block(s). Clear <y>?[/COLOR]

I'm a but unsure what to say since I dont even understand what the problem is, nor what's going on.

Please guys, I'm hoping some of you can help me with this issue and hopefully help me re-convince my friend linux really is more stable. Of all the times to happen it had to occur when she's around lol.

Thanks in advance.

---

### Post by b00g1e on 2009-03-11
I am also a new ubuntu user, so take this with a grain of salt. Hit the "y" button to say yes, and continue to do so until it prompts you to reboot. On reboot it should start correctly.

---

### Post by Psyphre on 2009-03-11
well I wasnt sure what it was deleting (read some posts where some guy lost the use of apt because of something similar) thats why I wanted to double check first. But since posting I did say yes (since I had no other option).
Had to say yes to a whole load of stuff and even after that it didnt work. 
Some error about X.

Still no luck I guess :(

---

### Post by Psyphre on 2009-03-11
ok tried rebooting a second time and it works now! so glad.
The problem is now solved, but I would still like to know why this happened in the first place?

Also how do i mark this thread as solved?

---

### Post by lykwydchykyn on 2009-03-11
Sounds like the hard drive may be going bad.  I would boot up the live CD and run the following from a terminal:

```

badblocks -v /dev/sda

```

If that starts spitting out a list of numbers, those are bad blocks.  That means the disk is physically going bad.

---

### Post by Psyphre on 2009-03-12
> **lykwydchykyn said:**
> Sounds like the hard drive may be going bad.  I would boot up the live CD and run the following from a terminal:

```

badblocks -v /dev/sda

```

If that starts spitting out a list of numbers, those are bad blocks.  That means the disk is physically going bad.

oh really? :(

Ok I'll try that, thanks.

---

