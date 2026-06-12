---
title: "How to get Supertux 0.6.0 on Ubuntu 18.04"
date: 2019-02-05
forum: Gaming &amp; Leisure
---

### Post by Cavsfan on 2019-02-05
Since Ubuntu 18.04 has version 0.5.1-1build1 and other distros have the newer 0.6.0 version, I thought I'd post this.

[http://tipsonubuntu.com/2018/12/25/install-supertux-0-6-0-ubuntu-18-04/](http://tipsonubuntu.com/2018/12/25/install-supertux-0-6-0-ubuntu-18-04/)

It will leave you with 2 of the same Supertux icons under Games unless or until you remove version 0.5.1-1build1.

You can purge it or remove it; both do the same thing.

```
cavsfan@bionic:~$ sudo apt purge supertux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libsdl2-image-2.0-0
Use 'sudo apt autoremove' to remove it.
The following packages will be REMOVED:
  supertux*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 4,257 kB disk space will be freed.
Do you want to continue? [Y/n]

```

It's a favorite of mine on Linux systems. The new version is quite a bit more difficult than the older one. :P

It looks like a lot of work went into the new version, which is nice to see.

I had to perform a restart to see the new version but, when I deleted the old one, it left one icon, the new version.

---

