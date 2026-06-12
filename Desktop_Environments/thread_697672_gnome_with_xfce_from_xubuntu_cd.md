---
title: "gnome with xfce from xubuntu cd"
date: 2008-02-15
forum: Desktop Environments
---

### Post by jakhicks on 2008-02-15
I know the apt-get to install xubuntu, but I only have dial-up at the moment so it would take too long to download, I do have a copy of xubuntu on cd though. Is it possible to install the packages from the cd to ubuntu through synaptic or do I need specific terminal commands?

---

### Post by mojoman on 2008-02-15
I think so, at least if they are the same release (e.g. both are gutsy or whatever).

First off, clean the apt-get archive.
```

sudo apt-get clean
```

This should make sure, I think, that you don't have any old sources when you later try to apt-get install something. Then add the xubuntu cd to your sources list using the command
```

sudo apt-cdrom add
```

Terminal will prompt you to pop in a CD. Do it, press enter and it should scan the CD. After that I think you should be able to install anything from the xubuntu CD by using the regular apt-get command. That should include the xfce desktop. 

Hope it helps
/mojoman

---

### Post by jakhicks on 2008-02-15
Worked perfectly! Thanks... xfce is surprisingly nice to use!

---

### Post by mojoman on 2008-02-16
> **jakhicks said:**
> Worked perfectly! Thanks... xfce is surprisingly nice to use!

It is. As DE comes and goes, it's my favorite. Apt is also awesome. It never ceases to surprise my how good it is.

---

