---
title: "Directory management in Ubuntu"
date: 2019-02-13
forum: Desktop Environments
---

### Post by myolliul on 2019-02-13
Hi. I'm perfectly newb in using Ubuntu.

I've used Ubuntu in VirtualBox to do my college assignment of C coding with gcc, vim, with the host os Windows10. But I don't know well about Ubuntu itself.
Few days ago, I made my Laptop be able to dual boot Windows10, Ubuntu18.04.1 LTS. I made the disk partition of 100GB to be used in Ubuntu. While nstalling Ubuntu, I assigned 10GB, 4GB, 86GB for '/', 'swap', '/home', I remember.

But I don't know that partitioning's meaning.(I just googled about dual booting, and just copy others' procedure.) 
But after I had installed some tools with apt, apt-get (build-essential, python, vim, etc), I noticed that they were put into /etc, /usr, /bin in some way I don't know. So I'm curious why I assigned most of memory(100GB) to /home.
This seems to be very easy question, but I cannot choose which keywords to search it.

---

### Post by CatKiller on 2019-02-13
Your allocation for / is a bit on the small side. You don't need a swap partition any more. 

> **myolliul said:**
> So I'm curious why I assigned most of memory(100GB) to /home.

All of your data goes in /home. Media files, Steam games, and so on. Everything else might go up to about 25-30 GB or so, depending on how much you install, but /home doesn't really have a limit on how much you might want to put there. 

[https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by myolliul on 2019-02-13
Oh Thanks for useful link. That really helped.

---

