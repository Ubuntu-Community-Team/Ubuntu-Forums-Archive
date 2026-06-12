---
title: "Sticky bit permissions etc."
date: 2009-03-12
forum: General Help
---

### Post by Kismet on 2009-03-12
Alright, I've searched alot, and played with sticky bits, but I still do not understand how they work and what they are supposed to do.

Here is what I want, if anyone can tell me if its possible/and how, I would greatly appreciate it. 

I want a directory that ANY file created by ANY user HAS A predefined owner and set of permissions.

ie 

```
bob$ touch test.txt
bob$ ls -lh
-rwxrwxrwx ? somebody somebody ... test.txt

joe$ touch test2.txt
joe$ ls -lh
-rwxrwxrwx ? somebody somebody ... test.txt
-rwxrwxrwx ? somebody somebody ... test2.txt

```

So no matter who creates/modifies the files in said directory, they always have the same owner/group and permissions?

Is this possible?

Any advice is appreciated.

---

### Post by kidders on 2009-03-13
Hi there,

> **Kismet said:**
> So no matter who creates/modifies the files in said directory, they always have the same owner/group and permissions?

Is this possible?In a word... no. If that were possible, the idea of ownership wouldn't be very useful. Additionally, permissions are set by the creator's umask ... they are not inherited from the parent directory.

The sticky bit allows you to prevent users that would otherwise be allowed to delete or rename files from doing so. It doesn't have anything to do with altering file ownership. You may be confusing it with the SGID bit. When applied to directories, it allows you to specify the default group that owns newly created files. It's mainly intended as a convenience, so it's easier for different members of the same group (that don't necessarily share the same primary group) to create files with sensible default access controls.

I hope that helps.

---

### Post by dandaman0061 on 2009-03-30
Look in to Access Control Lists...  I haven't used them extensively, so I can't say too much.

setfacl
getfacl

[http://www.cs.indiana.edu/Facilities/FAQ/General/ACL.html]("http://www.cs.indiana.edu/Facilities/FAQ/General/ACL.html")

If anyone more informed has criticism/comments on their use, I'd be interested.

Danny G

---

