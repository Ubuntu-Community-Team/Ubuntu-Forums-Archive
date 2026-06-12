---
title: "Problem when installing VMware-Server"
date: 2008-03-28
forum: Desktop Environments
---

### Post by bdcheung on 2008-03-28
So when installing vmware-server from the terminal, I get the following error:

```
bdcheung@bdcheung-laptop:~$ sudo apt-get install vmware-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  vmware-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/79.4MB of archives.
After unpacking 131MB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 125575 files and directories currently installed.)
Unpacking vmware-server (from .../vmware-server_1.0.4-1gutsy2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/vmware-server_1.0.4-1gutsy2_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/vmware-server_1.0.4-1gutsy2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Any idea what's going on?

---

### Post by warp99 on 2008-03-28
I'm not sure, first I would run

```
sudo apt-get -f install
```

to removed a failed install then remove the package from the archive

```
sudo rm /var/cache/apt/archives/vmware-server_1.0.4-1gutsy2_i386.deb
```

and try to load the package again. If that fails you can download the package then install it using:

```
sudo dpkg -i vmware-server_1.0.4-1gutsy2_i386.deb
```

BTW that package is not from the Ubuntu repositories so a number of problems may be happening. :(

---

### Post by bdcheung on 2008-03-29
That worked, thanks!

---

### Post by th3dark1 on 2008-04-30
I just saw this thread and I'm having the same issue:

The following NEW packages will be installed:
  vmware-server
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 79.4MB of archives.
After unpacking 131MB of additional disk space will be used.
Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner vmware-server 1.0.4-1gutsy2 [79.4MB]
Fetched 79.4MB in 1m16s (1039kB/s)                                                                   
Preconfiguring packages ...
(Reading database ... 95675 files and directories currently installed.)
Unpacking vmware-server (from .../vmware-server_1.0.4-1gutsy2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/vmware-server_1.0.4-1gutsy2_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/vmware-server_1.0.4-1gutsy2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
foo@foo-desktop:/var/cache/apt/archives$ 


The exception is that the solution above didn't work for me... Any ideas?

thanks,

---

### Post by yukunix on 2008-06-17
> **th3dark1 said:**
> I just saw this thread and I'm having the same issue:

The following NEW packages will be installed:
  vmware-server
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 79.4MB of archives.
After unpacking 131MB of additional disk space will be used.
Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner vmware-server 1.0.4-1gutsy2 [79.4MB]
Fetched 79.4MB in 1m16s (1039kB/s)                                                                   
Preconfiguring packages ...
(Reading database ... 95675 files and directories currently installed.)
Unpacking vmware-server (from .../vmware-server_1.0.4-1gutsy2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/vmware-server_1.0.4-1gutsy2_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/vmware-server_1.0.4-1gutsy2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
foo@foo-desktop:/var/cache/apt/archives$ 


The exception is that the solution above didn't work for me... Any ideas?

thanks,


Try to reconfigure first

$ sudo dpkg-reconfigure vmware-server

---

