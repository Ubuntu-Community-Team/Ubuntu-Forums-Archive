---
title: "There got to be a butter way 2 install .tar files"
date: 2006-01-03
forum: Desktop Environments
---

### Post by vtechlinux on 2006-01-03
Hi everyonehttp://ubuntuforums.org/images/smilies/icon_razz.gif
I'm new at this OS (Ubuntu) and I like it, but just hate installing .tar files. I was just wondering if anybody have a script or something that would extract and install (and off course password prompt). This would help.

---

### Post by HermanAB on 2006-01-03
It is just a one liner:
tar -zxvf filename.tar.gz

To make that a script would require 2 lines:
#! /bin/bash
tar -zxvf $1

So not much point in that...

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by jlintz on 2006-01-03
[QUOTE=vtechlinux]Hi everyonehttp://ubuntuforums.org/images/smilies/icon_razz.gif
I'm new at this OS (Ubuntu) and I like it, but just hate installing .tar files. I was just wondering if anybody have a script or something that would extract and install (and off course password prompt). This would help.[/QUOTE]

you only extract tar's, you do not install them.  There could be anything you want inside a tar.

---

### Post by bored2k on 2006-01-03
You have to understand that most tar are just compressed packages like bzip, zip, rar, arj and so on, so installing a "tar" would not be an easy task, given how the creator can package and create its application in a gazillion different manners. You do want to learn how to handle certain installations (some would be as easy as cake, while other make you compile && search for dependencies for it). [http://en.wikipedia.org/wiki/.tar](http://en.wikipedia.org/wiki/.tar)

---

