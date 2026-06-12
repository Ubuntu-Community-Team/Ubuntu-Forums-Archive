---
title: "Anybody elses apt slow?"
date: 2006-07-16
forum: Desktop Environments
---

### Post by staulkor on 2006-07-16
I just did an apt-upgrade and it was downloading extremly slow. I have FiOS and I usually get about 1800-1850 kB/s and now im only getting about 100kB/s.

Here is my sources.list:

```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

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

```

Also, I have tested my download speeds while downloading from the repositories and my speed is what it should be; ~1800kB/s.

---

### Post by bluecherry on 2006-07-16
Try generating a localised version of the sources.list at:
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic).

Make sure you fill in the 2-letter country code, this way you will connect to  a local mirror.

I don't know where you're at but a traceroute from my pc shows archive.ubuntu.com is located in the UK. (might be loadbalanced depending on location, i don't know)

---

