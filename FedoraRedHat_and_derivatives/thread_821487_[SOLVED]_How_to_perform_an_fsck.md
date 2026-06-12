---
title: "[SOLVED] How to perform an fsck?"
date: 2008-06-07
forum: Fedora/RedHat and derivatives
---

### Post by PmDematagoda on 2008-06-07
I'm asking a bit of a silly question here, but how does one perform an fsck check on Fedora(Fedora 9 specifically), I tried doing it as root but it tells me that the command is missing.

---

### Post by John.Michael.Kane on 2008-06-07
The command is installed on my fedora 9 test system. 

```
xxx@localhost ~]$ su -
Password: 
[root@localhost ~]# fsck
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/VolGroup00/LogVol00 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? 
```


Do you have e2fsprogs package installed?

---

### Post by PmDematagoda on 2008-06-07
I installed e2fsprogs, even ran fsck, e2fsprogs was already installed and fsck gives a command not found.

---

### Post by John.Michael.Kane on 2008-06-07
> **PmDematagoda said:**
> I installed e2fsprogs, even ran fsck, e2fsprogs was already installed and fsck gives a command not found.

That is strange. I am not sure why you cannot run fsck or at least get the same msg output I posted.

Try this.

su - to root

Then try typing the below at the command prompt
```
e2fsck
```

Which should give you the output below.
```
xxx@localhost ~]# e2fsck

Usage: e2fsck [-panyrcdfvstDFSV] [-b superblock] [-B blocksize]
		[-I inode_buffer_blocks] [-P process_inode_size]
		[-l|-L bad_blocks_file] [-C fd] [-j external_journal]
		[-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
```

---

### Post by PmDematagoda on 2008-06-07
This is really confusing, command not found....

And this is on a Fedora 9 install that I didn't tune or tweak.

---

### Post by PmDematagoda on 2008-06-07
This is strange, I can execute them properly if I execute the binary file found in sbin, otherwise I cannot.

---

### Post by PmDematagoda on 2008-06-07
Fixed it, I made a symbolic link of fsck to /bin linked to the one in /sbin and it now works:). Thanks for your help John.Michael.Kane:).

---

### Post by igknighted on 2008-06-07
> **PmDematagoda said:**
> Fixed it, I made a symbolic link of fsck to /bin linked to the one in /sbin and it now works:). Thanks for your help John.Michael.Kane:).

I think you are using the command 'su' to get root powers, rather than 'su -'.  The former only gives you super user rights, the later actually makes you root.  In order to get /sbin and a few others in your default path, you need to actually be root.  As an alternative, you could add /sbin to the default path, but using 'su -' is recommended.

You can also run fsck with the command /sbin/fsck.

---

### Post by PmDematagoda on 2008-06-08
> **igknighted said:**
> I think you are using the command 'su' to get root powers, rather than 'su -'.  The former only gives you super user rights, the later actually makes you root.  In order to get /sbin and a few others in your default path, you need to actually be root.  As an alternative, you could add /sbin to the default path, but using 'su -' is recommended.

You can also run fsck with the command /sbin/fsck.

Thanks for the clarification igknighted, you were right, that was the only thing I did wrong.

---

### Post by John.Michael.Kane on 2008-06-08
My apologizes. I should have been clearer and explained that I was issuing the (su -) command, and not the standard su.

---

### Post by PmDematagoda on 2008-06-08
> **John.Michael.Kane said:**
> My apologizes. I should have been clearer and explained that I was issuing the (su -) command, and not the standard su.

No problem, the main thing is that it was all figured out in the end:).

---

