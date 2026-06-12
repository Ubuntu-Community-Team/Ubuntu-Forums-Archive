---
title: "easy 2-way synchronizing, over internet?"
date: 2006-08-17
forum: Desktop Environments
---

### Post by 1002285 on 2006-08-17
I've been reading about synchronizing apps for some time now, but I still don't feel like I have understood everything I have wanted to know.
What I want is to back up my files, but backing up is not the only objective. I also want to have some of the files I work with in both of the computers I have, so I would rather use two computers than an external drive. The computers are not always in a single house (but when they are, they are in the same wifi area).
They are two laptops, one running Dapper and /home is in ext3 and on the other one I run Edgy and the partition for documents is in FAT32 (didn't know about ext driver for Windows then).
I'd like to be able to let a program know which directories I want to be in sync, and that it would remember these settings, and it would be really great to be able to do it from another city over internet.
Can jfilesync or grsync or anything else do all that?

---

### Post by it.henrik on 2006-08-17
if one of the computers is running 24/7 then I would reccomend sshfs for the job.

With sshfs you can mount a ssh-account on your local filesystem. you wont get two copies but always the same files.

---

### Post by 1002285 on 2006-08-17
> **it.henrik said:**
> if one of the computers is running 24/7 then I would reccomend sshfs for the job.
None of the computers are on all the time. Why is that important?
Anyway, I guess the first thing to get to know might be samba or sth like that. Because so far I can't even open files on the other computer.
I will try and read about that, too.

---

### Post by it.henrik on 2006-08-17
well .. 24/7 isnt as important as that they need to be on when ever you want to use the files that should be the same on both computers. 

ssh is a secure way of doing things like samba can do.If you dont know it I recommend you get to know it .. its very usefull :)

ssh is used to remotely connect to another machine and control it .. with sshfs you just get all the file manipulation-thingies in a nice wrapped package. 

Good luck and please post back here when you found a solution you like .. cause I might want to start doing things that way instead then :P

---

### Post by 1002285 on 2006-08-17
> **it.henrik said:**
> well .. 24/7 isnt as important as that they need to be on when ever you want to use the files that should be the same on both computers. 

I will try and learn about sshfs.
But about the 24/7, still: Can't I just work with a file on one computer, without having the other computer connected, and synchronize them later?
Having one computer on all the time is not a good option for me.

---

### Post by 1002285 on 2006-08-17
So if I have in my "locations" menu (gnome, second menu in the upper toolbar, whatever it is called in English, I have Ubuntu in Estonian) options like "network servers" and "connect to a server" - do I understand correctly, that the first one is there because of samba and the second one because of sshfs?
It seems that sshfs wants one computer, or at least something, to be a server, and samba is like Windows's "My network places", and it even calls the network "Windows network".
I still haven't figured much of it out, but will keep trying ...

---

### Post by it.henrik on 2006-08-17
SAMBA = windows network "for linux". 
SSH = encrypted control another computer over network
SSHFS = SSH but only operations on files, in a way that makes the remote file system look like a part of the local file system.

If you want to sync the files only when both computers get online at the same time then neither of these will do that for you.

The only other way of synch. files that I have used is CVS .. but that might be a bit over kill for your need.

---

### Post by N6546R on 2006-08-17
The classic way is with rsync. Here's a pointer: [http://www.jdmz.net/ssh/](http://www.jdmz.net/ssh/)

Perry


> **1002285 said:**
> I've been reading about synchronizing apps for some time now, but I still don't feel like I have understood everything I have wanted to know.
What I want is to back up my files, but backing up is not the only objective. I also want to have some of the files I work with in both of the computers I have, so I would rather use two computers than an external drive. The computers are not always in a single house (but when they are, they are in the same wifi area).
They are two laptops, one running Dapper and /home is in ext3 and on the other one I run Edgy and the partition for documents is in FAT32 (didn't know about ext driver for Windows then).
I'd like to be able to let a program know which directories I want to be in sync, and that it would remember these settings, and it would be really great to be able to do it from another city over internet.
Can jfilesync or grsync or anything else do all that?

---

### Post by anthro398 on 2006-08-17
I also do this.  I have a desktop at work, one at home, and a laptop.  I try to keep my work documents synced on my work desktop and my laptop and my some of my personal documents synced between my home desktop and laptop.  I'm sure there are some fancy gui applications to do this, but I've written some little bash scripts to call rsync to perform the syncs.

rsync can use ssh as a transport medium, but I mount the remote drive over samba and use rsync to sync the two local disks.  I think it was just simpler to do it that way when I was first learning bash and rsync, but it wouldn't be difficult to use it remotely over ssh.  You'll have to run two process- one to sync the local disk to the remote disk and one to sync the remote disk to the local disk.  rsync is very smart and that makes it much quicker than a simple copy.

The only complication is when you reorganize one of the directories.  Then you'll want to use the --delete flag.  So, I use it like so:
```
rsync -avv Documents/ /mnt/work/Documents/ 
```
Then you could run the reverse:
```
rsync -avv /mnt/work/Documents/ Documents/ 
```

The --dry-run flag is your friend until you're sure of what you're doing.  It takes a bit to get confident about ending slashes and the like.  At that point, it's nice to put the commands into a script and put an alias in .bash_aliases so you can just say something like: 
```
me@localhost:~$ sync_laptop
```

At least, that's how I do it.

---

### Post by 1002285 on 2006-08-17
> **anthro398 said:**
> 
rsync can use ssh as a transport medium, but I mount the remote drive over samba and use rsync to sync the two local disks.  I think it was just simpler to do it that way when I was first learning bash and rsync, but it wouldn't be difficult to use it remotely over ssh.  You'll have to run two process- one to sync the local disk to the remote disk and one to sync the remote disk to the local disk.  rsync is very smart and that makes it much quicker than a simple copy.
Thank you very much, I did feel for a moment that I got the idea vaguely, but I guess I really don't understand. I don't know how to mount the other computer over samba. Samba only shows me Windows network, which I don't want at all.
But I will try and learn about it all again tomorrow. The problem is that when you don't understand things at all and you  have work to do you only get to spend some hours or half a day on a weekend most for getting a new thing to work. It wasn't enought for me today.
But I am still grateful.

---

