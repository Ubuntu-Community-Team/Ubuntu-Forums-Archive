---
title: "can't install package libgtk2.0-dev"
date: 2006-09-02
forum: Desktop Environments
---

### Post by sanderman on 2006-09-02
Right now I'm following a guide on how to get my Creative Zen mp3 player to work with in ubuntu with gnomad2.
I need to compile gnomad2 from the source and I need the package libgtk2.0-dev  among others.

when installing the package, I get errors, I don't have a clue what to do. There's some dependancy problem but I don't know what to do about it.

```

sander@Sauron:~$ sudo aptitude install libgtk2.0-dev
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  libgtk2.0-dev libpango1.0-dev
The following NEW packages will be automatically installed:
  libatk1.0-dev libcairo2-dev libexpat1-dev libfontconfig1-dev
  libfreetype6-dev libglib2.0-dev libpng12-dev libx11-dev libxau-dev
  libxcursor-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev
  libxi-dev libxinerama-dev libxrandr-dev libxrender-dev x-dev
  x11proto-core-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev
  x11proto-randr-dev x11proto-render-dev x11proto-xext-dev
  x11proto-xinerama-dev
The following NEW packages will be installed:
  libatk1.0-dev libcairo2-dev libexpat1-dev libfontconfig1-dev
  libfreetype6-dev libglib2.0-dev libpng12-dev libx11-dev libxau-dev
  libxcursor-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev
  libxi-dev libxinerama-dev libxrandr-dev libxrender-dev x-dev
  x11proto-core-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev
  x11proto-randr-dev x11proto-render-dev x11proto-xext-dev
  x11proto-xinerama-dev
0 packages upgraded, 29 newly installed, 0 to remove and 0 not upgraded.
Need to get 6751kB of archives. After unpacking 26.3MB will be used.
The following packages have unmet dependencies:
  libpango1.0-dev: Depends: libpango1.0-0 (= 1.12.2-0ubuntu3) but 1.12.3-0ubuntu3 is installed.
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.8.17-1ubuntu5) but 2.8.20-0ubuntu1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
libgtk2.0-dev [Not Installed]
libpango1.0-dev [Not Installed]

Score is 8

Accept this solution? [Y/n/q/?] y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done


```

---

### Post by varean on 2006-09-02
```
The following packages have unmet dependencies:
  libpango1.0-dev: Depends: libpango1.0-0 (= 1.12.2-0ubuntu3) but 1.12.3-0ubuntu3 is installed.
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.8.17-1ubuntu5) but 2.8.20-0ubuntu1 is installed.
```

Looks like its looking for an older version of ubuntu3, is your system all up to date? Try running apt-get update and try again.

---

### Post by leeyee on 2006-09-02
The same issue here, I've updated I think.
Here is my post: [http://www.ubuntuforums.org/showthread.php?t=249312](http://www.ubuntuforums.org/showthread.php?t=249312)

---

### Post by sanderman on 2006-09-02
I'm running on a relatively fresh install of ubuntu dapper with the latest updates so that won't be an issue, il try to it with the update.

nope, still no luck.


[edit]
Oh my god, i've messed with the packages so much that even sudo apt-get install -f wont fix it. :S

---

### Post by Perfect Storm on 2006-09-02
Do you have any unofficial sources in your sourcelist? Like Xgl and compiz repo?

---

### Post by leeyee on 2006-09-02
Nope, I don't have, here is my source.list
```

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://archive.ubuntu.org.cn/ubuntu-cn/ dapper main restricted universe multiverse

```

The problem seems that libgtk2.0-dev needs libcairo2.0-dev, while libcairo2.0-dev wants libcairo2 (= 1.0.4-0ubuntu1) to be installed but the current version of libcairo2 in Dapper is 1.2.0-0ubuntu1quinn2. 

After I forced the libcairo2 version to 1.0.4-0ubuntu1 in Synaptic, it works! So I assume that the problem might be caused by something weird packages you've installed, just find it out and force it to Dapper's version, then it works!

Hope this help :grin:

---

### Post by shunthemask on 2006-09-02
I had the same problem, and it was because compiz updated some packages without updating the -dev packages.  I got rid of compiz because it wasn't for me, but if you want to keep it, I would check out the compiz repositories to see if they have the updated -dev packages.

---

### Post by sanderman on 2006-09-03
A new day and new problems to solve...

Alright, I've tried 'fix broken packages' in synaptic and got this error:

```

E: /var/cache/apt/archives/libnjb5_2.2.4-3ubuntu3_i386.deb: trying to overwrite `/usr/lib/libnjb.so.5.1.0', which is also in package libnjb-2.2.5

```

my sources list is quite normal, apart from the sources for easyubuntu and wine so I don't think that's the problem.

---

### Post by sanderman on 2006-09-03
Well, after some messing with synaptic, the broken packages were finally fixed, apparrently, don't ask me how I did it, I honestly don't know. :roll:

so now will install gtk2.0-dev again but I get this error:

```
libgtk2.0-dev:
  Depends: libgtk2.0-0 (=2.8.17-1ubuntu5) but 2.8.20-0ubuntu1 is to be installed
 Depends: libpango1.0-dev but it is not going to be installed
```

how do I force installation of these packages?

---

### Post by leeyee on 2006-09-03
hmmm... the problem might be caused by libcairo2 package, you need to force its version to 1.0.4 I think.

Tell us if it helps.:-)

---

### Post by sanderman on 2006-09-03
Won't work, am I missing something here? ](*,) 
```

sander@Sauron:~$ sudo apt-get install libcairo2=1.0.4
Reading package lists... Done
Building dependency tree... Done
E: Version '1.0.4' for 'libcairo2' was not found

```

---

### Post by sanderman on 2006-09-05
bumb

---

### Post by Sewage on 2006-09-11
ouch i am having the same problem too~ it's making me pretty crazy. D:

---

### Post by zgornel on 2006-09-19
I think it's a problem with the version of libgtk2.0-0. The dev package requires the exact version 2.8.17. I may be wrong :D . However, this is a rather **important bug**, people can't compile gtk2 software without the lib. 
PS. I'm having the same problem with libcairo 1.0.4

---

