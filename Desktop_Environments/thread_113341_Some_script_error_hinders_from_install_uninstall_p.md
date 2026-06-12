---
title: "Some script error hinders from install uninstall proftpd"
date: 2006-01-06
forum: Desktop Environments
---

### Post by martinjanson on 2006-01-06
I get the error

```
E: /var/cache/apt/archives/proftpd_1.2.10-22_i386.deb: subprocess new pre-removal script returned error exit status 100

```

When I try to remove, or re install proftpd via synaptic. Any tips how to fix this?

```

Preconfiguring packages ...
(Reading database ... 56961 files and directories currently installed.)
Preparing to replace proftpd 1.2.10-22 (using .../proftpd_1.2.10-22_i386.deb) ...
invoke-rc.d: unknown initscript, /etc/init.d/proftpd not found.
dpkg: warning - old pre-removal script returned error exit status 100
dpkg - trying script from the new package instead ...
invoke-rc.d: unknown initscript, /etc/init.d/proftpd not found.
dpkg: error processing /var/cache/apt/archives/proftpd_1.2.10-22_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 100

```

And then I try apt-get remove proftpd and I get the error

```
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  proftpd proftpd-common
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 1507kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 56960 files and directories currently installed.)
Removing proftpd ...
invoke-rc.d: unknown initscript, /etc/init.d/proftpd not found.
dpkg: error processing proftpd (--remove):
 subprocess pre-removal script returned error exit status 100
dpkg: proftpd-common: dependency problems, but removing anyway as you request:
 proftpd depends on proftpd-common (= 1.2.10-22).
Removing proftpd-common ...
Errors were encountered while processing:
 proftpd
E: Sub-process /usr/bin/dpkg returned an error code (1
```

---

### Post by martinjanson on 2006-01-06
Never mind, got it working now.

---

### Post by Fillepe on 2006-01-13
Would you care to elaborate on how you solved the problem as I have a similar one with nautilus after a fresh brezzy install and an apt-get upgrade...

---

### Post by martinjanson on 2006-03-12
Sorry, cant recall what I did

---

### Post by tofuconfetti on 2006-11-04
I just worked through this one and thought I'd share.  It was a DNS issue.  The setup script couldn't discern the IP address of the computer.  What I did was set the IP address to static (I always do that anyway) and entered the name as it appears in the network configuration dialogue in /etc/hosts like this ...

  192.168.1.30 eft64.mynet.net  eft64

then I uninstalled it and reinstalled it and viola! no error.

Hope that helps.

---

