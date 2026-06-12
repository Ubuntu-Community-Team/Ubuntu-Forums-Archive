---
title: "[SOLVED] bug in filesystem driver?"
date: 2006-09-27
forum: Desktop Environments
---

### Post by ropers on 2006-09-27
I just got this message:

```
root@tranquility:~/Desktop# find / -name nphelix.xpi
find: WARNING: Hard link count is wrong for /proc/4863: this may be a bug in your filesystem driver.  Automatically turning on find's -noleaf option.  Earlier results may have failed to include directories that should have been searched.
root@tranquility:~/Desktop# find / -name nphelix.xpi
root@tranquility:~/Desktop#

```

Does anybody know what to make of this?

Thanks and regards,
--ropers

---

### Post by Ramses de Norre on 2006-09-27
```
sudo shutdown -rF now
```
Will reboot and perform an fsck, that seems a good idea to try to me.

---

### Post by ajgreeny on 2006-09-27
Looks like it is something to do with the realplayer plugin for firefox.  Perhaps worth uninstalling that and reinstalling it to see if it clears the problem.

---

### Post by ropers on 2006-09-28
ajgreeny, Ramses de Norre: Thanks for your replies! :)

I have completed the fsck; there were no error messages/problems reported whatsoever. 

ajgreeny: Are you suggesting the realplayer reinstall because the nphelix.xpi file is realplayer related or do you have information on the purpose of /proc/4863 that would somehow link it to realplayer?

I'm asking because the **find / -name nphelix.xpi** command, when executed from a root shell (ie. after typing *sudo -s*; which I did) would traverse the entire file system while looking for that nphelix.xpi file. If in the course of walking the whole file system it encounters some problem somewhere, e.g. /proc/4863 in this case, then that in no way links /proc/4863 to realplayer. So unless you have other additional info to the contrary that independently establishes a link between /proc/4863 and realplayer, then I would say that realplayer has nothing to do with this error and reinstalling it is not likely to be of any use.

All that said, I would still be very curious as to why this kind of error message would have cropped up. Any ideas?

---

### Post by ajgreeny on 2006-09-28
I said the link is possible because the realplayer plugin is a file named nphelix.so and   .xpi files are normally what you would download to put various extensions into firefox if you were just downloading rather than letting forefox install them itself, hence my suggestion.  I'm afraid I can't help you further.  Have you tried what I suggested yet?  If so, what did it do?

---

### Post by sbergman27 on 2006-09-28
> **ropers said:**
> Does anybody know what to make of this?

Don't worry about it.  This is normal.  Note that it occurs in the /proc filesystem, a virtual filesystem which allows you to interact with the kernel.  I see this all the time.

You really want to restrict your search to the filesystems you want to search.  You can do this with the -mount option to find.  It will seach only that filesystem and ignore any filesystems, like /proc, which are mounted under it.

e.g.:

```
find / -mount -name myfile.txt
```

will search only the root filesystem.  If you have other filesystems that are mounted that you do want to search, e.g. /home, then you can do this:

```
find / /home -mount -name myfile.txt
```

---

### Post by sbergman27 on 2006-09-28
> **ropers said:**
> All that said, I would still be very curious as to why this kind of error message would have cropped up. Any ideas?

The /proc filesystem is constantly changing.  All the entries in directories like /proc/#### have virtual info related to the process with id ####.

If you want to play with this, you can do a:

```
$ ps a
```

to get the process status of processes owned by you.

Take note of one of proc ids. (The left most column)

The go into /proc/your_proc_id

In that directory, you will find "files" like "environ" and "cwd".

'cwd' is the current working directory for that process.  You can do:

 ```
$ cat cwd
```

 to see its contents.

'environ' is the environment for that process.  This would include the $PATH variable, etc.

The number of files in the "directory" changed in between the time find read the "directory" and when it counted the "files".

No real problem.

---

### Post by ropers on 2006-09-29
sbergman27: Thanks a whole bunch for your help! :) This is **excellent** information.

ajgreeny: I'm obviously not going to reinstall realplayer, because sbergman27 has just solved the issue. But thanks for your help anyway! :)

---

