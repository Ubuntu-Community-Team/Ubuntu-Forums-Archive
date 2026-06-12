---
title: "2nd LAMP installation in same box -- possible?"
date: 2009-06-24
forum: General Help
---

### Post by feminaexlux on 2009-06-24
This is a little more complicated than a typical LAMP question. I want to maintain a *php 4.3.9* site and *mysql 4.1.22* database with *apache 2.0.52* on a separate web server, and would like to edit files locally for testing. (I know I'd have to compile them from source, I'm fine with that)

I've all ready got an up-to-date LAMP installation on my ubuntu, which I use for testing another web server, and I'd like to keep that.

I was wondering if there's a safe way to install 2 different apaches, phps, and mysqls without things blowing up or running over each other? I know I can do that with Windows and WAMP Server. Is there a safe way in Ubuntu that keeps the outdated LAMP to itself, and the up-to-date LAMP to itself?

---

### Post by Mighty_Joe on 2009-06-25
[VirtualBox]("http://www.virtualbox.org/") or [VmWare Server]("http://www.vmware.com/products/server/")?  My employer uses VmWare to keep a number of virtual machines with different OS's around so we can do testing.  
You could set up two, one for each LAMP (I like to keep my build processes the same for each of my machines).  
Depending on how comfortable you are with the command line, I'd recommend you use Ubuntu Server or [Ubuntu JeOS]("http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos") for the "guest" OS to conserve resources on your "real" machine.

---

### Post by feminaexlux on 2009-07-02
That sounds like a good idea. Thanks for the tip :)

---

