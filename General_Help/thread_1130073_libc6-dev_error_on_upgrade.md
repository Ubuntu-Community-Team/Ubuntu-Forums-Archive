---
title: "libc6-dev error on upgrade"
date: 2009-04-19
forum: General Help
---

### Post by bacchus101 on 2009-04-19
I am stuck in a loop. I was attempting to upgrade from Ubuntu 8.04LTS to 8.10.

Everything looked like it was going well, but then I received an error concerning libc6-dev and now I can't seem to fix it.

When running apt-get install I get the following error:

[PHP]# apt-get install
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.7-10ubuntu4) but 2.8~20080505-0ubuntu9 is installed[/PHP]


When running apt-get -f install I get the following error:

[PHP]# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc6-dev
Suggested packages:
  glibc-doc manpages-dev
The following packages will be upgraded:
  libc6-dev
1 upgraded, 0 newly installed, 0 to remove and 416 not upgraded.
Need to get 0B/2590kB of archives.
After this operation, 123kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 34453 files and directories currently installed.)
Preparing to replace libc6-dev 2.7-10ubuntu4 (using .../libc6-dev_2.8~20080505-0ubuntu9_amd64.deb) ...
Unpacking replacement libc6-dev ...
dpkg: error processing /var/cache/apt/archives/libc6-dev_2.8~20080505-0ubuntu9_amd64.deb (--unpack):
 unable to stat `./usr/share/man/man1/rpcgen.1.gz' (which I was about to install): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libc6-dev_2.8~20080505-0ubuntu9_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/PHP]


I can't seem to find my way out of this as no matter what I try, it always circles back to the inability to install libc6-dev.

Any ideas?

Thanks.

---

### Post by blazemore on 2009-04-19
.
Sorry wrong URL I'll find a different one watch this space

---

### Post by blazemore on 2009-04-19
Try doing 
```
sudo aptitude purge libc6
sudo aptitude install libc6-dev
```

---

### Post by bacchus101 on 2009-04-19
Thanks for the quick reply!

Unfortunately, it seems unable to purge the library.

Here is what I get upon entering sudo aptitude purge libc6:

[PHP]The following packages will be upgraded:
  libc6 libc6-dev
2 packages upgraded, 0 newly installed, 0 to remove and 416 not upgraded.
Need to get 0B/7444kB of archives. After unpacking 123kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Preconfiguring packages ...
(Reading database ... 34453 files and directories currently installed.)
Preparing to replace libc6-dev 2.7-10ubuntu4 (using .../libc6-dev_2.8~20080505-0ubuntu9_amd64.deb) ...
Unpacking replacement libc6-dev ...
dpkg: error processing /var/cache/apt/archives/libc6-dev_2.8~20080505-0ubuntu9_amd64.deb (--unpack):
 unable to stat `./usr/share/man/man1/rpcgen.1.gz' (which I was about to install): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace libc6 2.8~20080505-0ubuntu7 (using .../libc6_2.8~20080505-0ubuntu9_amd64.deb) ...
Unpacking replacement libc6 ...
Errors were encountered while processing:
 /var/cache/apt/archives/libc6-dev_2.8~20080505-0ubuntu9_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up libc6 (2.8~20080505-0ubuntu9) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done

[/PHP]

---

### Post by bacchus101 on 2009-04-19
I think I got myself into a good sized mess, lol.

I'll probably try and create a new image with the updated OS and move over the data, rather than upgrade.

I appreciate the help.

---

