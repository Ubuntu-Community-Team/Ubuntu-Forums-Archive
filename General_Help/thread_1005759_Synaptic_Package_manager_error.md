---
title: "Synaptic Package manager error"
date: 2008-12-08
forum: General Help
---

### Post by alisaleh on 2008-12-08
I tried to open the Synaptic Package manager but this error appeared to me
plz help:

E: Unable to write mmap - msync (28 No space left on device)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by Peter09 on 2008-12-08
Can you post the output of the terminal command

```
df -h
```

Terminal Basics
To make life easier when using the terminal:
1. The up and down arrow keys allow you to move through the command history of the terminal. So if you make a mistake in a command the up arrow will return to it, you can the edit the command using the left/right arrows and the del/backspace keys. Hit enter when you are ready to re-issue.

2. Hitting the TAB key when you are in the middle of typing a command makes the terminal attempt to autocomplete the command/filename that you are typing.  Hitting the TAB key twice displays all the options available for autocompletion.

---

### Post by alisaleh on 2008-12-11
Hello petr
this is the output of the terminal command.I think that this means that I need to increase the space for the file system on sda7.

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             3.3G  3.3G     0 100% /
tmpfs                1008M     0 1008M   0% /lib/init/rw
varrun               1008M  192K 1008M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M  2.8M 1005M   1% /dev
tmpfs                1008M  104K 1008M   1% /dev/shm
lrm                  1008M  2.0M 1006M   1% /lib/modules/2.6.27-9-generic/volatile
overflow              1.0M   32K  992K   4% /tmp

---

### Post by Peter09 on 2008-12-11
Yes, your file system is 100% full. Check your waste basket is empty. There is a utility which will graphically check your disk space - I think its in applications->accessories (I have not got it installed on this machine).

You may have additional kernels that you do not want as well.

---

### Post by alisaleh on 2008-12-12
Thank you very much I want to increase the file system size.Is there a partition magic like software on Ubuntu?
thanks again.

---

### Post by devil404 on 2008-12-12
> **alisaleh said:**
> Thank you very much I want to increase the file system size.Is there a partition magic like software on Ubuntu?
thanks again.

There sure is. It's called [FONT=Courier New]gparted[/FONT]. I'd instruct you to install it, but you don't have any disk space to install it to. Perhaps you should use an Ubuntu livecd to boot into. It has that tool as part of the installation environment.

---

### Post by drs305 on 2008-12-12
You can probably free up some space by getting rid of hidden trash files. This link tells you how to find and delete these files, as well as some other things to free up enough space to install gparted.

[Disk Full? - Check Your Trash Bin(s)]("http://ubuntuforums.org/showthread.php?t=898573")

---

