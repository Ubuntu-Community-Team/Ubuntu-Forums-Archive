---
title: "Cannot write file"
date: 2009-01-29
forum: General Help
---

### Post by steavy on 2009-01-29
I mounted a ntfs partition with ntfs-3g but I cant edit some files... :(

For example I got a directory name "temp" with a file "script.php", with ls -l I got this:

-rwxrwxrwx 2 root root  3451 2008-02-15 19:34 script.php

If open with sudo gedit script.php it will not let me edit the file, the I renamed the file to script.txt and now it let me change and save the file. After that I renamed to script.php again. Now the ls -l give me this output

-rwxrwxrwx **1** root root  3451 2008-02-15 19:35 script.php

The change was on the hard link, the number change to 1. I dont know what happens and need to be able to edit several file like the example. Any ideas?

Thank a lot!

---

### Post by jerome1232 on 2009-01-29
How did you mount the ntfs partition?

Since ntfs doesnt' support unix style permissions you have to tell it what the permissions are at mount time.


Here's an example of mounting an ntfs partition so that everything is owned by ther first user on the system and readable/writable by the first user on the system only (which I'm guessing is your user), check out man ntfs-3g for much more detail info
```
mount /dev/sdxx /mnt/partition -o uid=1000,gid=1000,umask=007
```

---

### Post by steavy on 2009-01-29
This is the /etc/gstab line to mount my ntfs partition

/dev/sda5 /home/steavy ntfs-3g defaults,locale=en_US.utf8 0 0

The rare thing for me is that I cannot edit those files even as root...they can only be edited after they change from 2 hard links to 1. But I dont know how to change that, it just happens when i rename the file to anything else :(

---

### Post by jerome1232 on 2009-01-29
Strikes me as odd but try adding an umask=000 to that  fstab  line remounting and testing it.

```
/dev/sda5 /home/steavy ntfs-3g defaults,locale=en_US.utf8,umask=000 0 0
```

---

### Post by steavy on 2009-01-29
Didnt work :(

if I try sudo gedit file.php, when trying to save a change I got this message:

Could not save the file /home/steavy/temp/file.php. gedit cannot handle file: locations in write mode. Please check that you typed the location correctly and try again.

Again, if I rename the file I can edit and save normally, the problem is I got many files like this one.

---

### Post by jerome1232 on 2009-01-29
Well it didn't hurt to try, I'm truly as confused as you are then. This isn't a  compressed volume or anything is it?

---

### Post by steavy on 2009-01-29
No it didnt hurt at all thanks equally for your help ;)

If by compressed you mean the check that you made on windows under the volume properties I guess it is, otherwise I dont know...

Damn! I can do everything else: edit any txt file, change tags on mp3s, read and write any other format I tried this days but I dont know what is wrong with these php files :(

---

### Post by Cato2 on 2009-01-29
Hard links (see [http://en.wikipedia.org/wiki/Hard_link](http://en.wikipedia.org/wiki/Hard_link) - worth reading as it has a good explanation of concepts including diagram) are somewhat unique to Unix/Linux, and are supported by NTFS in a somewhat different way to Linux, it seems.  

Generally, if the link count goes from 2 to 1, either one link has been removed, or the file has been copied into an entirely new file with the same name (the original file may still exist with 2 links, of which one has been renamed to allow the new file to take the original name).

To find out what's happening, try "ls -il" on this file, before and after all operations on it including gedit. This shows the 'inode number', which in Unix/Linux is the unique identifier of a file within a filesystem - e.g. file with inode 1789 may have several (hard) links and hence several filenames but there is only one file with that inode.   It's possible that the link is being broken, so you end up with 2 copies of the file. If you do "ls -il | sort -n" that will bring together any links to this file in the same directory, but the other link could be elsewhere.

See [http://linuxcommando.blogspot.com/2008/09/how-to-find-and-delete-all-hard-links.html](http://linuxcommando.blogspot.com/2008/09/how-to-find-and-delete-all-hard-links.html) for some more details on working with links.   I recommend you do a search for some of the files you've had this issue with, across the whole NTFS filesystem - the 'find' command for this is mentioned in this page.  It lets you use the inode number to locate the other links.  

Links of various sorts (symbolic and hard) are supported on NTFS, but are really quite a mess and not well documented: [http://www.shell-shocked.org/article.php?id=284](http://www.shell-shocked.org/article.php?id=284) has a good article including some of the dangers.

It's possible that Linux's use of NTFS has limitations that mean that hard links don't work well - e.g. some editors rename a file when editing it and save it under a new filename, but can work OK because they know about hard links.  If some part of this works differently with NTFS hard links, that could cause this sort of problem.

It may also be that there's an NTFS-3G bug (NTFS-3G is the Linux implementation of NTFS that's used by Ubuntu) - see [https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/199161](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/199161) which indicates that something to do with hard links was fixed in NTFS-3G.  However, before you go down that route, you need to find out exactly what's happening and get a simple set of shell commands that show the problem.

One basic question: do you really need more than one hard link to this file, particularly given NTFS's limitations?  Or is something creating the extra link 'under the covers' for you?

---

### Post by steavy on 2009-01-29
Ok im reading right now.

About your question: "do you really need more than one hard link to this file, particularly given NTFS's limitations?"

No I dont need more than one, actually I dont know where the second hard link come from. If I could I would remove the other hard link of every file in the ntfs partition. I made a search by name and only found one file, I dont know where the other hard link is or how to remove it.

---

### Post by jerome1232 on 2009-01-29
Another possibility from [http://www.ntfs-3g.org/support.html](http://www.ntfs-3g.org/support.html)

> Why can't I read or modify some files?
    NTFS supports built-in, transparent compression and encryption of files and directories on the file system level. Reading transparently compressed files are supported but writing of compressed and encrypted files is denied. Please note that compressed files, like .zip, .gz, .rar, etc, can be freely modified because they are compressed on the file, not on the file system level.

    Workaround: Uncompress or decrypt the files on Windows.

    Status: Sponsoring the development of this driver extension is possible. 

---

### Post by steavy on 2009-01-29
> **jerome1232 said:**
> Another possibility from [http://www.ntfs-3g.org/support.html](http://www.ntfs-3g.org/support.html)

Yeah maybe that could be a reason...my temporal solution will be moving all the php scripts to the linux partition...after all Im only having trouble with this files. But im still hopping other possible solutions :p

---

### Post by steavy on 2009-01-29
I forgot...thanks a lot both of you!

---

