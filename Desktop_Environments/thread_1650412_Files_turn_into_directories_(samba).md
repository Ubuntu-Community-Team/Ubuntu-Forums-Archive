---
title: "Files turn into directories? (samba)"
date: 2010-12-21
forum: Desktop Environments
---

### Post by andrewc6l on 2010-12-21
I've run into a weird state when using a Samba-mounted filesystem on Ubuntu 9.10. Every now and then, files will turn into directories. In other words, I see:
```

$ ls
realdir/ test.txt/ otherfile.txt/
```

If I change in and out of that directory, things fix themselves back up:
```
$ cd ..
$ cd mydir
$ ls
realdir/ test.txt otherfile.txt

```

I'm using the default shell, which I think is dash, and my Samba server is an Ubuntu Server 10.04 LTS. If I try to do file operations while the files are in the weird state (such as open in an editor) other programs recognize the files as directories and not regular files.

Has anyone ever seen anything like this before?

 - A

---

