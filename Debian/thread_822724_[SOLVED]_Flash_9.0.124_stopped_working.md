---
title: "[SOLVED] Flash 9.0.124 stopped working"
date: 2008-06-08
forum: Debian
---

### Post by kung fu buntu on 2008-06-08
I had version 9.0.115  IIRC, but after I installed the newer version things broke :(

This happens both with firefox and opera.

Any ideas?

---

### Post by pro003 on 2008-06-08
Why dont you:

```
sudo apt-get remove flash-plugin-nonfree
```

and then:

```
sudo apt-get update
```

```
sudo apt-get autoclean
```

```
sudo apt-get install ubuntu-restricted-extras
```

...see what happens?:popcorn:

---

### Post by kung fu buntu on 2008-06-08
I don't have flash-plugin-nonfree installed.

I have checked for updates before, but there is no newer version.

I'm using Debian, not Ubuntu.



I would be interested to know if there is anyone with 9.0.124 working or how can I trace this problem.

Thanks

---

### Post by pro003 on 2008-06-08
oh, what am I thinking? anyway, you could check this [page]("http://playingwithsid.blogspot.com/2007/09/installing-flash-plugin-in-debian.html")

good luck.

---

### Post by Sef on 2008-06-08
Moved to Debian Forum.  

OP, are you using a 64-bit system?

---

### Post by kung fu buntu on 2008-06-08
@ Sef

Yes, I'm using 64bit system.
That is why I posted it there.

I remind that I used to have flash working fine previously.
It is probably something (but I'm not 100% sure) related with this upgrade/flash version.


I removed the package and when I tried to reinstall:
> Setting up flashplayer-mozilla (9.0.124.0-0.0) ...
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: error while loading shared libraries: libpixman-1.so.0: cannot open shared object file: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplayer/libflashplayer.so
dpkg: error processing flashplayer-mozilla (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplayer-mozilla
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up flashplayer-mozilla (9.0.124.0-0.0) ...
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: error while loading shared libraries: libpixman-1.so.0: cannot open shared object file: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplayer/libflashplayer.so
dpkg: error processing flashplayer-mozilla (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplayer-mozilla

I'll goog and see if I can fix this...

---

### Post by kung fu buntu on 2008-06-08
I updated my ia32*libs and reinstalled the thing (remember to purge it first, not just remove it).

After that the plugin was detected by Opera (it wasn't previously) and it's now working fine in Opera and IceWeasel.

---

