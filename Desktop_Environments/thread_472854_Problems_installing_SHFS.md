---
title: "Problems installing SHFS"
date: 2007-06-13
forum: Desktop Environments
---

### Post by chrisjoha on 2007-06-13
I'm trying to install SHFS, but no such luck. I did:

sudo apt-get install shfs-source shfs-utils module-assistant linux-headers-`uname -r`
sudo module-assistant build shfs

Then it just fails, and the log displays this info, but I don't know what it means?

                  &#9474; /usr/src/modules/shfs/Linux-2.6/dir.c: In function ‘shfs_create’:          &#9618;                   
                  &#9474; /usr/src/modules/shfs/Linux-2.6/dir.c:305: error: ‘struct inode’ has no    &#9618;                   
                  &#9474; member named ‘u’                                                           &#9618;                   
                  &#9474; /usr/src/modules/shfs/Linux-2.6/dir.c:306: error: ‘struct inode’ has no    &#9618;                   
                  &#9474; member named ‘u’                                                           &#9618;                   
                  &#9474; make[4]: *** [/usr/src/modules/shfs/Linux-2.6/dir.o] Error 1               &#9618;                   
                  &#9474; make[3]: *** [_module_/usr/src/modules/shfs/Linux-2.6] Error 2             &#9618;                   
                  &#9474; make[3]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'      &#9618;                   
                  &#9474; make[2]: *** [default] Error 2                                             &#9618;                   
                  &#9474; make[2]: Leaving directory `/usr/src/modules/shfs/Linux-2.6'               &#9618;                   
                  &#9474; make[1]: *** [binary-modules] Error 2                                      &#9618;                   
                  &#9474; make[1]: Leaving directory `/usr/src/modules/shfs'                         &#9646;                   
                  &#9474; make: *** [kdist_build] Error 2

---

### Post by chrisjoha on 2007-06-16
Does anyone have an idea?

---

### Post by honeysett on 2007-06-18
I have exactly the same problem -  i.e. failed at the same place with the same error message. I am after help too.

---

### Post by chrisjoha on 2007-06-29
Anyone?

---

### Post by dl7und on 2007-07-02
I don't know what's going on with shfs, but there is another package that might even be better: sshfs.

It's in the repositories, and since it works through fuse, it should not be necessary to recompile a package each time you get a new kernel. The syntax is the same as with shfsmount, just use sshfs instead.

Though there seems to be one problem on Feisty: You need to add yourself manually to the fuse group, or you will get a permission denied error from fusermount and/or /dev/fuse.

I've been using shfs happily for a few years now and just ran into the same problem all of you experienced, but sshfs looks like an even better replacement. Give it a try...

---

