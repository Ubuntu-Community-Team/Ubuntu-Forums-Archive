---
title: "Openbox - obmenu menu editor"
date: 2006-01-07
forum: General Help
---

### Post by ScreemingBlue on 2006-01-07
Has anybody had any luck installing obmenu from source. It's a menu editor for openbox, looks pretty cool if I could get it running....:(

You can have a look here.. [http://obmenu.sourceforge.net/](http://obmenu.sourceforge.net/) .

---

### Post by mztriz on 2006-01-07
[QUOTE=ScreemingBlue]Has anybody had any luck installing obmenu from source. It's a menu editor for openbox, looks pretty cool if I could get it running....:(

You can have a look here.. [http://obmenu.sourceforge.net/](http://obmenu.sourceforge.net/) .[/QUOTE]
I haven't tried to install it but what errors were you receiving?

---

### Post by ScreemingBlue on 2006-01-07
After installing python2.4, python2.4-dev and python2.4-gtk2 I followed the instructions to install obmenu and that all works fine with no errors. 
I run obmenu and get this:-

> File "/usr/bin/obmenu", line 8, in ?
       import xml.dom.minidom, gtk, gtk.glade, gobject, random, time, os, sys
ImportError: No module named glade

Any ideas?

Cheers

---

### Post by ScreemingBlue on 2006-01-07
Sorry fixed it, sometimes reading the error messages gives you clues.

I ran > sudo apt-get python2.4-glade2 and all worked OK.

Cheers for your help.

---

### Post by starscalling on 2006-01-09
yeah
not so great from here
installed all the above stuff
and get this


neko@uub:~$ tar xzf obmenu-0.9.2.tar.gz
neko@uub:~$ cd obmenu
neko@uub:~/obmenu$ su
Password:
root@uub:/home/neko/obmenu# python setup.py install
running install
running build
running build_scripts
creating build
creating build/scripts-2.4
copying and adjusting obmenu -> build/scripts-2.4
changing mode of build/scripts-2.4/obmenu from 644 to 755
running install_scripts
copying build/scripts-2.4/obmenu -> /usr/bin
changing mode of /usr/bin/obmenu to 755
running install_data
root@uub:/home/neko/obmenu#

so far so good
till i try using it
either as a user or as root !_!

obmenu
Error: File not found
root@uub:~#

and there u go !_!

---

### Post by PeterWolf on 2006-01-11
To get over the file not found error, try:

obmenu /home/*yourusername*/.config/openbox/menu.xml

Works for me.

---

### Post by okicache on 2006-02-27
You are going to need python2.4-dev to get the python script to properly install, run this and then follow the readme with obmenu.  Should work like a charm.
```
sudo apt-get install python2.4-dev
```

---

