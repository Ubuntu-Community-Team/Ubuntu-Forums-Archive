---
title: "backports not working"
date: 2005-10-02
forum: Desktop Environments
---

### Post by jnev on 2005-10-02
is it just me, or are the repositories down? for the last few days everytime i sudo apt-get update, this is the message i get:

```
jnev@jnevlinux:~$ sudo apt-get update
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release.gpg
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release.gpg
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release
Ign http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
Get:1 http://us.archive.ubuntu.com hoary Release.gpg [189B]
Ign http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
Get:2 http://us.archive.ubuntu.com hoary-updates Release.gpg [189B]
Get:3 http://security.ubuntu.com hoary-security Release.gpg [189B]
Get:4 http://archive.ubuntu.com hoary Release.gpg [189B]
Ign http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Err http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
  404 Not Found
Hit http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Hit http://us.archive.ubuntu.com hoary Release
Hit http://security.ubuntu.com hoary-security Release
Hit http://archive.ubuntu.com hoary Release
Hit http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Hit http://us.archive.ubuntu.com hoary-updates Release
Hit http://security.ubuntu.com hoary-security/main Packages
Hit http://archive.ubuntu.com hoary/multiverse Packages
Hit http://us.archive.ubuntu.com hoary/main Packages
Hit http://us.archive.ubuntu.com hoary/restricted Packages
Hit http://security.ubuntu.com hoary-security/restricted Packages
Hit http://security.ubuntu.com hoary-security/main Sources
Hit http://archive.ubuntu.com hoary/multiverse Sources
Hit http://us.archive.ubuntu.com hoary/main Sources
Hit http://us.archive.ubuntu.com hoary/restricted Sources
Hit http://us.archive.ubuntu.com hoary/universe Packages
Hit http://us.archive.ubuntu.com hoary/universe Sources
Hit http://us.archive.ubuntu.com hoary-updates/main Packages
Hit http://us.archive.ubuntu.com hoary-updates/restricted Packages
Hit http://security.ubuntu.com hoary-security/restricted Sources
Hit http://security.ubuntu.com hoary-security/universe Packages
Hit http://security.ubuntu.com hoary-security/universe Sources
Hit http://us.archive.ubuntu.com hoary-updates/main Sources
Hit http://us.archive.ubuntu.com hoary-updates/restricted Sources
Fetched 4B in 1s (3B/s)
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

the backports.mirrormax have have always been ignored (i'm assuming that's what ign means) since i installed kubuntu, but now i'm also getting some error associated with them. i'm trying to install gaim-encryption and it's telling me that it's unable to fetch some archives. i went to my sources.list and removed the backports, and now it's working perfectly. what's wrong with the backports?

thanks

---

### Post by tehwa on 2005-10-02
Backports are moved:

[http://linux.blogweb.de/archives/109-Shout-it,-shout-it,-shout-it-out-loud....html](http://linux.blogweb.de/archives/109-Shout-it,-shout-it,-shout-it-out-loud....html)

---

### Post by jnev on 2005-10-02
that would explain it, thanks!

---

### Post by ryke on 2005-10-03
Hi,

Thanx for the help (I had the same problem). However, there are still some packages that cannot be accessed (like bittornado, chkrootkit, unrar, w32codecs...). Is there any place to get them?

BTW, is there any place where you can find information about this kind of repos' changes?

thanx

---

### Post by escobar on 2005-10-10
[QUOTE=ryke]Hi,

Thanx for the help (I had the same problem). However, there are still some packages that cannot be accessed (like bittornado, chkrootkit, unrar, w32codecs...). Is there any place to get them?

BTW, is there any place where you can find information about this kind of repos' changes?

thanx[/QUOTE]

*bump*

I'd like to know as well. Especially the second part of your question. Also, are the Hoary backports safe for use in Breezy?

---

