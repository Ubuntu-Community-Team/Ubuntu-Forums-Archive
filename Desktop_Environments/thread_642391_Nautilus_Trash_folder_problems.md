---
title: "Nautilus Trash folder problems"
date: 2007-12-16
forum: Desktop Environments
---

### Post by ifireball on 2007-12-16
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/176755](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/176755) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've recently came across some problems when trying to use the Nautilus "Trash" folder with files that reside on a disk other then the one where my home folder is.

To cut a long story short, if you get the following error message from Nautilus:
```
Cannot move file to trash do you want to delete immediately?
```
And you'd rather Trash would work rather then delete the file you should simply create a directory called ".Trash-<username>" (Replace <username> with your desktop user name) in the file system's root directory with the following commands:
```
sudo mkdir /your/filesystem/mount/point/.Trash-<username>
sudo chown <username>:<username> /your/filesystem/mount/point/.Trash-<username>
```

This is probably related to the following  thread:
[http://ubuntuforums.org/showthread.php?t=103460](http://ubuntuforums.org/showthread.php?t=103460)

I've posted a detailed description of the problem and how I managed to solve it here:
[http://http://ifireball.wordpress.com/2007/12/13/fixing-the-nautilus-garbage-bin/](http://http://ifireball.wordpress.com/2007/12/13/fixing-the-nautilus-garbage-bin/)

I've also opened the related bug [#176755]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/176755").

I hope this helps other people who may come across this problem.

---

