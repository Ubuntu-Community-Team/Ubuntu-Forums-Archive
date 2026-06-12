---
title: "Installing VMWare Server on Ubuntu 5.10"
date: 2006-03-07
forum: Desktop Environments
---

### Post by jeffery on 2006-03-07
I am running Ubuntu 5.10 and want to install vmware server.

I've seen on a couple sites that it is necessary to compile the kernel in order to install and configure vmware.


I am completely new to Linux; therefore, I do not know how to compile a kernel - let alone make sure that I compile it properly for vmware.

Is there anyone out there that has installed vmware server successfully on Ubuntu 5.10 that would be able to give me a play-by-play?


Thank you in advance,
Jeffery

---

### Post by fille on 2006-03-08
Just make sure that you have the build-essential packages installed.
It will installed the needed compiler stuff and kernel headers/source.
Then run the vmware installer script.
```
sudo apt-get update
sudo apt-get install build-essential
vmware-install.pl
```

---

### Post by jeffery on 2006-03-11
Thanks fille!

I ended up having to point the configurator to the header files, but it wasn't too hard to figure out that portion for myself.

---

