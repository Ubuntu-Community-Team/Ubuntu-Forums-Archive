---
title: "Dependency hell or libvte issue? Problems with broken packages."
date: 2006-09-06
forum: Desktop Environments
---

### Post by faceoftheearth on 2006-09-06
I have compiz-quinn and am running cgwd. I noticed the sticky about libvte breaking synaptic but they never really say what broken is. I assume they mean synaptic will no longer start so my problem is different. I could be wrong. Basically I have two broken packages, cwgd and csm. I have been trying to trace the dependency issues back but it is circular.E.G. cgwd depends on compiz-something which depends on something else CSM has no description so I'm not sure what it is, but CGWD will not fix. I have attached the results of an apt-get -f install. I think it has something to do with using the non-approved repos but is there a solution at least so that I can update my system?

Thanks!

```
The following extra packages will be installed:
  compiz-core compiz-plugins
The following NEW packages will be installed:
  compiz-core compiz-plugins
0 upgraded, 2 newly installed, 0 to remove and 15 not upgraded.
3 not fully installed or removed.
Need to get 0B/718kB of archives.
After unpacking 3138kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 130170 files and directories currently installed.)
Unpacking compiz-core (from .../compiz-core_0.0.13.45-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-core_0.0.13.45-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/bin/compiz', which is also in package compiz
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking compiz-plugins (from .../compiz-plugins_0.16-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-plugins_0.16-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libshowdesktop.so', which is also in package compiz
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-core_0.0.13.45-0ubuntu1_i386.deb
 /var/cache/apt/archives/compiz-plugins_0.16-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Anduu on 2006-09-06
There just might be a temporary problem with Quinns repo...ie not all the files are available yet.Time should correct this.

If you aren't gettting other updates because of this you can just comment out Quinns repos in /etc/apt/sources.list the do an apt-get update/upgrade then change your sources.list back.

---

### Post by faceoftheearth on 2006-09-07
Sweet, that commenting thing might be just the thing for which I'm looking. At least that way I can update the system without trying to figure out the mess with broken packages. 

Thanks!

---

