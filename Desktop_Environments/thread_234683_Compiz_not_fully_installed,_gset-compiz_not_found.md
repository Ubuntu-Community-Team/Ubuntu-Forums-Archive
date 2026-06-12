---
title: "Compiz not fully installed, gset-compiz not found?"
date: 2006-08-11
forum: Desktop Environments
---

### Post by Jessehk on 2006-08-11
I followed the instructions to install xgl and compiz here: [https://help.ubuntu.com/community/CompositeManager/Xgl?highlight=%28xgl%29](https://help.ubuntu.com/community/CompositeManager/Xgl?highlight=%28xgl%29)

using method A, which sets up a Session in gdm.

My problem is that it doesn't seem to have fully installed. Some things, like wobbly windows, work. About 90% of advertised features are just not present.

Lastley, when I try to install gset-compiz, it tells me it can't find it.

Here is all the relavent information. Any help would be greatly appreciated.

**error when trying to install gset-compiz**
```

$ sudo apt-get install gset-compiz
Reading package lists... Done
Building dependency tree... Done
Package gset-compiz is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gset-compiz has no installation candidate

```

**sources.list**
```

# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://ca.archive.ubuntu.com/ubuntu dapper main restricted
deb http://ca.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://ca.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://ca.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://ca.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://ca.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# for XGL/compiz
deb http://ubuntu.compiz.net/ dapper main
deb http://beerorkid.com/compiz/ dapper main

```

Attached is a screenshot of the limited installation I have.

---

### Post by Jessehk on 2006-08-11
I apologise for doing this, but I must BUMP.

If any more information would be useful in solving this problem, please let me know. I would would be happy to provide it. 

Furthermore, before telling me to search, I can assure you I have been for the past 4 hours. Thanks again. :)

---

### Post by Jessehk on 2006-08-11
As per requested on #ubuntu, here is some more information.

**/usr/bin/startxgl.sh**
```

#!/bin/sh

Xgl :1 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer &
DISPLAY=:1
exec gnome-session

```

**/usr/share/xsessions/xgl.destop**
```

[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Comment=Start an Xgl Session
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application

```

Attached screenshot of my start up programs:

---

### Post by Jessehk on 2006-08-11
I feel stupid.

If this happens to you, the solution is to manually add entries to the list of loaded plugins in gconf-editor. 

Just add them in this order and it should work: gconf, miniwin, decoration, transset, state, wobbly, fade, minimize, cube, rotate, zoom,
scale, move, resize, place, switcher, trailfocus, water, bs

Compiz is amazing! :D

---

### Post by JerMe on 2006-08-12
From [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) ....



Add these to your /etc/apt/sources.list file:
```
deb http://www.beerorkid.com/compiz dapper main
deb http://media.blutkind.org/xgl/ dapper main
deb http://ubuntu.compiz.net/ dapper main
```

Then add the GPG keys:
```
wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
wget http://media.blutkind.org/xgl/quinn.key.asc -O - | sudo apt-key add -
wget http://ubuntu.compiz.net/quinn.key.asc -O - | sudo apt-key add -
```

then update and install gset-compiz
```
sudo apt-get update
sudo apt-get install gset-compiz
```


I had both ubuntu-desktop and kubuntu-desktop installed.  When I cleaned out kubuntu-desktop (KDE), it took my compiz setup along with it.  I tried to re-install gset-compiz but was getting the error that you posted.  So I paid a visit to Quinn's site, which had different repositories than before.  So once you add those new repositories, you can install gset-compiz.  Good luck~

---

### Post by anasofiapaixao on 2006-08-20
Looks like they pulverized gset-compiz from all repositories... I have installed compiz in my mom's and this hasn't happened. Thankfully I hadn't cleared the cache from there [and so I saved the deb file]("http://anasofiapaixao.iespana.es/apps/gset-compiz_0.3.3-0ubuntu2_i386.deb.tar.gz"). Perfect for a temporary fix ;)

NOTE: THIS IS A DEB FILE, NOT A TARBALL. Take off the extension, for some reason if I left it with .deb it would give me the "403 Forbidden" message.

---

### Post by mobin on 2006-08-25
Thanks ana I was going crazy trying to find gset-compiz

---

### Post by peabody on 2006-08-25
I believe it was pulled from the repositories for being old and unmaintained.  The best way to tweak the features currently is through gconf from what other countless people tell me.

---

### Post by asfonseca on 2006-08-26
Thank you, thank you, thank you! Clever girl!

bye

> **anasofiapaixao said:**
> Looks like they pulverized gset-compiz from all repositories... I have installed compiz in my mom's and this hasn't happened. Thankfully I hadn't cleared the cache from there [and so I saved the deb file]("http://anasofiapaixao.iespana.es/apps/gset-compiz_0.3.3-0ubuntu2_i386.deb.tar.gz"). Perfect for a temporary fix ;)

NOTE: THIS IS A DEB FILE, NOT A TARBALL. Take off the extension, for some reason if I left it with .deb it would give me the "403 Forbidden" message.

---

