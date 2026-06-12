---
title: "permissions for external hard drive"
date: 2009-01-09
forum: General Help
---

### Post by kaarnijoki on 2009-01-09
Hello everybody.:D

 Got a bit stuck here. Maybe someone knows what to do?

 Extracted a hard drive from my old mac (rip) and desperately trying to get to my music that is being stored in there. Sudo nautilus gives access to them and i can see what there is and am able to play them with Amarok. However i want to copy them to my internal hard drive which does not work because of permissions which i cannot change. Tried in shell with chmod with no success.

 Getting: chmod: changing permissions of `file': Read-only file system

What shall i try next? 

Thank you. Hope You all are keeping warm. Freezing in here. Sunny ol England..


Thanks again

Pasi

---

### Post by heindsight on 2009-01-09
You don't need write permission on the external drive to be able to copy files from it. If you can read the files, you can copy them. If you can't access read the files using your normal user account, you could copy them as root.
for example, assuming your external drive is mounted at /media/disk and the music is all in /media/disk/music, and you want to put the music in the Music directory in your home dir (and assuming that your username is kaarnijoki) you could do:
```
cd
sudo cp -R /media/disk/music/ Music
sudo chown -R kaarnijoki:kaarnijoki Music

```

after copying you may want to change the permissions of the files you copied. You can use find the -perm option of the find command to search for files or directories with 'incorrect' permissions and use the -exec option to change permissions for those files

---

### Post by kaarnijoki on 2009-01-10
Many thanks Heindsight.

Will give it a go.

Live long and prosper.

---

### Post by heindsight on 2009-01-10
> **kaarnijoki said:**
> Many thanks Heindsight.

Will give it a go.

Live long and prosper.

You're welcome.

May the source be with you ;)

---

