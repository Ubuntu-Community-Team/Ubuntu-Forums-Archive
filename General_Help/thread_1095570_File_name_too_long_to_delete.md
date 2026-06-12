---
title: "File name too long to delete"
date: 2009-03-13
forum: General Help
---

### Post by broozm on 2009-03-13
Even Ubuntu 8.10 can't fix ALL windows errors ?! ;)

I have an NTFS volume that I can mount OK and make changes and deletions on all files  - except I cannot get rid of one subdirectory because it is too long to rename or del or rmdir

Any ideas?

Error stating file '/media/vsbdc3/R/Cq/users/rdcl/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop
<SNIP 55 lines of the same (9 /Desktop !!!)>
/Desktop/Desktop': File name too long

---

### Post by circa82 on 2009-03-13
```
rm -rf <top directory to be deleted>
```

IE: If you wanted to remove the 'vsbdc3' folder and all subfolders, you would run:
```
rm -rf /media/vsbdc3
```

---

### Post by broozm on 2009-03-13
Thanks, the command does not show a failure - but it simply does not do the action.
I tried at two differing levels of the tree - and both do the same thing:

> 
bm@bm-desktop:/media/vsbdc3/R/Cq$ cd ..
bm@bm-desktop:/media/vsbdc3/R$ rm -rf /media/vsbdc3/R/Cq
bm@bm-desktop:/media/vsbdc3/R$ ls
Cq
bm@bm-desktop:/media/vsbdc3/R$ cd Cq
bm@bm-desktop:/media/vsbdc3/R/Cq$ ls
users
bm@bm-desktop:/media/vsbdc3/R/Cq$ cd users
bm@bm-desktop:/media/vsbdc3/R/Cq/users$ ls
rdcl
bm@bm-desktop:/media/vsbdc3/R/Cq/users$ cd rdcl
bm@bm-desktop:/media/vsbdc3/R/Cq/users/rdcl$ ls
Desktop
bm@bm-desktop:/media/vsbdc3/R/Cq/users/rdcl$ rm -rf Desktop
bm@bm-desktop:/media/vsbdc3/R/Cq/users/rdcl$ ls
Desktop
bm@bm-desktop:/media/vsbdc3/R/Cq/users/rdcl$ 


The error text posted before, was obtained from attempting a delete using the gui File Browser.

I also tried a verbose output - but still it shows nothing..:(
> 
bm@bm-desktop:/media/vsbdc3/R/Cq/users/rdcl$ rm -rfv Desktop
bm@bm-desktop:/media/vsbdc3/R/Cq/users/rdcl$ 


---

### Post by aesis05401 on 2009-03-13
If you remove the -force does it prompt you with any files for deletion at all or just fail silently?

I would also try sudo rmdir <dir> just to see if it failed silently as well - rmdir is only supposed to remove empty dirs and throw an error if !empty.

---

### Post by broozm on 2009-03-13
> **aesis05401 said:**
> If you remove the -force does it prompt you with any files for deletion at all or just fail silently?


Without the -force it does not prompt me and I get:

```
bm@bm-desktop:/media/vsbdc3/R/Cq/users/rdcl$ rm -rv Desktop
rm: cannot remove `Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Deskto
<SNIP (lots of /Desktop s)>
/Desktop/Desktop/Desktop': No such file or directory

```

> 
I would also try sudo rmdir <dir> just to see if it failed silently as well - rmdir is only supposed to remove empty dirs and throw an error if !empty.

this yields the same result (after prompting for my password)

I'M STUMPED
It's not a biggie as the file has no size so is not wasting space, but its irritating.
I might have to move the good data, then format it!?

---

### Post by aesis05401 on 2009-03-14
> **broozm said:**
> 
I'M STUMPED
It's not a biggie as the file has no size so is not wasting space, but its irritating.
I might have to move the good data, then format it!?

The file is zero size.  This sounds like a symbolic link issue.  

If you:
```

mkdir test
ln -s test test

```

/test will not be empty if you 'ls' it.  It will have contents /test/test.  If you 'stat /test/test' you should see the letter 'l' in the first perms position indicating it is a link file.  I wonder if the pathname is too long because something is looping out on a self-referencing link.

I'm gonna think about this a bit more, unfortunately I am not a Linux expert, but this one is kinda fun.

---

### Post by mb_webguy on 2009-03-14
Could you post the results of "ls -lsa /media/vsbdc3/R/Cq/users/rdcl/Desktop"?

---

### Post by broozm on 2009-03-14
> **aesis05401 said:**
> 
/test will not be empty if you 'ls' it.  It will have contents /test/test.  If you 'stat /test/test' you should see the letter 'l' in the first perms position indicating it is a link file.  I wonder if the 

```

bm@bm-desktop:/media/vsbdc3/R/Cq/users/rdcl$ stat test/test
  File: `test/test' -> `test'
  Size: 16        	Blocks: 1          IO Block: 4096   symbolic link
Device: 823h/2083d	Inode: 78681       Links: 1
Access: (0777/lrwxrwxrwx)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2009-03-14 22:27:23.000000000 +1300
Modify: 2009-03-14 22:27:23.000000000 +1300
Change: 2009-03-14 22:27:23.000000000 +1300

```

Yes, it shows an l

I think the issue is that the long subdir structure cannot be put into a variable holder in order to process it..

Now what

---

### Post by broozm on 2009-03-14
> **mb_webguy said:**
> Could you post the results of "ls -lsa /media/vsbdc3/R/Cq/users/rdcl/Desktop"?

```

ls -lsa /media/vsbdc3/R/Cq/users/rdcl/Desktop
total 4
0 drwxrwxrwx 1 root root    0 2008-04-19 21:46 .
4 drwxrwxrwx 1 root root 4096 2009-03-14 22:27 ..
0 drwxrwxrwx 1 root root    0 2008-04-19 21:46 Desktop

```

---

### Post by theozzlives on 2009-03-14
since it's on a Windows partition I would suggest some sort of malware causing this. I would run clamav from Ubuntu just to rule it out.  First mount the partition and look in /media to find out the mountpoint (normally /media/disk) , then:
```
sudo apt-get install clamav
``````
sudo mkdir /tmp/virus
``````
clamscan -ri --move=/tmp/virus <mountpoint>
```
Try that.

---

### Post by MIH1406 on 2009-03-14
I do not know why all this "Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop"?

---

### Post by broozm on 2009-03-14
```
clamscan -ri --move=/tmp/virus <mountpoint>
```
Try that.[/QUOTE]

Hmm - the scan seems to just hang and get no where - I can hear the disk accessing periodically - but have left it for 10 minutes or more.
What should I see on screen?

```

bm@bm-desktop:/$ clamscan -ri --move=/tmp/virus /media/vsbdc3
LibClamAV Warning: **************************************************
LibClamAV Warning: ***  The virus database is older than 7 days!  ***
LibClamAV Warning: ***   Please update it as soon as possible.    ***
LibClamAV Warning: **************************************************
flashing cursor here

```

I tried running the same scan on another device in another terminal window - but it does not even get as far as the first line of output :(

Do I need to sudo it?
How can I see the if the process is still alive?
ps shows me it appears to still be Running:

```

bm@bm-desktop:~$ ps -A r
  PID TTY      STAT   TIME COMMAND
 7583 pts/2    R+    22:03 clamscan -ri --move=/tmp/virus /media/vsbdc3
 7628 pts/1    R+    11:01 clamscan -ri --move=/tmp/virus /media/qsbdb2
 7639 pts/3    Rs     0:00 bash
 7660 pts/3    R+     0:00 ps -A r
bm@bm-desktop:~$ 

```

---

### Post by broozm on 2009-03-14
> **MIH1406 said:**
> I do not know why all this "Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop"?

This was data copied from a hard disk that was in a Windows Vista PC that was corrupted after doing an in-place upgrade of Vista Home to Vista Premium. I imaged the disk and copied data and this is a copy which I have never been able to get rid of.
And now that I have moved the disk to my new Ubuntu machine, I am tidying up, renaming volumes, creating an rsync between my two 320GB sata drives.

---

### Post by geirha on 2009-03-14
If the problem is that the path is too long, perhaps renaming each directory to a shorter name may allow all components to be stated ...

The following should recurse into all Desktop folders and rename each one to "d" as it goes.
```

cd /media/vsbdc3/R/Cq/users/rdcl/
while [ -e Desktop/ ]; do mv Desktop/ d/; cd d/; done

```

---

### Post by broozm on 2009-03-14
Scan completed OK:
```

----------- SCAN SUMMARY -----------
Known viruses: 465915
Engine version: 0.94.2
Scanned directories: 2420
Scanned files: 17956
Infected files: 0
Data scanned: 26591.03 MB
Time: 3290.459 sec (54 m 50 s)

```

---

### Post by lykwydchykyn on 2009-03-14
Seems like I had something similar happen once on an NTFS disk, it was just some kind of filesystem corruption that created an undeletable folder.  Have you run chkdsk /r on this disk (that's a windows recovery console command, not a LInux one)?  Might help, might not.

---

### Post by heindsight on 2009-03-14
Try this:
```
cd /media/vsbdc3/R/Cq/users/rdcl
find Desktop -depth -type d -empty -execdir rmdir \{\} \;
```

That will go find each directory under /media/vsbdc3/R/Cq/users/rdcl/Desktop. For each empty directory, it will effectively cd into the parent dir and then run rmdir to remove the empty directory. The -depth option forces find to process the contents of a directory before the directory itself. Thus effectively find will start rmdir-ing empty directories at the end of that chain of nested Desktop directories and work it's way up until they're all gone - Assuming they're all empty except for directories containing directories that is.

I know it's confusing, read the manual:
```
man find
```

If that doesn't work (perhaps some of those Desktop directories are not empty) you could do:
```
cd /media/vsbdc3/R/Cq/users/rdcl
find Desktop -depth -type d -execdir rm -Rf \{\} \;
```

---

### Post by broozm on 2009-03-14
> **geirha said:**
> If the problem is that the path is too long, perhaps renaming each directory to a shorter name may allow all components to be stated ...

The following should recurse into all Desktop folders and rename each one to "d" as it goes.
```

cd /media/vsbdc3/R/Cq/users/rdcl/
while [ -e Desktop/ ]; do mv Desktop/ d/; cd d/; done

```

DONE :)

A combination of renaming all subfolders to a short name and then rm got rid of them all!

The renaming command did not appear to complete, yet it did rename sufficient directories to allow the deletions.

Thanks everyone, I have learnt a bit from this

```


bm@bm-desktop:/media/vsbdc3/R/Cq/users/rdcl$ sudo rm -rv d
removed directory: `d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d/d'
.
.
.
.
removed directory: `d/d/d/d/d/d/d/d/d/d'
removed directory: `d/d/d/d/d/d/d/d/d'
removed directory: `d/d/d/d/d/d/d/d'
removed directory: `d/d/d/d/d/d/d'
removed directory: `d/d/d/d/d/d'
removed directory: `d/d/d/d/d'
removed directory: `d/d/d/d'
removed directory: `d/d/d'
removed directory: `d/d'
removed directory: `d'

bm@bm-desktop:/media/vsbdc3/R/Cq/users/rdcl$ ls
test
bm@bm-desktop:/media/vsbdc3/R/Cq/users/rdcl$ 


```

---

### Post by zigx on 2009-03-14
dang, that was a wild one!

glad to see you came out successful though!!

---

### Post by lisati on 2009-03-14
> **MIH1406 said:**
> I do not know why all this "Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop/Desktop"?

> **zigx said:**
> dang, that was a wild one!

glad to see you came out successful though!!
I agree! Well done for the success! 

I've occasionally had weird file names pop up like this - thankfully not often. They've usually turned out to be messed up pointers in the directory structure.

---

### Post by dingogray on 2012-12-21
> **broozm said:**
> Thanks, the command does not show a failure - but it simply does not do the action.
I tried at two differing levels of the tree - and both do the same thing:



The error text posted before, was obtained from attempting a delete using the gui File Browser.

I also tried a verbose output - but still it shows nothing..:(

Hey why don't you try"Long Path Tool" I am sure it help you.

---

### Post by nothingspecial on 2012-12-21
Old thread.

Closed.

---

