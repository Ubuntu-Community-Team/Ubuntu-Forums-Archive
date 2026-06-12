---
title: "An error occurred!"
date: 2008-12-15
forum: General Help
---

### Post by Kaneda187 on 2008-12-15
I got this message when i started up after updating...

**An error occurred**

The following details were provided:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


```

What should I do?? 

Thanks

---

### Post by eBoxNet on 2008-12-15
> **Kaneda187 said:**
> I got this message when i started up after updating...

**An error occurred**

The following details were provided:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


```

What should I do?? 

Thanks


it looks like something happened during update. (broken package installation or something like that)
type ```
sudo dpkg --configure -a 
```
in a terminal window

---

### Post by Kaneda187 on 2008-12-15
Im not much good at reading terminal code so...
```
kaneda@kanedas-interface:~$ sudo dpkg --configure -a
[sudo] password for kaneda: 
Setting up initramfs-tools (0.92bubuntu16) ...
update-initramfs: deferring update (trigger activated)

Setting up msttcorefonts (2.5) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.27-9-generic
Errors were encountered while processing:
 msttcorefonts
kaneda@kanedas-interface:~$ 


```

is that good?

---

### Post by Kaneda187 on 2008-12-15
It dont look good:P

---

### Post by oldos2er on 2008-12-15
No, apt-get is trying to install msttcorefonts but can't find them. You can download the *deb file from here: [http://packages.debian.org/stable/x11/msttcorefonts](http://packages.debian.org/stable/x11/msttcorefonts) 

 Once it's downloaded, double-click on it to install.

---

### Post by RJARRRPCGP on 2008-12-15
> **Kaneda187 said:**
> I got this message when i started up after updating...

**An error occurred**

The following details were provided:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


```

What should I do?? 

Thanks

Looks like you may have borked your apt-get configuration file with perhaps a paste from the clipboard. Or the server is fubared.

---

