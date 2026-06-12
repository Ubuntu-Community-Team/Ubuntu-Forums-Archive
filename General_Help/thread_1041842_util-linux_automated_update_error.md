---
title: "util-linux automated update error"
date: 2009-01-17
forum: General Help
---

### Post by Superkuh on 2009-01-17
**Pseudo-solved. Manually editing Errno.pm did work in allowing the util-linux package to install.**

I am on 8.04.1 64bit and during a recent automated update the package 'util-linux' failed.
> util-linux
Version 2.13.1-5ubuntu3: 
  * Disable the fallback clause when /dev/rtc cannot be opened. hwclock
    should not access the x86 RTC using I/O instructions unless explicitly
    requested from the command line (--directisa).
    LP: #274402
This package contains a number of important utilities, most of which are oriented towards maintenance of your system.
Some of the more important utilities included in this package allow you to partition your hard disk, view kernel messages, and create new filesystems.
I couldn't copy (the error text) from the auto-update inline terminal and didn't want to retype it. So I used util-linux from the cached file on disk in a regular terminal.

The automated update mentioned architecture issues so I thought I'd just force it, though this proved to be irrelevant.
> $ sudo dpkg -i --force-architecture /var/cache/apt/archives/util-linux_2.13.1-5ubuntu3_amd64.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libisc32
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  util-linux
1 upgraded, 0 newly installed, 0 to remove and 22 not upgraded.
1 not fully installed or removed.
Need to get 0B/462kB of archives.
After this operation, 0B of additional disk space will be used.
(Reading database ... 309684 files and directories currently installed.)
Preparing to replace util-linux 2.13.1-5ubuntu2 (using .../util-linux_2.13.1-5ubuntu3_amd64.deb) ...
**Errno architecture (x86_64-linux-gnu-thread-multi-2.6.15.7) does not match executable architecture (x86_64-linux-gnu-thread-multi-2.6.24-16-server) at /usr/local/share/perl/5.8.8/Errno.pm line 11.**
Compilation failed in require at /usr/sbin/install-info line 304.
BEGIN failed--compilation aborted at /usr/sbin/install-info line 304.
dpkg: warning - old pre-removal script returned error exit status 9
dpkg - trying script from the new package instead ...
Errno architecture (x86_64-linux-gnu-thread-multi-2.6.15.7) does not match executable architecture (x86_64-linux-gnu-thread-multi-2.6.24-16-server) at /usr/local/share/perl/5.8.8/Errno.pm line 11.
Compilation failed in require at /usr/sbin/install-info line 304.
BEGIN failed--compilation aborted at /usr/sbin/install-info line 304.
dpkg: error processing /var/cache/apt/archives/util-linux_2.13.1-5ubuntu3_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 9
Errno architecture (x86_64-linux-gnu-thread-multi-2.6.15.7) does not match executable architecture (x86_64-linux-gnu-thread-multi-2.6.24-16-server) at /usr/local/share/perl/5.8.8/Errno.pm line 11.
Compilation failed in require at /usr/sbin/install-info line 304.
BEGIN failed--compilation aborted at /usr/sbin/install-info line 304.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 9

Can I just change Errno.pm to pass the test? (temporarily)
This is /usr/local/share/perl/5.8.8/Errno.pm :
```
#
# This file is auto-generated. ***ANY*** changes here will be lost
#

package Errno;
our (@EXPORT_OK,%EXPORT_TAGS,@ISA,$VERSION,%errno,$AUTOLOAD);
use Exporter ();
use Config;
use strict;

"$Config{'archname'}-$Config{'osvers'}" eq
"x86_64-linux-gnu-thread-multi-2.6.15.7" or
	die "Errno architecture (x86_64-linux-gnu-thread-multi-2.6.15.7) does not match executable architecture ($Config{'archname'}-$Config{'osvers'})";
```
For example:
```
"$Config{'archname'}-$Config{'osvers'}" eq
**"x86_64-linux-gnu-thread-multi-2.6.24-16-server"** or
	die "Errno architecture (x86_64-linux-gnu-thread-multi-2.6.15.7) does not match executable architecture ($Config{'archname'}-$Config{'osvers'})";
```

---

