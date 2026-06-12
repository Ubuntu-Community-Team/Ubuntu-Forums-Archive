---
title: "softlinked Desktop not working"
date: 2008-03-08
forum: Desktop Environments
---

### Post by Rigrig on 2008-03-08
I have a problem with my desktop:

I use libpam-encfs to encrypt a part of my home directory, I have a folder /home/richard/enc where the encrypted filesystem is mounted on login. This worked fine, so I moved folders I want to encrypt there, and soft-link to them from the original location:
```
richard@cc5337-a:~$ ls -l
total 20
drwxr-xr-x  7 richard richard 4096 2008-03-08 20:41 bin
**lrwxrwxrwx  1 richard richard   12 2008-03-08 21:07 [COLOR="Cyan"]Desktop[/COLOR] ->[COLOR="Blue"] enc/Desktop/[/COLOR]**
lrwxrwxrwx  1 richard richard   14 2008-03-08 20:01 documents -> enc/documents/
drwxr-xr-x  7 richard richard 8192 2008-03-08 20:46 enc
drwxr-xr-x 16 richard richard 4096 2007-09-03 13:25 www

```
The problem is that nautilus doesn't seem to get the Desktop link: My desktop displays the content of my home folder instead of my Desktop, also the 'Desktop' link in nautilus' places side pane takes me to my home folder, instead of the linked to folder.

Clicking the link works fine and takes me to the folder I want to use as desktop, and I've tried linking to '/home/richard/enc/Desktop', instead of the relative path.
I also moved+linked .evolution and .mozilla, and both Evolution and Firefox work fine.

Is there some way I can fix this, or is this a bug in nautilus?

**Edit:**
Solved it by editing ~/.config/user-dirs.dirs , somehow all entries were changed to "$HOME/".

---

