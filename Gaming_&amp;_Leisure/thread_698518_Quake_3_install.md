---
title: "Quake 3 install"
date: 2008-02-16
forum: Gaming &amp; Leisure
---

### Post by Tek-Noir on 2008-02-16
Hello, ive been using this guide to install Q3 to my pc.

[http://e-lime.vox.com/library/post/quake-3-on-ubuntu-edgy-x86_64.html](http://e-lime.vox.com/library/post/quake-3-on-ubuntu-edgy-x86_64.html)

 Everything is ok but i cant do step 5. I dont know what the command is to copy these to the Q3 directory is. 

If anyone could help id really appreciate it.

---

### Post by Tek-Noir on 2008-02-16
I think i need to change the permissions of the file im trying to copy to but dont know the command either.

---

### Post by RemmyLee on 2008-02-16
You can grab the Open Arena source and build a native 64 bit executable. While it will prevent you from playing on punkbuster servers, you can play on any of the others that aren't crc checking.

---

### Post by Tek-Noir on 2008-02-16
Cheers but just want to get this sorted first.

---

### Post by RemmyLee on 2008-02-16
Oh. you just need to copy them over? 

cp filenameA.ext /directory/where/it/should/go

Or better yet, just move them:

mv filenameA.ext filenameB.ext filenameC.ext /directory/where/it/should/go

To change permissions you [chmod]("http://en.wikipedia.org/wiki/Chmod") them.

---

