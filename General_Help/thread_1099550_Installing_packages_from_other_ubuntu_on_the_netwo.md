---
title: "Installing packages from other ubuntu on the network."
date: 2009-03-18
forum: General Help
---

### Post by muxecoid on 2009-03-18
I saw that sometimes when I want to install a package that is already installed on other ubuntu in local network it does not download it from remote server, but takes it from nearby computer instead. Is there a way to transform one of the machines to "mirror" and tell other machines to take packages and updates only from this machine and not try to connect to external repos?

---

### Post by lykwydchykyn on 2009-03-18
You can install apt-mirror and create a local repository.  It takes 20-40 GB of space depending on how much of the repositories you want to mirror (main, universe, multiverse, backports, etc).

Check out this howto:
[http://www.howtoforge.com/local_debian_ubuntu_mirror](http://www.howtoforge.com/local_debian_ubuntu_mirror)

---

### Post by muxecoid on 2009-03-18
Thanks. In fact what I want is that only software that the packages that are installed on given machine to be installable on other computers. Not a real full mirror, just using the packages from cache on local network.

---

### Post by lykwydchykyn on 2009-03-18
Sounds like you need apt-proxy.  I have never used it, so I can't help you with setting it up, but I'm pretty sure that's what it does.

[https://help.ubuntu.com/community/AptProxy](https://help.ubuntu.com/community/AptProxy)

---

