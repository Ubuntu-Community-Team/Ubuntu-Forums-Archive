---
title: "keeping old HDDs, reinstall issues?"
date: 2009-01-27
forum: General Help
---

### Post by shortridge11 on 2009-01-27
Hey all,

I decided to reinstall because i had a lot of older stuff on my machine i wanted to get rid of/i enjoy reinstalling every now and then.  This machine was my file server and i was running desktop on it.  Before you say "why desktop on your server?!", it's because i need a gui for some of the things i do, and i like being able to vnc in to show off to people.  Anyways, I've got my 6 harddrives (internal) plugged in, and I'm not sure what to do with them.  i just used pysdm (or psydm, can't remember) to automount them.  I've been told /media is a terrible place to mount my harddrives, and so i guess i'll mount them elsewhere this time.  Should i create a user and make it accessible to everyone and then mount them in his home folder? 
ie: /home/server_user/mounted_drives

also,  Any advice on maintaining a working server by managing things through user names (creating a user specifically for ftp, ssh, samba, etc) will be very welcome.  I've heard you can do that, and that seems to be a bit more secure then the standard way of using your normal account (not root) to do everything.

Cheers

---

### Post by hyper_ch on 2009-01-27
why is it a terrible place to mount them in /media?

---

### Post by shortridge11 on 2009-01-27
[http://ubuntuforums.org/showthread.php?t=1032347](http://ubuntuforums.org/showthread.php?t=1032347)

That is why

---

### Post by sedawk on 2009-01-27
This might not be state-of-the-art, but when operating a file server
you might think about creating a directory /export and mount every
file system in a subdirectory there, e.g. /export/music, /export/videos,
/export/data, etc.

If your file server (NFS/Samba/FTP) is used by many people
and you want to have normal security (e.g. User A cannot always
see everything from user B) there might not be an alternative
to run all services as root, so the daemons running
can change the owner and groups of files on the file server
according to the configuration.

---

### Post by shortridge11 on 2009-01-27
Should this directory be created in a user's home folder? or just in the filesystem?

I'm just trying to make sure i go by the book, or what won't break my install or look really stupid.

---

### Post by hyper_ch on 2009-01-27
I still don't see anything wrong with mounting it in /media...

---

### Post by shortridge11 on 2009-01-27
really? i guess i was told wrong then?

i think their main point was that it messed with things that were supposed to automount?

---

### Post by mb_webguy on 2009-01-27
The /media directory is specifically for removable media, and mounting non-removable volumes there will cause problems.  The /mnt directory is for temporarily mounted non-removable volumes according to [filesystem hierarchy standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard"), though unlike the /media directory there's no inherent problem to mounting volumes there permanently as far as I know.  Permanently mounted volumes can, of course, be put anywhere else if it makes sense to do so.  But the system will treat anything mounted in /media as removable storage, whether it actually is or not.

---

### Post by jerome1232 on 2009-01-27
What's the problem with mounting volumes under /media?


If I have something mounted at /media/backup, and I plug in my removable drive which happens to be labeled "backup" it auto-mounts to /media/backup_, if that exists /media/backup__ and so on.

There's no conflict happening the auto mounting system handles it very well.

---

### Post by hyper_ch on 2009-01-28
and what does it make different if the system treats something as "removable storage" and "non-removable storage"? Where is there the difference?

---

### Post by shortridge11 on 2009-01-30
I ended up mounting these with the fstab by their UUID, and i mounted them in media.  One of my harddrives was bad though, and when it was plugged in the machine wouldn't even get to the grub.  It wasn't trying to load from it, because i disabled it in the bios so that it only read from the hd that had the OS on it.  Any ideas on how to figure out what's wrong with it?  No computer i've tried will boot with it on, but i think i tested it with smartmontools before it started acting up and it was fine.  It was buggy before, as in random data would disappear from the HD, and it still passed the smartmontools tests, but now i can't test it because no machine will start up with it attached. any ideas?

---

