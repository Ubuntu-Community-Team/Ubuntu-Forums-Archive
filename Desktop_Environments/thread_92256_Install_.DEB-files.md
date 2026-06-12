---
title: "Install .DEB-files"
date: 2005-11-19
forum: Desktop Environments
---

### Post by elreteipos on 2005-11-19
Hello,

I have a file (make-2.80-9_i386.deb, the make command) and I want to install it on Ubuntu. How do I do that?

---

### Post by matthewv on 2005-11-19
[QUOTE=elreteipos]Hello,

I have a file (make-2.80-9_i386.deb, the make command) and I want to install it on Ubuntu. How do I do that?[/QUOTE]
you would do ```
sudo dpkg -i <nameoffile.deb>
``` eg sudo dpkg -i make-2.80-9_i386.deb

However, make is in the ubuntu repositories, so all you will have to do is 
```
sudo apt-get install make
``` although the easiest way to install make is ```
sudo apt-get install build-essential
```

The apt-get commands will download the package and its dependancies from the ubuntu repositories, and install it

For most common progs you can use apt-get

---

### Post by elreteipos on 2005-11-19
I'm afraid I can't use the *sudo apt-get install build-essential* command because my wireless LAN doesn't work with Ubuntu.

---

### Post by matthewv on 2005-11-19
But using dpkg to install the file works, right??

---

### Post by elreteipos on 2005-11-19
Yes. Thanks for helping me out with this.

---

