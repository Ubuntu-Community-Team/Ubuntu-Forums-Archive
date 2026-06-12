---
title: "invalid key signature in repo archive"
date: 2009-04-17
forum: General Help
---

### Post by sphilli8 on 2009-04-17
Hi,

The latest of my [almost daily repo failures]("http://ubuntuforums.org/showthread.php?t=1126979"):

Adept Updater will not open at all, and when I try "apt-get update" I get this error message:
> W: GPG error: [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems


I tried this command that I found in another forum:
```
sudo apt-get update -o Acquire::http::No-Cache=true 
```

..but no joy.

Anyone got joy?

---

