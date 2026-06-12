---
title: "Sub-process gzip returned an error code (1)"
date: 2006-06-05
forum: Desktop Environments
---

### Post by dajomu on 2006-06-05
Can anyone help me out to find out what the problem is with my kubuntu installation?

This is my repos:
```

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free
```

This is the error messages I get:

```

Get:10 http://archive.ubuntu.com dapper/multiverse Packages [121kB]
Get:11 http://archive.ubuntu.com dapper-updates/main Packages [6221B]
95% [10 Packages gzip 0] [5 Packages bzip2 3465216]                                                                            321kB/s 0s
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com dapper/multiverse Packages
  Sub-process gzip returned an error code (1)
95% [11 Packages gzip 0] [5 Packages bzip2 3465216]                                                                            321kB/s 0s
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com dapper-updates/main Packages
  Sub-process gzip returned an error code (1)
Fetched 1878kB in 14s (129kB/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.Get:10 http://archive.ubuntu.com dapper/multiverse Packages [121kB]
Get:11 http://archive.ubuntu.com dapper-updates/main Packages [6221B]
95% [10 Packages gzip 0] [5 Packages bzip2 3465216]                                                                            321kB/s 0s
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com dapper/multiverse Packages
  Sub-process gzip returned an error code (1)
95% [11 Packages gzip 0] [5 Packages bzip2 3465216]                                                                            321kB/s 0s
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com dapper-updates/main Packages
  Sub-process gzip returned an error code (1)
Fetched 1878kB in 14s (129kB/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by pellgarlic on 2006-06-09
try changing your sources.list so that wherever it says "http://" instead, put "ftp://" 
(credit to xurizaemon: [http://ubuntuforums.org/showthread.php?t=9944&highlight=gzip+bzip2+error](http://ubuntuforums.org/showthread.php?t=9944&highlight=gzip+bzip2+error))

if that doesn't help, try reading my post here: [http://ubuntuforums.org/showthread.php?p=1115981#post1115981](http://ubuntuforums.org/showthread.php?p=1115981#post1115981)

hope one of these works for you...

---

### Post by dr_d on 2007-02-24
want to fix this? don't want to change to ftp? here's how:

[http://ubuntuforums.org/showthread.php?t=369001](http://ubuntuforums.org/showthread.php?t=369001)

enjoy :popcorn:

---

### Post by deadgoon on 2007-04-20
> **dr_d said:**
> want to fix this? don't want to change to ftp? here's how:

[http://ubuntuforums.org/showthread.php?t=369001](http://ubuntuforums.org/showthread.php?t=369001)

enjoy :popcorn:

Worked like a charm.. thanks!

---

### Post by sars on 2007-08-07
A better solution (and reason)

[http://www.webservertalk.com/archive291-2006-2-1394937.html](http://www.webservertalk.com/archive291-2006-2-1394937.html)

"
# ls /var/lib/apt/lists/partial/
 
 Delete any files you see there and run apt-get update again.
"

---

### Post by Thomas Barregren on 2007-08-17
As described at [http://www.barregren.se/node/10]("http://www.barregren.se/blog/sub-process-gzip-returned-error-code-1")   just do following:

```

sudo rm /var/lib/apt/lists/partial/*

```

---

