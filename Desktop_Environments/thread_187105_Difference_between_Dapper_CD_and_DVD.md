---
title: "Difference between Dapper CD and DVD"
date: 2006-06-02
forum: Desktop Environments
---

### Post by therumble on 2006-06-02
Through a blog, I found [_this website_]("http://torrent.ubuntu.com/releases/dapper/release/dvd/") with torrent files for a Dapper DVD release. It seems legit, even though ubuntu.com does not list this DVD ISO anywhere on the site or on its mirrors.

What are the differences between the ~700 MB CD Dapper release and the DVD release? I have the resources to use both, but don't know what to use.

Thanks for the help!

---

### Post by ubnoobie on 2006-06-02
the dvd releases are found [http://cdimage.ubuntu.com/releases/6.06/release/](http://cdimage.ubuntu.com/releases/6.06/release/)

the dvd contains some extra packages and additional kernel versions (optimised for specific cpu's) not found on the cd. these other packages can be installed via the online repositories on any dapper system using apt-get, aptitude, synaptic, adept, etc. regardless of the media used to install the system.

the extra packages on the dvd are not installed with a default installation, but are "just there" so you can install them without having to download them.

the installed system using either cd or dvd will be the same, excepting the possibility that the dvd may install the cpu optimised kernel automatically (ie. the k7 kernel on an athlon instead of the generic 386 one).

for most people, a desktop (live cd & gui install) or alternate (text install, choice of regular install or a bare 'server' install) iso will be sufficient.

---

### Post by therumble on 2006-06-02
Thanks, ubnoobie. You don't seem very noob-ish, haha. With your help, I'm deciding to go with the DVD.

---

### Post by aysiu on 2007-01-28
I just checked *The Official Ubuntu Book* from the library, and as far as I can tell, the Ubuntu DVD contains the entire Main and Restricted repositories but boots to Ubuntu (Gnome) by default.

It also allows you to do a server installation, a text mode installation, or a regular live CD installation.

---

