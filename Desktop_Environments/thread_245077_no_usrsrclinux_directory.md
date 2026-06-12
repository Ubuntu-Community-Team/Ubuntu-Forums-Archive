---
title: "no /usr/src/linux directory"
date: 2006-08-27
forum: Desktop Environments
---

### Post by Jacks0n on 2006-08-27
Hi. I followed [this]("http://www.ubuntuforums.org/showthread.php?t=217657") guide to compile the latest kernel (2.6.17.11). It worked perfectly, except I found that there was no wireless driver. Also I didn't configure it properly, so I decided to re-install it. I just uninstalled 2 packages from synaptic (linux 2.6.17.11 and the header for it), and re-started. It worked fine. I went to follow the guide again, and I'm up to the 3rd command .. sudo rm -rf linux && sudo ln -s /usr/src/linux-2.6.17.11 linux && cd /usr/src/linux. But I don't have a /usr/src/linux directory. Plus there's a link to one in /usr/src.

I'm sure this is really trivial, sorry, I'm just really new to this.
What did I do wrong, and how do I compile the kernel? I have the tarball on hand, I just have no idea how to install a kernel.

P.S. By the way, where *is* each kernel stored?

-Thanks, Jackson.

---

### Post by taurus on 2006-08-27
You need to link /usr/src/linux to whatver kernel you are using or planning to compile...

```

sudo ln -s /usr/src/linux-2.17.xx /usr/src/linux

```
The kernel is in /boot.

---

### Post by Jacks0n on 2006-08-27
aah ok.. thanks alot!

---

