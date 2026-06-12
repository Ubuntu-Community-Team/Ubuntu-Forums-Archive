---
title: "Desktop File Sharing issue ... ??"
date: 2013-01-20
forum: Desktop Environments
---

### Post by adym3333 on 2013-01-20
I did a fresh install of lucid lynix 10.04 and installed samba packages on it and want to share my desktop files so i right click the desktop folder and then to share tab and create share ,selected allow guests and users to create and delete files.
So now the folder of desktop can be seen on other systems but when the folder is clicked to open it asks username and password although even after giving correct username and password of the shared desktop system it says authentication failed ...:confused:.... ??

---

### Post by meteorrock on 2013-01-20
You probably do not have administration rights to open that file, try to use the included file manager 'nautilus' in the terminal to give yourself sudo or superuser rights.

```
gksu nautilus
```

I do not know if your distro includes nautilus by default, you might have to get it through the apt-get.

```
 sudo apt-get update && sudo apt-get install nautilus
```

The above code should open up nautilus for you to open and move that file if it is installed. If not use the bottom code first to install it. 

I hope that file is not a file for your operating system.

---

