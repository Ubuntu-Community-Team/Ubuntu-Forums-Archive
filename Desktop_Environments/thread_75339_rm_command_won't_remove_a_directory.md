---
title: "rm command won't remove a directory"
date: 2005-10-13
forum: Desktop Environments
---

### Post by MuRRe on 2005-10-13
Cant remove folder even when root in terminal. It say:
root@aspire5024:/home/murre/Desktop# ls
80211g
root@aspire5024:/home/murre/Desktop# rm 80211g
rm: cannot remove `80211g': Is a directory

---

### Post by drogoh on 2005-10-13
rmdir to remove empty directories.

'rm' is just for single or multiple files, not for directories.  You need to use the -r flag for recursive.

---

### Post by aysiu on 2005-10-13
Maybe try ```
sudo rm -r 80211g
```

**Edit:** Drogoh beat me to it.

---

### Post by MuRRe on 2005-10-13
Is their a website with a command list for the Terminal (see how im NOT using "DOS" looking thingy anymore, lol)
And by tthe way i cant acces my NTFS. I could acces my FAT32 but it says i dont have permission on my NTFS.

---

### Post by aysiu on 2005-10-13
There are many websites with Linux commands. Do a Google search.

If you want to know more about how to use a particular command, use *man*. For example, let's say you want to know more about *ls*. Type ```
man ls
``` in the terminal. As long as there's a manual for it, it'll list instructions for you.

[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

---

### Post by zeroverse on 2005-10-13
[QUOTE=MuRRe]Is their a website with a command list for the Terminal (see how im NOT using "DOS" looking thingy anymore, lol)
And by tthe way i cant acces my NTFS. I could acces my FAT32 but it says i dont have permission on my NTFS.[/QUOTE]

[http://linuxcommand.org/](http://linuxcommand.org/)

To access ntfs, read this: [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

EDIT: oops, redundant.

---

### Post by kustomjs on 2007-11-15
or to take out the whole program and directory is apt-get remove program

---

