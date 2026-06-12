---
title: "Creating a distribution based on another distribution"
date: 2008-11-28
forum: Development CD/DVD Image Testing
---

### Post by JeyPeyy on 2008-11-28
How do I create a live-cd distribution based on another distribution? It's for a project at school.

---

### Post by albandy on 2008-11-28
You can use Ubuntu Customization Kit, it's a utility to build your own customized Ubuntu distro.

[http://uck.sourceforge.net/](http://uck.sourceforge.net/)

---

### Post by JeyPeyy on 2008-11-29
> **albandy said:**
> You can use Ubuntu Customization Kit, it's a utility to build your own customized Ubuntu distro.

[http://uck.sourceforge.net/](http://uck.sourceforge.net/)

Is this the way the developers do? I want to do it the way the developers do when they make a new distribution or a new version of their distribution. For example: How did canonical do the first version of ubuntu based on debian? How did they do when they made intrepid ibex?

---

### Post by albandy on 2008-11-29
1.- Download all src debs you need from debian
2.- Compile it
3.- Download bootCD
4.- Create manually all the script you need to make it boot.

It's a bit hard but you can do it in this way. I recomend you the following manuals:

[http://www.debian.org/doc/developers-reference/](http://www.debian.org/doc/developers-reference/)
[http://wiki.debian.org/DebianInstaller/GUI](http://wiki.debian.org/DebianInstaller/GUI)
[http://debian-live.alioth.debian.org/](http://debian-live.alioth.debian.org/)

is not as easy as UCK.

---

### Post by JeyPeyy on 2008-11-29
> **albandy said:**
> 1.- Download all src debs you need from debian
2.- Compile it
3.- Download bootCD
4.- Create manually all the script you need to make it boot.

It's a bit hard but you can do it in this way. I recomend you the following manuals:

[http://www.debian.org/doc/developers-reference/](http://www.debian.org/doc/developers-reference/)
[http://wiki.debian.org/DebianInstaller/GUI](http://wiki.debian.org/DebianInstaller/GUI)
[http://debian-live.alioth.debian.org/](http://debian-live.alioth.debian.org/)

is not as easy as UCK.

Is this also how they did when doing Intrepid ibex? Actually, I want to base my distribution on openSUSE, but I find this forum much better.

---

### Post by damis648 on 2008-11-29
What I have done is use [this guide]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=5454201"). I would recommend it. It starts with a minimal CLI installation of Ubuntu, and from there you can install a GUI and anything else and customize to your heart's content.

---

### Post by JeyPeyy on 2008-11-29
Ok, I've decided to do it [this way]("https://help.ubuntu.com/community/LiveCDCustomization") instead. But I would like to do a openSUSE distribution. Is there any documentation like that one about doing an openSUSE live-cd? If not I'll just stick with [this]("https://help.ubuntu.com/community/LiveCDCustomization").

---

### Post by Sorivenul on 2008-11-30
The [KIWI Image System]("http://kiwi.berlios.de/") may be of use.
Also, this should probably be in "Other OS Talk".

---

### Post by salvachn on 2009-05-06
> **albandy said:**
> 1.- Download all src debs you need from debian
2.- Compile it
3.- Download bootCD
4.- Create manually all the script you need to make it boot.

It's a bit hard but you can do it in this way. I recomend you the following manuals:

[http://www.debian.org/doc/developers-reference/](http://www.debian.org/doc/developers-reference/)
[http://wiki.debian.org/DebianInstaller/GUI](http://wiki.debian.org/DebianInstaller/GUI)
[http://debian-live.alioth.debian.org/](http://debian-live.alioth.debian.org/)

is not as easy as UCK.

Is this the way we create a distro from Debian? or Ubuntu?

---

