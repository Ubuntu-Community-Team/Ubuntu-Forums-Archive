---
title: "stuck while installing avant-window-navigator"
date: 2007-11-19
forum: Desktop Effects &amp; Customization
---

### Post by markster23 on 2007-11-19
I installed avant-window-navigator, but now when i try to go in to synaptic, i get a problem with broken packages, and it won't let me fix it.. and everytime i try to install a new package, it tells me to install libawn-bzr again.. over and over... i don't get it..
anybody ??


```

The following packages were automatically installed and are no longer required:
  python-alsaaudio libawn0 python-libgmail cairo-clock
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libawn-bzr
The following NEW packages will be installed:
  libawn-bzr
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/63.1kB of archives.
After unpacking, 180kB of additional disk space will be used.
Do you want to continue [Y/n]? Y 
(Reading database ... 127503 files and directories currently installed.)
Unpacking libawn-bzr (from .../libawn-bzr_0.2.0-bzr142-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libawn-bzr_0.2.0-bzr142-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn0
Errors were encountered while processing:
 /var/cache/apt/archives/libawn-bzr_0.2.0-bzr142-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by sethvath on 2007-11-19
Remove and purge AWN via synaptic and install it following this howto: 
[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

---

### Post by markster23 on 2007-11-19
thanks!!

---

