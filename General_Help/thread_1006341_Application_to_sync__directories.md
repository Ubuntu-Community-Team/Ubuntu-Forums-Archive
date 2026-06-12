---
title: "Application to sync  directories"
date: 2008-12-09
forum: General Help
---

### Post by Aseld on 2008-12-09
Greetings, and I hope this is in the right forum (It's very late, I'm tired, and the forum structure confuses me :P).

I want to have certain directories sync, in a particular way; I want files added to any one directory automatically added to all. The apps that I have investigated don't do that. 

Is there a utility extant that will do this, or should I just stop being such a lazy ******* and write my own?

Thanks, 
sio

---

### Post by kevdog on 2008-12-09
Whats wrong with unison or rsync?

---

### Post by Vadi on 2008-12-09
If it's between different computers, dropbox works too.

Otherwise... right-click, "Make Link".

---

### Post by Metallion on 2008-12-09
> **kevdog said:**
> Whats wrong with unison or rsync?

Can rsync be set up to constantly monitor a number of directories and keep them in sync whenever a change is made? I'd love to know how if it can :D

---

### Post by fjf on 2008-12-09
The gnome interface for rsync is called grsync.  Works very nicely.

---

### Post by hessiess on 2008-12-09
Unison, works both ways. Though I would like to find a way to run it automatically whenever there is a change in the filesystem.

---

### Post by sysop on 2008-12-09
I've used a program called DirSyncPro with good success under Ubuntu. It has command line options for various profiles and I script it to run various profiles daily. (Needs Java Runtime)

[http://sourceforge.net/projects/dirsyncpro/]("http://sourceforge.net/projects/dirsyncpro/")

---

### Post by JohnFH on 2008-12-09
Does anyone actually read forum posts anymore?

rsync by itself won't work because it doesn't monitor filesystem changes.  However combining the use of rsync with incron should keep two directories in sync.  

```
incrontab -t
```
will display the list of system events it recognises.

```
/home/me/dir-to-monitor IN_WRITE_CLOSE /home/me/rsync-script $# 
```
is an example of an incrontab entry which will result in the rsync-script being run if a file in the directory dir-to-monitor changes.  the rsync-script can then be used to sync the recent change to another directory.

Having said all that, if all you want it for is to backup something, I wouldn't bother with incron.  Just setup the rsync script to run periodically.  If it's not for backup use and you don't need two copies of the same file then you can mount the same directory in two places (see mount command).  That's an easy solution that also saves disk space.

---

