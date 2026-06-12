---
title: "Multiple squashmnt dir"
date: 2009-04-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by moremeba on 2009-04-08
All, i have noticed that i have a dir under my file system named squashmnt 2.7gb and inside that dir i have a sub dir called squashmnt, and inside that dir i have another sub called squashmnt etc etc.
I am getting low on disk space....any ideas as to why this would happen? Is it possible to delete it? surely i only need one instance.

Any help much appreciated
Rgds
Moremeba
Dell Mini 9 8GB ssd

---

### Post by HeeledOver on 2009-05-26
I'm having the same problem and I'd love to have the answer to this as well!

---

### Post by ramin.honary on 2009-08-01
The "squashmnt" directory is a symbolic link (in Windows terms a "shortcut", in MacOS terms an "alias") which points to the root directory. If you run the command:```
ls -ld /squashmnt
```you should get the output ```
lrwxrwxrwx 1 root root 1 2009-03-30 23:25 squashmnt -> /
```The little arrow pointing to a slash at the end of the line is telling you that this is a symbolic link that points to the "/" directory.

When you look inside, you will see exactly the same files that are contained in your root directory, which includes the squashmnt symbolic link itself, so you can jump down into the squashfs directory indefinitely (or until your file browser or shell tells you you have hit a recursive limit).

It is probably related to the "squashfs" which is a special linux filesystem that compresses all of the data stored in it, which makes it useful for small computer systems that need to conserve space. [http://squashfs.sourceforge.net/](http://squashfs.sourceforge.net/)

I don't know that Dell inspiron actively uses squashfs for anything except perhaps for booting into a "safe mode" or "diagnostics mode" perhaps. I have also heard that I the Java runtime environment needs a "squashmnt" for some reason. Or maybe the software guys at dell needed it for debugging or something. Therefore you should leave it alone.

I wish I could tell you more, but I don't really know too much about it.

---

