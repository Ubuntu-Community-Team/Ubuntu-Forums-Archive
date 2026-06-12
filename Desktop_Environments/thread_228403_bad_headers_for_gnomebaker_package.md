---
title: "bad headers for gnomebaker package"
date: 2006-08-03
forum: Desktop Environments
---

### Post by rvbhute on 2006-08-03
I'm trying to install gnomebaker. But I'm getting errors related to "bad headers" - both through Synaptic and from the command line - for the last three days. I tried installing other packages (a2ps) which went through perfectly. Can anyone tell me what is the problem? My repositories are <archives.ubuntu.com>.

Also, while running apt-get update, I get various status messages. What do "Ign", "Hit" mean? Are they different from a total success?

---

### Post by philippe_carlo on 2006-08-03
Can you post the contents of your /etc/apt/sources.list file?

---

### Post by rvbhute on 2006-08-03
My sources.list file
```

## install cdrom
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

## internet repostitory
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
# deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

## security updates
# deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

```

"sudo apt-get install gnomebaker" gives following.
```

rohit@bhute:~$ sudo apt-get install gnomebaker
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libgstreamer0.8-0
Suggested packages:
  gstreamer0.8-tools gstreamer0.8-plugins
Recommended packages:
  gstreamer0.8-mad gstreamer0.8-flac gstreamer0.8-vorbis
The following NEW packages will be installed:
  gnomebaker libgstreamer0.8-0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1562kB of archives.
After unpacking 5214kB of additional disk space will be used.
Do you want to continue [Y/n]?
Err http://archive.ubuntu.com dapper/universe libgstreamer0.8-0 0.8.12-1ubuntu1
  Bad header line
Err http://archive.ubuntu.com dapper/universe gnomebaker 0.5.1-0ubuntu1
  Got a single header line over 360 chars
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.8/libgstreamer0.8-0_0.8.12-1ubuntu1_i386.deb  Bad header line
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/g/gnomebaker/gnomebaker_0.5.1-0ubuntu1_i386.deb  Got a single header line over 360 chars
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Tried both suggestions.

---

