---
title: "No permissions to edit id3 tags with easy tag"
date: 2005-12-24
forum: Desktop Environments
---

### Post by dcast on 2005-12-24
Hi, I have some mp3s which I copied over to my comp from a cd ( not ripped just copied) anyway some of the tags aren't all there so I installed easytag however when I try to change a tag it says I don't have permissions. I have root permissions to the folder with the music however some of the tracks have a little lock next to them in the folder. How can I change this?

thanks,
         Dcast

---

### Post by Sutekh on 2005-12-24
[QUOTE=dcast]I have root permissions to the folder with the music [/QUOTE]

What do you mean by root permissions, because to me that means that 'root' owns the files, which is why you don't have permission to change them as your user.

The little lock means that the owner of the files doesn't have write permission.

Go to a folder that has files that you can't change the tags of and
```
ls -l
```
Paste a snippet of that output so we can see what the permissions are for those files.

Something like this (one file is enough)
```
-rwx------  1 user user 5570560 2005-09-04 15:54 Orbital - The Middle of Nowhere - Track 05 - Otono.mp3

```

This particular file is owned by 'user', and the group ownership belongs to the group 'user'.  The permissions -rwx------ mean that 'user' has read, write and execute permissions to the file, but the group owner and exeryone else has no access.  If you're files have a little lock then the 'w' is probably missing.

---

### Post by ardchoille on 2005-12-24
I would agree with Sutekh on this one. You can gain write perms on those files by doing the following:

```

chmod u+w /path/to/mp3_files/*.mp3

```

That will make all .mp3 files in that dir writable by your user.

---

