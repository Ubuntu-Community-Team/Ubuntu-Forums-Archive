---
title: "stuck when apt-get compiz"
date: 2007-04-02
forum: Desktop Effects &amp; Customization
---

### Post by aaronfromchina on 2007-04-02
Hi,

I'd like to install compiz on dapper. I've followed the wiki and got XGL worked. but cann't install compiz. 

```

sudo apt-get install compiz compiz-gnome compiz-plugins compiz-core csm
Reading package lists... Done
Building dependency tree... Done
Package csm is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package csm has no installation candidate
```

I've used the following sources in /etc/apt/source.list

```

deb http://cn.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb http://cn.archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb http://cn.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb http://cn.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb http://mirror.lupaworld.com/ubuntu/ubuntu-cn dapper main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://cn.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://cn.archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://cn.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://cn.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

# ClearType patches
deb http://www.elisanet.fi/mlind/ubuntu dapper fonts
deb-src http://www.elisanet.fi/mlind/ubuntu dapper fonts

## XGL and alglx
#deb http://media.blutkind.org/xgl/  dapper main aiglx
deb http://www.beerorkid.com/compiz dapper main aiglx
#deb http://ubuntu.compiz.net/  dapper main aiglx

#Backports
deb http://archive.ubuntu.com/ubuntu dapper-backports main universe multiverse restricted

deb http://www.beerorkid.com/compiz dapper main
deb http://xgl.compiz.info/ dapper main
```

My video card is: Ndivia Geforce 5900.

How to get compiz installed? 
Thank you!

---

### Post by aaronfromchina on 2007-04-02
I guess that the compiz version I want to 'apt-get' is too old. It cannot be found in current repository.

Any idea?!

---

