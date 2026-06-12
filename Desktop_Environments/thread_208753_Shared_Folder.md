---
title: "Shared Folder"
date: 2006-07-04
forum: Desktop Environments
---

### Post by john_markh on 2006-07-04
Hi all :KS ,
I want to create a local shared folder so every user using computer localy (not SMB) could read/write in that directory. Also, files copied by some user will be availble to all.
Any way of doing it ?

---

### Post by gatiba on 2006-07-04
Why not?
Just open a terminal then type this to create a new folder in /home:

```
sudo mkdir /home/shared
```

Then give it read/write permission for all users:

```
sudo chmod 777 /home/shared
```

So all the users will read/copy the files in it!

---

### Post by john_markh on 2006-07-04
Thanks!
I kind of figure out a first step, but :
[LIST]
[*]What is 777 means ?
[*]When user will create his own sub folder, will it still be accessble for all users ?
[/LIST]

---

### Post by aysiu on 2006-07-04
The default behavior in Ubuntu is 644--meaning that everyone can read the file but only the owner (creator) of the file can write to it or modify it.

This can be annoying with shared files. You can change them to 775 if you want, but then the next time you create a new file, it will be 644 again until you change it again manually.

[There's a solution to this problem, but it's a bit convoluted](http://www.ubuntuforums.org/showpost.php?p=832721&postcount=9). I'm not sure how much you want to invest in this process.

---

