---
title: "help!rar decompressor needed!"
date: 2005-03-25
forum: Desktop Environments
---

### Post by lorap on 2005-03-25
hi friends!
does anybody know any utility unpacks rar files?
it's VERY sad i can't unpack my LED ZEPPELIN album :-)
thanks.
pavel.

---

### Post by carlc on 2005-03-25
What about archive manager (file roller)?

---

### Post by telmo on 2005-03-25
I like Led Zeppelin! :) Why don't you install the 'rar' from multiverse? It might help you. I think it useless for files that were compressed with a rar version above 2.80, but it's worth to try.

---

### Post by lorap on 2005-03-25
i didn't compress them but i do want to uncompress,does anybody know the utility name to unpack rar files in linux?
thanks pavel

---

### Post by Buffalo Soldier on 2005-03-25
You mean the default application **file-roller** (Applications -> Accessories -> File Manager) doesn't work for you?

It uncompresses & unpacks RAR files just fine for me (works fine both in Warty and Hoary).

---

### Post by lorap on 2005-03-25
nope,it doesn't...
this's an error i get when trying to unpack the package:

/bin/sh: line 1: unrar: command not found

thanks.
pavel

---

### Post by chz on 2005-03-25
[QUOTE=lorap]hi friends!
does anybody know any utility unpacks rar files?
it's VERY sad i can't unpack my LED ZEPPELIN album :-)
thanks.
pavel.[/QUOTE]
 [http://ubuntuguide.org/#rar](http://ubuntuguide.org/#rar)

---

### Post by lorap on 2005-03-25
sudo apt-get install rar

Reading Package Lists... Done
Building Dependency Tree... Done
Package rar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rar has no installation candidate

---

### Post by Bob D. on 2005-03-25
You need to activate the the universe and multiverse repos for your copy of Warty. You should then be able to get unrar (universe) or unrar-nonfree (multiverse). See here for instructions: [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

According to the description in Synaptic,  unrar from universe cannot handle RAR  3.0 format files. I haven't tried myself, but I assume that unrar-nonfree can handle files in that format. This is for Hoary...I'd figure it would be the same for Warty.

Bob

---

### Post by lorap on 2005-03-25
i'll try it friend.
thank you very much.
it'd work for sure.
pavel

---

