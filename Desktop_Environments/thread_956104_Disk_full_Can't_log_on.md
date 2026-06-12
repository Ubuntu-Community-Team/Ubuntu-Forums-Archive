---
title: "Disk full Can't log on"
date: 2008-10-22
forum: Desktop Environments
---

### Post by alex_kde on 2008-10-22
Hi,

don't know how, but yesterday I couldn't log on, so I boot with the live disk, and see the disk is full, but can't delete any file cause of the permitions.

I don't know how to recover disk space, the Ubunt start fine but Can't log on.

I will appreciate any conment to lead my find a solution.

TIA,

Alex.

---

### Post by kilroy423 on 2008-10-23
> but can't delete any file cause of the permitions.

You should be able to gain root on the live cd and be able to clear out some files.

```
sudo su
```

> I don't know how to recover disk space, the Ubunt start fine but Can't log on.

```

mount /dev/DISKPARTITIONNUMBER MOUNTPOINT
df -h
rm -rf filename

```

you would have to mount the disk first 
df -h will let you know the disk usage of mounted file systems
rm -rf will delete files, careful

---

### Post by pirattrev on 2008-10-23
this happened to me.  Xserver and the graphics try to write new session files each time you log in.  If you get an error just switch into tty mode and i think you should be able to navigate and delete some files (assuming that you aren't _that_ precariously close to being completely full. However I have my / partition as separate from the /home so logging in was only a /home issue of being full due to torrents, and complete overload wasn't an issue because i still had 4 gigs free on my / partition.  

so my solution: try the tty first because it'll be less time consuming then the live cd (or alt will work as well). 
*note: to get to tty mode after a failure to login, just hit ctrl-alt-f1 and you'll boot into tty1 and just enter your 'username' and 'password' to log in via commandline. To delete stuffs just "cd" to different directories and "rm" stuff (rm --help to learn how to use it)

---

### Post by alex_kde on 2008-10-25
Hi,

now, say thank you very much for your help.

I was too busy until now to fix this trouble. 

your comments help me a lot.

Alex.

---

### Post by 4lc0h0l1c on 2008-10-28
Hi,
This just happened to me but now my KDE doesn't work at all!  I used the tty to clear out some files because my disk is full but when I log in to KDE I get nothing but a shell window.  If I run kicker it appears but doesn't function correctly.  If I run Opera from the shell and then exit Opera I can't type anything in the terminal. And things like alt+f2 don't run.  Like the KDE conf is all wrong!  I reinstalled KDE and it didn't help

Edit:
I fixed it.  This problem came about when I was compiling Qt4 for a program that needed it.  My computer ran out of space in the middle of this process.  Although I deleted the build directories, it wasn't enough.  I restarted my computer and was unable to log in to KDE because I hadn't freed up enough space.  I just used synaptic to install Qt4-dev-tools and the next time I tried to log in to KDE everything appeared as normal (except my konsole colors are reset...maybe because at one point I used synaptic to "completely remove" KDE?)

This is a kind of useless post as pertaining to OT but perhaps in future if someone else does the same thing it will help

---

### Post by tmetzcc325 on 2008-12-30
Hey there, I am having a similar problem, but I can't log in at all, even after clearing up disk space.  Might one of you possibly take a look at this thread?

[http://ubuntuforums.org/showthread.php?t=1019591](http://ubuntuforums.org/showthread.php?t=1019591)

Thanks a bunch,
Tom

---

