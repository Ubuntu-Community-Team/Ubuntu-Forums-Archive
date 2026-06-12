---
title: "What do these tar backup output lines means"
date: 2009-03-22
forum: General Help
---

### Post by sofasurfer on 2009-03-22
```

tar: /sys/module/bluetooth/initstate: File shrank by 4091 bytes; padding with zeros
tar: /sys/module/bluetooth/refcnt: File shrank by 4094 bytes; padding with zeros
tar: /sys/module/bluetooth/sections/.note.gnu.build-id: File shrank by 4077 bytes; padding with zeros
tar: /sys/module/bluetooth/sections/.text: File shrank by 4077 bytes; padding with zeros
tar: /sys/module/bluetooth/sections/.exit.text: File shrank by 4077 bytes; padding with zeros
tar: /sys/module/bluetooth/sections/.init.text: File shrank by 4077 bytes; padding with zeros
tar: /sys/module/bluetooth/sections/.rodata: File shrank by 4077 bytes; padding with zeros
tar: /sys/module/bluetooth/sections/.smp_locks: File shrank by 4077 bytes; padding with zeros
tar: /sys/module/aes_x86_64/sections/.strtab: File shrank by 4077 bytes; padding with zeros
tar: /proc/sys/net/ipv4/route/flush: Cannot open: Permission denied
tar: /proc/sys/net/ipv6/route/flush: Cannot open: Permission denied
tar: /proc/2/task/2/exe: Cannot readlink: No such file or directory
tar: /proc/2/exe: Cannot readlink: No such file or directory
tar: /proc/3/task/3/exe: Cannot readlink: No such file or directory
tar: /proc/3/exe: Cannot readlink: No such file or directory
tar: /proc/4/task/4/exe: Cannot readlink: No such file or directory
tar: Removing leading `/' from hard link targets

```

Is this just processes that occur during tar archiving or is this an indication of an undesirable situation?

---

### Post by lloyd_b on 2009-03-22
The former, I think.  You really shouldn't be backing up the "/proc" and "/sys" filesystems in the first place - these are "virtual" filesystems that are dynamically created by the kernel, not actual files that you have to worry about losing.

Lloyd B.

---

### Post by sofasurfer on 2009-03-22
Yes, I know. 
I am using the --listed-incremental option. While learning about how to use it I had used the --exclude=$EXCLUDEDFILE option which should have excluded /proc, /sys, etc. Apparently it wasn't working right because along with trying to process these "excluded" directories it was also giving me errors.

So I think if I find out why "exclude" was not working right, and correct it, I will not see the output lines in question.

Thanks for your input.

---

### Post by sofasurfer on 2009-03-22
Any idea what the following means...
```

/$ tar --list --incremental --verbose --file=Sun12fullarchive.1.tar
tar: This does not look like a tar archive
tar: Skipping to next header
tar: Archive contains obsolescent base-64 headers
tar: Error exit delayed from previous errors

```

---

### Post by sofasurfer on 2009-03-23
I found that I do not get the errors if I do NOT compress the archive. But if it is compressed I always get the errors.

Another problem, probable just a very simple thing, is that "--exclude" does not work. Here is my command...

"tar cvf $FULLBACKUPFILE --exclude=/proc --listed-incremental=/snar $DIRECTORYNAME"

The command works great (except that it can not be used with the "z" option) if I do not use the "--exclude" option.

---

### Post by lloyd_b on 2009-03-23
> **sofasurfer said:**
> I found that I do not get the errors if I do NOT compress the archive. But if it is compressed I always get the errors.

Another problem, probable just a very simple thing, is that "--exclude" does not work. Here is my command...
tar cvf $FULLBACKUPFILE --exclude=--listed-incremental=/snar $DIRECTORYNAME

The command works great (except that it can not be used with the "z" option) if I do not use the "--exclude" option.

I've never tried incrementally updating a compressed tar file, so that may very well be incompatible (if you have the space, you could potentially uncompress it, do the incremental backup, and then compress it again, but that's a lot of busy work...)

Your syntax for "--exclude=" makes no sense - what exactly are you telling it to exclude? (The normal usage is "--exclude=PATTERN", where PATTERN is a pattern to exclude.  If you need multiple patterns, I'd suggest putting them in a text file and using "--exclude-from=FILE" instead).

Lloyd B.

---

### Post by sofasurfer on 2009-03-23
I will study your suggestion and figure out how to do what you say. 
As for my use of 'exclude' not making sense... ordinary tar command will let you use '--exclude=any/file' to exclude file or directory from the archive such as the unwanted /sys, /lost+found, /proc, etc.
Now I know that the 'exclude' option probably does not work with '--listed-incremental.

Thanks for your reply.

---

### Post by Xiong Chiamiov on 2009-03-23
--exclude and --listed-incremental are both flags; you can't use one as a parameter to the other.

---

### Post by sofasurfer on 2009-03-23
I just realize that I made a mistake in post #5 where I show my tar command. I just edited it. Isn't it correct now? Or is "exclude" still not compatible in that command line?

---

