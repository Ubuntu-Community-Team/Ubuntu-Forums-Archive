---
title: "Upgrade failing - apport"
date: 2009-05-10
forum: General Help
---

### Post by ryanfx on 2009-05-10
Hello everyone,

I'm having an issue upgrading my box running several services to my network.  I do not know enough to provide relevant information off the top of my head so just ask for a specific file or output of command and I will post up the results ASAP.

The following is what happens when I try to update the machine:

```

ryan@esiserver:~$ sudo apt-get upgrade
[sudo] password for ryan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apport
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
25 not fully installed or removed.
Need to get 0B/108kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 153600 files and directories currently installed.)
Preparing to replace apport 0.119 (using .../apport_0.119.2_all.deb) ...
Unpacking replacement apport ...
update-mime-database: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
update-mime-database: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64
dpkg: error processing /var/cache/apt/archives/apport_0.119.2_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 127
update-mime-database: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/apport_0.119.2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I tried to remove apport and the following happens:

```

ryan@esiserver:~$ sudo apt-get remove apport
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  x11vnc xvnc4viewer smbfs libvncserver0 expect tcl8.4
  freenx-session-launcher
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  apport
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
25 not fully installed or removed.
After this operation, 500kB disk space will be freed.
Do you want to continue [Y/n]? Y
dpkg: error processing apport (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 apport
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Yellow Pasque on 2009-05-10
I hope your hard disk and RAM are OK. :/ My (64-bit) system seems to have the gzopen64 symbol in libxml2.so.2 Check your links in /usr/lib
```
/usr/lib$ ls -la | grep libxml2.so.2
lrwxrwxrwx   1 root root       17 2009-04-24 00:30 libxml2.so -> libxml2.so.2.6.32
lrwxrwxrwx   1 root root       17 2009-04-23 22:47 libxml2.so.2 -> libxml2.so.2.6.32
-rw-r--r--   1 root root  1425368 2009-04-08 17:01 libxml2.so.2.6.32
```

```
/usr/lib$ strings libxml2.so.2.6.32 | grep gz
gzopen64
...
```

---

### Post by ryanfx on 2009-05-10
```

ryan@esiserver:/usr/lib$ ls -la | grep libxml2.so.2
lrwxrwxrwx   1 root root       17 2009-01-02 22:25 libxml2.so.2 -> libxml2.so.2.6.32
-rw-r--r--   1 root root  1286600 2008-11-18 14:24 libxml2.so.2.6.32
ryan@esiserver:/usr/lib$ strings libxml2.so.2.6.32 | grep gz
gzopen64
gzdopen
gzread
gzrewind
gzclose
gzwrite
gzclose()
gzwrite()
Content-Encoding: gzip
gzread()
Accept-Encoding: gzip

```

Any help?

---

### Post by Yellow Pasque on 2009-05-10
A similar bug report:
[https://bugs.launchpad.net/ubuntu/+source/libxml2/+bug/151045](https://bugs.launchpad.net/ubuntu/+source/libxml2/+bug/151045)

You might also try running ldconfig and then reinstalling apport:
```
sudo ldconfig
sudo apt-get --reinstall install apport
```

---

### Post by ryanfx on 2009-05-10
> **Temüjin said:**
> A similar bug report:
[https://bugs.launchpad.net/ubuntu/+source/libxml2/+bug/151045](https://bugs.launchpad.net/ubuntu/+source/libxml2/+bug/151045)

You might also try running ldconfig and then reinstalling apport:
```
sudo ldconfig
sudo apt-get --reinstall install apport
```

so just ```
sudo ldconfig
``` ??

I tried that, attempted to reinstall, and nothing changed =/

---

### Post by ryanfx on 2009-05-10
update:

```

ryan@esiserver:/usr/local/lib$ objdump -T /usr/lib/libxml2.so.2.6.32 | grep gzopen64
00000000      DF *UND*	00000000              gzopen64


```


it looks like my library is missing a symbol to gzopen64 ???

---

### Post by Yellow Pasque on 2009-05-10
From this thread:
[http://www.webservertalk.com/archive99-2008-1-2280879.html](http://www.webservertalk.com/archive99-2008-1-2280879.html)

You might have a local version of libz in /usr/local/lib. Remove that and then run the sudo ldconfig

---

### Post by ryanfx on 2009-05-10
> **Temüjin said:**
> From this thread:
[http://www.webservertalk.com/archive99-2008-1-2280879.html](http://www.webservertalk.com/archive99-2008-1-2280879.html)

You might have a local version of libz in /usr/local/lib. Remove that and then run the sudo ldconfig

ding ding ding :)

thanks a ton!

---

