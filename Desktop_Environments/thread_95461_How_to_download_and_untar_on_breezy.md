---
title: "How to download and untar on breezy?"
date: 2005-11-26
forum: Desktop Environments
---

### Post by RAV TUX on 2005-11-26
can some please help me out or point me in the right direction to easily download and untar things, ie the flock browser? need very basic beginer steps please.:confused:

---

### Post by aysiu on 2005-11-26
Read this:
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by matthew on 2005-11-26
There are two ways to do this. In either case you will first need to install the unrar utility. It is called unrar-nonfree and you can install it using Synaptic or by typing this in a terminal:
```
sudo apt-get install unrar-free
``` Once that is installed you can simply click on a rar archive when browsing in Nautilus (the default graphic file browser in Ubuntu) or you can use the command line in a terminal like this:
```
unrar e <filename>.rar
```

EDIT: I read "unrar" instead of "untar." My mistake...follow the directions in aysiu's link. I'll leave mine here just in case anyone is interested... :)

---

