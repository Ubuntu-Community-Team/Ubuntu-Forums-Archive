---
title: "Broken locales after bad install"
date: 2006-07-22
forum: Desktop Environments
---

### Post by JeffreyRatcliffe on 2006-07-22
I just tried installing to Dapper the version of hplip from Edgy, hoping to sort out some printer issues I am having. Unfortunately, there were a load of dependencies and one of them broke my locales. So I'd like it back as it was. 

The Synaptic log in question is:

```
Removed the following packages:
hplip-ppds

Upgraded the following packages:
foomatic-filters-ppds (20060406-0ubuntu1) to 20060530-2
gcc-4.1-base (4.1.1-2) to 4.1.1-9ubuntu1
hpijs (2.1.7+0.9.7-4ubuntu1) to 2.1.10+0.9.11-2ubuntu4
hplip (0.9.7-4ubuntu1) to 0.9.11-2ubuntu4
hplip-data (0.9.7-4ubuntu1) to 0.9.11-2ubuntu4
libc6 (2.3.6-15) to 2.4-1ubuntu6
libc6-dev (2.3.6-15) to 2.4-1ubuntu6
libc6-i686 (2.3.6-15) to 2.4-1ubuntu6
libffi4 (4.1.1-2) to 4.1.1-9ubuntu1
libffi4-dev (4.1.1-2) to 4.1.1-9ubuntu1
libgcc1 (1:4.0.3-1ubuntu5) to 1:4.1.1-9ubuntu1
libsnmp-base (5.2.1.2-4ubuntu2) to 5.2.2-4ubuntu1
libsnmp9 (5.2.1.2-4ubuntu2) to 5.2.2-4ubuntu1
libssl0.9.8 (0.9.8a-7build1) to 0.9.8b-2
libstdc++6 (4.0.3-1ubuntu5) to 4.1.1-9ubuntu1
libusb-0.1-4 (2:0.1.10a-22ubuntu1) to 2:0.1.12-2
sysv-rc (2.86.ds1-6ubuntu32) to 2.86.ds1-14.1ubuntu2
xbase-clients (7.0.0-0ubuntu45) to 1:1.1
xfonts-100dpi (6.8.2.1-5) to 1:1.0.0-2
xfonts-75dpi (6.8.2.1-5) to 1:1.0.0-2
xfonts-base (6.8.2.1-5) to 1:1.0.0-3
xfonts-scalable (6.8.2.1-5) to 1:1.0.0-4
xutils (7.0.0-0ubuntu45) to 1:1.1

Installed the following packages:
hpijs-ppds (2.1.10+0.9.11-2ubuntu4)
python-central (0.5.1)
xkb-data (0.8-7ubuntu1)
```

I've played with things like ```
apt-get install package=version
``` and aptitude to no avail. Anybody got any good ideas?

Thanks

Jeff

---

### Post by mlind on 2006-07-22
```

sudo aptitude install hplip=0.9.7-4ubuntu1

```

doesnt work?

You can use alternatively do aptitude download hplip=0.9.7-4ubuntu1
and use dpkg -i to install the package.

---

### Post by JeffreyRatcliffe on 2006-07-22
> **mlind said:**
> ```

sudo aptitude install hplip=0.9.7-4ubuntu1

```

doesnt work?

Well, it reinstalls hplip 0.9.7-4ubuntu1, but my locales are still broken.

However, you put me on the right track. My guess was that libc6 was the guilty package, but ```
sudo aptitude install libc6=2.3.6-15
``` complained that it couldn't find it. Stupidly, the quick answer didn't click, and I took it all back to 2.3.6-0ubuntu20, forcing the deinstall of GnuCash 2, which I reinstalled from Sid, giving me back 2.3.6-15.

Of course, I should have just activated Sid in sources.lst and gone straight for 2.3.6-15.

Now everything seems fine.

Thanks for the help.

---

### Post by mlind on 2006-07-22
> **JeffreyRatcliffe said:**
> Well, it reinstalls hplip 0.9.7-4ubuntu1, but my locales are still broken.

However, you put me on the right track. My guess was that libc6 was the guilty package, but ```
sudo aptitude install libc6=2.3.6-15
``` complained that it couldn't find it. Stupidly, the quick answer didn't click, and I took it all back to 2.3.6-0ubuntu20, forcing the deinstall of GnuCash 2, which I reinstalled from Sid, giving me back 2.3.6-15.

Of course, I should have just activated Sid in sources.lst and gone straight for 2.3.6-15.

Now everything seems fine.

Thanks for the help.

IMO libc6 is a package that you shouldn't upgrade or you may cause very big mess with other package that are built against current dapper libc6, which is 2.3.6-0ubuntu20.
If you need some packages from debian unstable, just rebuild it yourself. Against Dapper's libc6.


As libc6 description say, almost all other programs use it too..
```

Contains the standard libraries that are used by nearly all programs on
the system. This package includes shared versions of the standard C library
and the standard math library, as well as many others. Timezone data is also included.

```

---

### Post by JeffreyRatcliffe on 2006-07-24
I discovered after rebooting that X was also broken. I've learned a lesson here...

Thanks to Knoppix I could dig out the version numbers of the offending packages from my post above and repair them as above with aptitude from the console without X.

---

