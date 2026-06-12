---
title: "Wrong icons in &quot;Places&quot;.  Though, the icons exist."
date: 2008-12-05
forum: Desktop Environments
---

### Post by qetuR on 2008-12-05
Hi! 

I have a problem that I don't know how to  get around, seems like a simple problem. And the easiest way to describe it is through showing  you a picture of it.

[http://img518.imageshack.us/my.php?image=skrmbild1fy6.png](http://img518.imageshack.us/my.php?image=skrmbild1fy6.png)

See the "Platser" the top icon is right, the blueone that is my home folder. But the rest is grey. The strange thing is that in nautilus, the icons are right, and in bookmarks in also right.

Anyone know how to get around this problem?

Some icon themes can change this ie. the basic icon thems that comes with ubuntu from start. 

Help is very apriciated!

---

### Post by centyx on 2009-01-23
You need to create a symbolic link in the places folder from folder.{svg,png} to inode-directory.{svg,png} then reload the icon theme ( ie. change icon sets to something else then back again ).

This worked for me.

---

### Post by centyx on 2009-01-23
Sorry, was in a hurry. Here's a little more detailed instructions:

You need to create a symlink for inode-directory.{png,svg} in places:

```

cd /usr/share/icons/<iconset>/scalable/places/
ln -s folder.svg inode-directory.svg

```

Now switch icon set to something else and back again.

---

