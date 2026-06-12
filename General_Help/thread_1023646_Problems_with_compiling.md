---
title: "Problems with compiling"
date: 2008-12-28
forum: General Help
---

### Post by GhentK on 2008-12-28
Hi all

First, I'm using Eeebuntu with the modified Array kernel, but I'm posting here due to good experiences with the Ubuntu community. :)

I'm trying to compile a program from source in order to [use my HTC Diamond as a modem](http://ubuntuforums.org/showthread.php?t=935203) (link to guide on how to do it). I've followed the steps in the guide, and it's easy as pie until step 4 (installing).

When I make, the terminal spits the following out at me:

```
user@machine:/usr/local/src/usb-rndis-lite$ make
make -C /lib/modules/2.6.27-8-eeepc/build SUBDIRS=/usr/local/src/usb-rndis-lite modules
make: *** /lib/modules/2.6.27-8-eeepc/build: No such file or directory.  Stop.
make: *** [default] Error 2
```

If I create /lib/.../build, and then make, I get the following:

```
user@machine:/usr/local/src/usb-rndis-lite$ make
make -C /lib/modules/2.6.27-8-eeepc/build SUBDIRS=/usr/local/src/usb-rndis-lite modules
make[1]: Entering directory `/lib/modules/2.6.27-8-eeepc/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.27-8-eeepc/build'
make: *** [default] Error 2
```

If I compile the program on my regular-Ubuntu computer, the installation is a breeze. I'm not enough in to compiling to fix the problem any further, so any help would be appreciated. :)

---

### Post by spiderbatdad on 2008-12-28
You do not need to make the directories. Of course you have to have a working internet connection to use subversion. You probably do or you wouldn't be in the usb-rndis-lite directory. I just ran make and it ran fine. You might contact the developers and request a patch for eeebuntu.

---

