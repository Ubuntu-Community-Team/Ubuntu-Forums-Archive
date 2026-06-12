---
title: "Cannot burn CD"
date: 2005-12-21
forum: General Help
---

### Post by ubuntu27 on 2005-12-21
Hello all :)

Today I tried to burn a CD using Nautiln.  I get this: 

[[IMG]http://img478.imageshack.us/img478/2943/nautiluscdburner6nj.png[/IMG]](http://imageshack.us)

I'm tryng to burn a Data CD. Files contains Zip, and Jpeg. Some of then are Doc and odt. and.. yeah, some of those files contain Japanese character... hope it dosn't have to do with anything.

I'm using Memorex CD-R 700MB. 

Have any ideas?

---

### Post by schilcha on 2005-12-21
Seems, as if your tmp-disk-space is full. Check your free disk space.

---

### Post by ubuntu27 on 2005-12-21
[QUOTE=schilcha]Seems, as if your tmp-disk-space is full. Check your free disk space.[/QUOTE]
Oh nO! I need some HD space in order to burn CD? >< Now I'm doomed.

Check this thread: [http://ubuntuforums.org/showthread.php?t=106566](http://ubuntuforums.org/showthread.php?t=106566)

I'm out of space :(

Now what should I do?

---

### Post by schilcha on 2005-12-21
[QUOTE=ubuntu27]Oh nO! I need some HD space in order to burn CD? >< Now I'm doomed.[/QUOTE]

Just to make things clear: You want to free some space from your linux-partition by burning stuff to cd? But you can't burn, since you don't have enough space to create the cd-image.

You can try two things:
Free up some space by deleting unnecessary stuff, e.g. from /tmp (this is done on startup by default), /var (maybe you have loads of logs), browser-cache, mail-folders, ...
Burn linux-stuff from windows. I know there are tools for windows to access ext3-partitions (at least to read them). However I don't know them, since I don't have windows.

Good Luck!

---

