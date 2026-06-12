---
title: "Installed libpod by hand, now synaptic wants to install it again"
date: 2006-04-10
forum: Desktop Environments
---

### Post by Anagonda on 2006-04-10
Ok, so the problem is that I installed by hand(right words?) gtkpod, libpod etc.
Now every time I try to upgrade or install something from synaptic(apt-get) it tries to install libpod. If I search for libpod from synaptic I found that it's allready installed and no upgrades are available.
So why does it try to install it allways? And what can I do to stop it? This really sucks, coz every upgrade or software install stops in a error message that it can't install libpod because its allready installed. Sometimes it doesn't install everything before error message so I must install the same things many times before I get everything I want.

---

### Post by Anagonda on 2006-04-10
Ok, now it broke the hole system. Hadn't noticed that last few dist-upgrades didn't go right. It only downloaded the packages and then hang on the libgpod error. But now it installed newest nvidia drivers! But nothing else. And the drivers where for newer kernel...

So had to do apt-get remove for gtkpod to get the system up again...

---

### Post by morrisonpeter on 2006-07-26
I seem to have the same problem, when I type "sudo apt-get install-f" in the console, I get:

> Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libgpod0
Recommended packages:
  libgpod-common
The following NEW packages will be installed:
  libgpod0
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/64.2kB of archives.
After unpacking, 188kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 175288 files and directories currently installed.)
Unpacking libgpod0 (from .../libgpod0_0.3.2-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libgpod0_0.3.2-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libgpod.so.0', which is also in package libgpod
Errors were encountered while processing:
 /var/cache/apt/archives/libgpod0_0.3.2-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Anyone have any idea how to fix this?

---

### Post by ifokkema on 2006-07-29
> **morrisonpeter said:**
> Anyone have any idea how to fix this?
OK, first of all, be careful with the solution I bring you. There's obviously a bug in one of the two packages, and this will force the installation of libgpod0 to overwrite other packages' files. If libgpod0 is installed properly, you can go ahead and install other packages the normal way.

```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/libgpod0_0.3.2-0ubuntu1_i386.deb
```

---

