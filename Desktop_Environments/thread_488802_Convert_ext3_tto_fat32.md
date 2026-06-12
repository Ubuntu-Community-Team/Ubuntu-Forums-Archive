---
title: "Convert ext3 tto fat32"
date: 2007-06-30
forum: Desktop Environments
---

### Post by Magiczero on 2007-06-30
Hi

I have 2 drives in my ubuntu system.  Soon I am buying a dell with Vista & my 2nnd drive is a ext3 file system right now.  I need to convert my 2nd drive so Vista can read it.   Can I just convert it as a FAT32 file system?

Thanks

---

### Post by jimbob on 2007-06-30
I do not believe you can just convert it to a different file system.

You're probably going to have to delete it and re-create it as the file system type you want.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by Freddy on 2007-07-01
Don't use FAT32, it's ugly, instead format you drive with ext3 and use [http://www.fs-driver.org/](http://www.fs-driver.org/) from windows to mount it as ext2. It's bit tricky to install this from Vista, but if you rightclick the .exe and go to properties, you can emulate XP for this program and it works like a charm.

/Freddan

---

