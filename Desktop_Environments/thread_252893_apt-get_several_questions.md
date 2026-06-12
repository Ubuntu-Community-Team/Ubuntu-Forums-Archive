---
title: "apt-get several questions"
date: 2006-09-07
forum: Desktop Environments
---

### Post by conexion200 on 2006-09-07
Hi!
1. How to lock specific version of package, so it will not be updated?
2. How to install specific version of package (older than newest)?

---

### Post by etank on 2006-09-07
To start with I would recommend using aptitude instead of apt-get see [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude) for the reasons why.

Here is a snippit from [http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)
> Using this resource is simple. You just need to edit the file /etc/apt/preferences.

The format is simple:

     Package: <package>
     Pin: <pin definition>
     Pin-Priority: <pin's priority>

Each entry must be separated from any other entries by a blank line. For example, to keep package sylpheed that I have modified to use "reply-to-list" at version 0.4.99, I add:

     Package: sylpheed
     Pin: version 0.4.99*


I hope that helps.

---

### Post by az on 2006-09-07
> **conexion200 said:**
> Hi!
1. How to lock specific version of package, so it will not be updated?
2. How to install specific version of package (older than newest)?

On the desktop, you can use synaptic to lock the version of a package and you can also install previous versions of a package, if they are still available.

---

### Post by etank on 2006-09-07
I like your way better, its easier. I didn't think of that.

---

