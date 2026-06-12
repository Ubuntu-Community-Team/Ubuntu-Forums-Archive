---
title: "Not able to copy file from one user directory to other user directory"
date: 2009-05-16
forum: General Help
---

### Post by bargi on 2009-05-16
Hi,

I am facing problem in copying file from one user directory to other user directory.

I have created two user account one bargi and other abc.
I am trying to copy file from bargi to abc but it giving following error:

> 
cp: cannot create regular file `/home/abc/a.txt': Permission denied



I tried changing owner but it was giving following error:

> 
chown: changing ownership of `/home/abc/a.txt': Operation not permitted


Can any body tell me how can I do this ?

Both bargi and abc are only user not root.
Thanks
Bargi

---

### Post by Old *ix Geek on 2009-05-16
```
sudo cp /home/bargi/a.txt /home/abc
```

You'll be prompted for your password.

After the file is copied, do this:
```
sudo chown abc /home/abc/a.txt
```

---

### Post by bargi on 2009-05-16
Can there be a way in which no root access is there..??
I mean to say that some how it can be possible that abc allows or permit bargi to copy file to his location ? 
Or any other sol. in which root access is not req. 

Thanks

---

### Post by Old *ix Geek on 2009-05-16
Yes, there are several ways.  Which one you choose depends on your specific situation.

For one, bargi can change the file's permissions to give everyone read/write access:
```
chmod 666 ~/abc.txt
```

and then abc can copy the file:
```
cp /home/bargi/abc.txt ~
```

If abc cannot read bargi's home directories and bargi doesn't want to let them, bargi can copy the file to some neutral location, such as /tmp and then abc can copy it from there.  Again, bargi needs to change its permissions before abc can copy it.

---

### Post by Carl Hamlin on 2009-05-16
The way I would do this is to create a group to which only bargi and abc belong, then let the group share ownership of both directories.

Here's how. Dots indicate responses from the system - just follow the prompts.

```

you@yourcomputer:~$ sudo addgroup bargiabc
...
you@yourcomputer:~$ sudo adduser bargi bargiabc
...
you@yourcomputer:~$ sudo adduser abc bargiabc
...
you@yourcomputer:~$ cd /home
you@yourcomputer:/home$ sudo chown bargi:bargiabc bargi
...
you@yourcomputer:/home$ sudo chown abc:bargiabc abc
...
you@yourcomputer:/home$ sudo chmod 770 bargi
you@yourcomputer:/home$ sudo chmod 770 abc

```

That ought to do it. From then on, both directories will be writable to both users, but nobody else.

---

