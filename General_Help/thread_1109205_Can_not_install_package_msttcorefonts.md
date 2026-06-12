---
title: "Can not install package msttcorefonts"
date: 2009-03-28
forum: General Help
---

### Post by Dave_Connor on 2009-03-28
```
 sudo apt-get --reinstall install msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of msttcorefonts is not possible, it cannot be downloaded.
The following packages were automatically installed and are no longer required:
  libmikmod2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ttf-mscorefonts-installer (2.7) ...

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
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of msttcorefonts:
 msttcorefonts depends on ttf-mscorefonts-installer; however:
  Package ttf-mscorefonts-installer is not configured yet.
dpkg: error processing msttcorefonts (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-mscorefonts-installer
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I cannot get this to work and is there anyway to get dpkg forget about this freaking package. I tryed the method of editing the postint script and that did not work. I also changed my proxy settings and this did not work as well. Any help here ?

---

### Post by Rallg on 2009-03-28
Did you try it using Synaptic package manager?

---

### Post by dcstar on 2009-03-28
> **Rallg said:**
> Did you try it using Synaptic package manager?

Yep, the place where you can also simply change the proxy values so it will actually download and install.

---

### Post by Slim Odds on 2009-03-28
> [http://:8080/](http://:8080/)

Well that's not a very good proxy.

Go under System->Perferences->Network Proxy and choose something better....

---

