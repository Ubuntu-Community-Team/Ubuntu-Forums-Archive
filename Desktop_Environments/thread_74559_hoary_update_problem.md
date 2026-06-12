---
title: "hoary update problem??"
date: 2005-10-12
forum: Desktop Environments
---

### Post by fei on 2005-10-12
When I run "apt-get upddate" from the command line, I've got the following errer:
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Fetched 46.6kB in 10s (4325B/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/binary-i386/Packages.gz)  MD5Sum mismatch
Reading package lists... Done
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.



I also tried using Synaptic. It has the same problem. Can anyone help me to solve this problem? Thanks in advance!!

---

### Post by Pablo_Escobar on 2005-10-12
Could You post your /etc/apt/sources.list file here ? We'll try to hunt down the problem.

---

### Post by fei on 2005-10-12
This is my sources.list:
```

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb http://nz.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://nz.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nz.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://nz.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://nz.archive.ubuntu.com/ubuntu hoary universe
deb-src http://nz.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

# for downloading realplayer
# This is the old backports. Been replaced by the new server below.
#deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
#deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

# The new Official Backports
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted

#deb http://archive.ubuntu.org.cn/ubuntu hoary main restricted universe multiverse
#deb http://archive.ubuntu.org.cn/ubuntu hoary-security main restricted universe multiverse
#deb http://archive.ubuntu.org.cn/ubuntu hoary-updates main restricted universe multiverse
#deb http://archive.ubuntu.org.cn/ubuntu-cn ubuntu.org.cn main universe multiverse restricted
#deb http://archive.ubuntu.org.cn/backports hoary-backports main universe multiverse restricted
#deb http://archive.ubuntu.org.cn/backports hoary-extras main universe multiverse restricted

```

Thanks for your help!

---

### Post by Pablo_Escobar on 2005-10-12
It seems ok.
Maybe try to comment out the backports. 

And if this doesn't help, try to stay clear off Synaptic for this Breezy release period. Mabye the servers are being prepeared for heavy traffic and something can be not 100% right.

---

### Post by fei on 2005-10-12
IT's working fine now. I think the problem was what you said that the server was busy. 

Ubuntu is so popular now. But, why there is only one backports server??

---

