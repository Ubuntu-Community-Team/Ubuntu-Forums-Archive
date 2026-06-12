---
title: "How can I detect if anyone ever copied my files?"
date: 2009-03-16
forum: General Help
---

### Post by lm433 on 2009-03-16
Hi all,

I have to leave a sub directory open for the coworker. But I'm wondering if I can detect everyone that has ever viewed or copied my files in that shared directory. How can I do that?

Thank you!

---

### Post by lm433 on 2009-03-16
17 views and no reply. Does it mean it's impossible? :(

---

### Post by jespdj on 2009-03-16
No, it only means that people who viewed your question didn't know the answer. Sorry, I don't know either.

---

### Post by kellemes on 2009-03-16
> **lm433 said:**
> Hi all,

I have to leave a sub directory open for the coworker. But I'm wondering if I can detect everyone that has ever viewed or copied my files in that shared directory. How can I do that?

Thank you!

There are ways to monitor changes to a file or directory but viewing or copying doesn't modify the file so I can't think of a way to handle this.

---

### Post by jellylogix on 2009-03-16
> **lm433 said:**
> 17 views and no reply. Does it mean it's impossible? :(

It probably means that people would like to know if this was possible. Personally I think it would be cool if ubuntu was able to track this, however on that note: I don't know.

---

### Post by sdennie on 2009-03-16
It will depend on how you have your filesystems mounted.  Files have access times associated with them so, you could potentially see the last time a file was accessed with:

```

ls -l --time=atime

```

However, you probably won't be able to get useful information because by default, Ubuntu mounts filesystems as relatime.  That means that access time is only updated with modification time.

---

### Post by heindsight on 2009-03-16
This is by no means foolproof, but you could try use something like:
```
lsof +D dir -r 1
``` 
That will cause lsof to repeatedly (once per second) produce a listing of all open instances of files under the directory dir.

Of course this doesn't necessarily help much, since chances are a command like cp won't have the file open for as long as a second (unless it's a really large file) and so chances are lsof won't even notice cp accessing 
the file.

It occurs to me though, that it may be possible to write an app (or quite possibly it has already been done) using the inotify library to monitor a set of files and report on when files are accessed (I'm not sure if it would necessarily be possible to use that to also report which process belonging to which user, running which command actually accessed the file).

---

### Post by 73ckn797 on 2009-03-16
It seems that copying a file and being able to know what was copied, is not a simple task. The file being accessed may be determined but I have only seen that info when using Windows. Changes to a file would be time stamped. The only other way would be to require a logon by others where you could control what they can access.

I do not know the programming to make what you ask possible.

---

### Post by heindsight on 2009-03-16
I've slapped together a little hack, that I call accessmon, which monitors a directory (specified as a command line argument) and all its subdirectories (and their subdirs, etc.). It reports every open and every close of any file in any of the directories being monitored.

For example, if accessmon is run with /foo as argument:
```
accessmon /foo
```
Then:
if file /foo/bar/baz is opened, accessmon prints:
```
o:/foo/bar/baz
```
if /foo/bar/baz was open for writing and is closed, accessmon prints:
```
cw:/foo/bar/baz
```
if /foo/bar/baz was open (but not for writing) and is closed, accessmon prints:
```
c:/foo/bar/baz
```

It continues monitoring until it is killed or all directories it was monitoring are deleted.

Unfortunately I could not find a way to obtain information about the process that opened the file.

It is possible to pipe the output to awk and run lsof each time a file is opened, in an attempt to gain information about the process accessing the file. 
```
accessmon DIR | awk -F: '($1 == "o") {system("lsof "substr($0,3))}
```
Unfortunately, this doesn't often work - most of the time it takes so long for accessmon to receive notification of the file opening and report it and then for awk to process the output and run lsof, that the file is already closed again long before lsof can find out who opened it.

Hmm, the forums don't allow uploading .c files, so I've had to gzip it.

---

### Post by sdennie on 2009-03-16
@heindsight: I'm sure it's possible to get the info you're missing in realtime because iotop can do it.  It's a small tool written in python so, it should be really easy to figure out what it's doing to get the name of the processes that's causing I/O.

Though another possibility would be to enable block_dump from /proc/sys/vm/block_dump and tail -f /var/log/syslog | grep READ | grep your_directory.  That would make for gigantic log files though.

---

### Post by heindsight on 2009-03-17
> **sdennie said:**
> @heindsight: I'm sure it's possible to get the info you're missing in realtime because iotop can do it.  It's a small tool written in python so, it should be really easy to figure out what it's doing to get the name of the processes that's causing I/O.

Thanks, I'll look into that :)

EDIT:
I don't think the iotop way would work for this. It uses the kernel's [taskstats interface]("http://www.kernel.org/doc/Documentation/accounting/taskstats.txt") to get stats for running processes. 

The way that works is that a process requests stats for a specified set of processes from the kernel and the kernel replies with various stats (in a [taskstats struct]("http://www.kernel.org/doc/Documentation/accounting/taskstats-struct.txt")). It doesn't give any information about open files, only stats on how much IO the specified processes are doing.

---

### Post by unutbu on 2009-03-17
The output in /var/log/syslog that is generated after doing
```

sudo sh -c "echo 1 > /proc/sys/vm/block_dump"

```
is close to what is needed:

For example, 
```

Mar 17 17:56:45 turtle kernel: [33966.088038] emacs-snapshot(6208): dirtied inode 1662992 (ddd) on sda6
```

It records the time, PID, and inode of the modified file. All that's needed is the ower of the process. iotop / top does this so that part is doable.

Any ideas on how to deal with the copious output in /var/log/syslog?
Is there any way to send the kernel messages to a block file (FIFO?) instead of to /var/log/syslog?

---

### Post by heindsight on 2009-03-18
> **unutbu said:**
> The output in /var/log/syslog that is generated after doing
```

sudo sh -c "echo 1 > /proc/sys/vm/block_dump"

```
is close to what is needed:

For example, 
```

Mar 17 17:56:45 turtle kernel: [33966.088038] emacs-snapshot(6208): dirtied inode 1662992 (ddd) on sda6
```

It records the time, PID, and inode of the modified file. All that's needed is the ower of the process. iotop / top does this so that part is doable.

Any ideas on how to deal with the copious output in /var/log/syslog?


Hmm, it might be doable. Once you have the PID it should be easy enough to get the owner - the simplest I can think of right now is to stat /proc/PID.

However, I'm not sure this is good enough. Even if you could somehow reduce the sheer volume of log data, you'd still have to do some processing to:
[LIST]
[*]Parse the input to get the time, filename, PID and inode
[*]Get the full path to a file (I notice that log output just gives inode number, device and filename)
[*]Decide whether you're actually interested in accesses to this file
[/LIST]
In the time it takes to do all that, the process that accessed the file might have ceased to exist.

Of course you could stat /proc/PID as soon as you get the PID from the log and then just discard the info if it turns out you're not actually interested in it. However, the process might even exit before you even read the log lines telling you that it accessed a file you're interested in (eg if someone cats a file of only a few KBs).

Part of the problem is that you're doing this in a userspace process - completely at the mercy of the kernel's scheduling algorithms.

Another issue is that if someone reads from a hardlink to a file you're interested in, you might not even realise it unless you keep track of the inode numbers of every single file you're interested in.

To summarise, I think that the only way you could be 100% certain of getting all the info you want for each access to each file you're interested in monitoring, would be if the kernel could supply all that information *atomically*. 

> **unutbu said:**
> 
Is there any way to send the kernel messages to a block file (FIFO?) instead of to /var/log/syslog?

I'm sure this should be possible with an appropriate rule in /etc/syslog.conf

---

