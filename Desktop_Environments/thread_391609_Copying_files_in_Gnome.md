---
title: "Copying files in Gnome"
date: 2007-03-23
forum: Desktop Environments
---

### Post by mikeglaz on 2007-03-23
I want to copy a folder from my Desktop to /var/www.  But I get a Permission Denied error.  Is there any way to do this without relogging in as root?  I want to just drag and drop a file from one directory to another (like in Windows) without going through the terminal with 'sudo'.

thanx,
mike

---

### Post by taurus on 2007-03-23
Press <Alt>F2 and type

```
gksudo nautilus
```
Browse to where the directory you want to move/copy and just drag it over to /var/www.

---

### Post by aysiu on 2007-03-23
Read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

It'll help for this situation.

---

### Post by jenhsun on 2007-03-23
Mike, use your Automatix2 and find Nautilus Script
then install it.
If you like to copy and paste in GUI mode, above your file browser right click-> script->root-nautilus-here..... 
You will know what I mean, just drag and drop.

---

### Post by ardchoille42 on 2007-03-23
> **jenhsun said:**
> Mike, use your Automatix2 and find Nautilus Script
then install it.
If you like to copy and paste in GUI mode, above your file browser right click-> script->root-nautilus-here..... 
You will know what I mean, just drag and drop.

Or he could just do

```

gksudo nautilus

```

and still be able to drag and drop without having to install anything :)

---

