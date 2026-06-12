---
title: "Files placed on Windows share get locked"
date: 2009-03-03
forum: General Help
---

### Post by stereomuffin on 2009-03-03
Every new file i create or copy on a windows share (Company NT domain) gets locked in Ubuntu. 
I can solve it by chmodding it but its annoying.

I use Likewise and have my Ubuntu machine hooked up to the domain, anyway who can help me with this problem? Much appreciated :KS

---

### Post by stereomuffin on 2009-03-10
anyone?

---

### Post by igor. on 2009-03-10
Take a look at the second post here: [http://ubuntuforums.org/showthread.php?t=373281](http://ubuntuforums.org/showthread.php?t=373281)

---

### Post by vginov on 2009-03-10
Add your windows user in samba server

---

### Post by stereomuffin on 2009-03-10
Thank you both! I will look at it tomorrow and post the result :D

---

### Post by stereomuffin on 2009-03-18
Well this is not working for me i'm afraid:

There is no samba-server, its a windows 2003 domain.
The other solution doesn't work either, perhaps cause there IS authentication going on. 

I'm clueless as to what to do here, any other ideas?
Just to add:

I use mount.cifs to connect to shares and i use my NT domain account to authenticate, all is good there. 

I find it odd that the files that get locked CAN be unlocked by me (using sudo chmod) by chmodding them?

This is an example from my /etc/rc.local file (i hear its better to use fsstab, but ok thats something else i guess)

sudo mount.cifs //fileserver.domain.nl/share/ /home/user/share -o user=<mydomain-account>,password='mypassword',domain=domain.nl

Any thought why my files placed on this mounted share gets locked?

Thank you all!

---

### Post by igor. on 2009-03-19
So you have a Windows 2003 server with file sharing. You connect ubuntu to this. The files get locked.

In what way are the files locked? Can ubuntu not access them or windows or both? What are the exact file permissions on those files?

---

### Post by stereomuffin on 2009-03-23
> **igor. said:**
> So you have a Windows 2003 server with file sharing. You connect ubuntu to this. The files get locked.

In what way are the files locked? Can ubuntu not access them or windows or both? What are the exact file permissions on those files?

Thanks igor, the permissions are as followed:

-rw-r--r-- 1 root root 106496 2009-03-23 11:51 document.doc

To be exact: the file is not actually locked under Windows (when i try to access it from a windows PC its writable and not locked) its only locked for me as a user on my ubuntu system (i log into ubuntu using my domain account, this was accomplished by using Likewise to add my system to the domain) 

So i can just chmod the file as root and its fixed, but i want the file created on the share to have default permissions that allow me to edit it after. and not having to chmod every time.

Any ideas? :)

EDIT: 

just to add, that if i place a file on the share and i 'umount' the share and remount it, the lock is gone. 
i tried removing the word sudo from my sudo mount.cifs lines in /etc/rc.local but that doesn solve it either.

---

### Post by stereomuffin on 2009-03-23
It is fixed! 
Added 'noperm' to the end of each mount.cifs line, remounted everything and now my issue is solved :popcorn:
For anyone else experiencing a problem similar in the future and who ends up here :p : this is what my mount.cifs line in my /etc/rc.local file looks like now:

mount.cifs //fileserver.domain.nl/myshare /home/stereomuffin/myremoteshare -o user=<domain username>,password='mypassword',domain=domain.nl,noperm

---

