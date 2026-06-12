---
title: "Trouble installing pure-ftpd"
date: 2006-07-31
forum: Desktop Environments
---

### Post by aaronshaf on 2006-07-31
When I run apt-get install pure-ftpd, I get this:

```
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  netkit-inetd openbsd-inetd xinetd
The following NEW packages will be installed:
  pure-ftpd
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 150kB of archives.
After unpacking 463kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com dapper/universe pure-ftpd 1.0.21-1ubuntu4 [150kB]
Fetched 150kB in 0s (193kB/s)
Selecting previously deselected package pure-ftpd.
(Reading database ... 16259 files and directories currently installed.)
Unpacking pure-ftpd (from .../pure-ftpd_1.0.21-1ubuntu4_i386.deb) ...
Setting up pure-ftpd (1.0.21-1ubuntu4) ...
Starting ftp server: Running: /usr/sbin/pure-ftpd -l pam -u 1000 -E -O clf:/var/log/pure-ftpd/transfer.log -B
invoke-rc.d: initscript pure-ftpd, action "start" failed.
dpkg: error processing pure-ftpd (--configure):
 subprocess post-installation script returned error exit status 252
Errors were encountered while processing:
 pure-ftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas?

---

### Post by aaronshaf on 2006-07-31
No ideas?

---

### Post by EricFitchett on 2007-08-23
Hi, I know this is really late, but I encountered this problem and found a solution.

I ran an strace of the pure-ftpd process, and found that it didn't have permission to reduce its capabilities using the capset function (even though I was running sudo):
```
capset(0x19980330, 0, {CAP_CHOWN|CAP_DAC_READ_SEARCH|CAP_SETGID|CAP_SETUID|CAP_NET_BIND_SERVICE|CAP_NET_ADMIN|CAP_SYS_CHROOT|CAP_SYS_NICE, CAP_CHOWN|CAP_DAC_READ_SEARCH|CAP_SETGID|CAP_SETUID|CAP_NET_BIND_SERVICE|CAP_NET_ADMIN|CAP_SYS_CHROOT|CAP_SYS_NICE, 0}) = -1 EPERM (Operation not permitted)
```

Apparently I needed to insert a module into the kernel, but I was unable to do so as I was running under a VPS.
I found the following forum thread, and decided to ask my hosting company about the problem:
[http://www.unixshell.com/forum/archive/index.php/t-353.html](http://www.unixshell.com/forum/archive/index.php/t-353.html)

They were able to fix it, no problem - took a few hours for them to get to me, then a quick reboot and I was ready to go.
Good luck.

-Eric

---

