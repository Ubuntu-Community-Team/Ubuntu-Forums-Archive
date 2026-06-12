---
title: "LFS Using Wine."
date: 2007-02-26
forum: Gaming &amp; Leisure
---

### Post by Nitrofire on 2007-02-26
Anyone done it? I keep getting the error. Are you sure LFS is installed correctly on a Hard Drive (Or something along those lines)

---

### Post by houstonbofh on 2007-02-26
Did you look in the Wine App DB?  [http://appdb.winehq.org/appview.php?iVersionId=3755](http://appdb.winehq.org/appview.php?iVersionId=3755) shows some people doing it, and some things to try.

---

### Post by Nitrofire on 2007-02-26
I looked there. There is nothing about my problem of it complaining about the HDD. I don't know what i should doo :(

---

### Post by houstonbofh on 2007-02-26
What exactly is the error?

---

### Post by Nitrofire on 2007-02-26
Cannot Write to Data folder.

It wasn't saying that before!

---

### Post by houstonbofh on 2007-02-26
I assume you are running it from a terminal.  Cut and paste **everything** from the command until you get back to the command line.  Put it in code tags to keep the formatting.  And please don't make it so hard to help you.  More information is a good thing.

---

### Post by Nitrofire on 2007-02-26
```
mark@mark-laptop:~$ wine /home/mark/lfs/LFS.exe
mark@mark-laptop:~$

```

After this you get

---

### Post by houstonbofh on 2007-02-26
[http://www.lfsforum.net/archive/index.php/t-17569.html](http://www.lfsforum.net/archive/index.php/t-17569.html)
[http://forum.rscnet.org/showthread.php?t=77148](http://forum.rscnet.org/showthread.php?t=77148)
But most likely;
[http://ubuntuforums.org/showthread.php?t=79009](http://ubuntuforums.org/showthread.php?t=79009)

All these were found on Google with the search;
```
lfs "could not write to data folder"
```

---

### Post by TomMK on 2007-06-02
I got the same error message. I found the solution was to use the "cd" command in the terminal to go to the directory that LFS.exe is in first, **then** run it. So i do this:

> cd /home/tom/.wine/drive_c/lfs
wine LFS.exe

That solves it for me.

---

