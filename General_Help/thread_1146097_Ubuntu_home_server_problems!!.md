---
title: "Ubuntu home server problems!!"
date: 2009-05-02
forum: General Help
---

### Post by renegadeandy on 2009-05-02
Hey guys!

I have been running a home server of ubuntu 7.10 for quite a while.

Today I come along and want to install lynx for a new cron job and this happens

```

andy@server:~$ sudo apt-get install lynx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  php-db
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed
  lynx
0 upgraded, 1 newly installed, 0 to remove and 19 not upgraded.
Need to get 1166kB of archives.
After unpacking 4977kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  lynx
Install these packages without verification [y/N]? y
Err http://gb.archive.ubuntu.com gutsy/main lynx 2.8.6-2ubuntu1
  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/l/lynx/lynx_2.8.6-2ubuntu1_i386.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

So i try apt-get update and I get about 100 404 errors.

So what is the solution and why is this happening.

I cannot even attempt a distro upgrade because doing sudo apt-get dist-upgrade fails with the same 404s!

Thanks,

Andy

---

### Post by dabang on 2009-05-02
See this:
[http://www.ubuntulinux.org/news/ubuntu-7.10-eol](http://www.ubuntulinux.org/news/ubuntu-7.10-eol)

If you have a look at [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu), you won't find Gutsy anymore...

I guess it's time to upgrade! If you need a long term support, go for Ubuntu 8.04 or Debian Lenny (I'd recommend the last if you want to run a server).

---

### Post by renegadeandy on 2009-05-02
dam- started updating to 8.10 i think.

How do i go about changing it to your recommendation for the server after its done?

---

### Post by dabang on 2009-05-02
> How do i go about changing it to your recommendation for the server after its done?

That's not quite what I meant...
If you want to stick to Ubuntu, grab one of the server install CDs (I think they don't install a desktop as default) *or* go for Debian Lenny, which is very stable and supported for a long time. Either way, it's going to be a clean new install.
You could of course try and update Ubuntu 7.10 to the latest version, but I have no experiences with that. It should work though! ;-)

---

### Post by FluffyElmo on 2009-05-02
You should be fine just doing an upgrade to a more current version. I've updated my system with each release and have had no problems. Ubuntu and Debian are extremely similar, I don't think there is enough of a difference to justify a re-install. Just my two cents:)

---

