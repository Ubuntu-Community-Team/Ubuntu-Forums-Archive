---
title: "Software Update question"
date: 2005-10-26
forum: Desktop Environments
---

### Post by Kirzzy_Boy on 2005-10-26
I just recieved an update notice on my system and opened it to install. I checked the Changes and Description tabs as I always do and found the following info:

UPDATE:
libgl1-mesa
libgl1-mesa-dri
libgu1-mesa

CHANGES:
Version 6.3.2-0ubuntu6breezy1: 

  * Really, seriously, don't optimise DRI driver builds on i386 (closes:
    Ubuntu#15036).

Is it advisable to install or not

---

### Post by GeneralZod on 2005-10-26
More than advisable - go for it! :)

---

### Post by Kirzzy_Boy on 2005-10-26
Thx a mill.... ;)

---

### Post by Single on 2005-10-26
I got the following erros while trying to upgrade:

ng@u053691m:~$ sudo apt-get upgrade libgl1-mesa
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libgl1-mesa-dev: Depends: libgl1-mesa (= 6.3.2-0ubuntu6breezy1) but 6.3.2-0ubuntu6 is installed
  libgl1-mesa-dri: Depends: libgl1-mesa (= 6.3.2-0ubuntu6breezy1) but 6.3.2-0ubuntu6 is installed
E: Unmet dependencies. Try using -f.


ng@u053691m:~$ sudo apt-get -f upgrade libgl1-mesa
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be upgraded:
  libgl1-mesa
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B/282kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 106871 files and directories currently installed.)
Preparing to replace libgl1-mesa 6.3.2-0ubuntu6 (using .../libgl1-mesa_6.3.2-0ubuntu6breezy1_i386.deb) ...
Unpacking replacement libgl1-mesa ...
dpkg: error processing /var/cache/apt/archives/libgl1-mesa_6.3.2-0ubuntu6breezy1_i386.deb (--unpack):
 unable to create `./usr/lib/libGL.so.1.2': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libgl1-mesa_6.3.2-0ubuntu6breezy1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ng@u053691m:~$


Someone please help :???:

---

### Post by GeneralZod on 2005-10-26
[QUOTE=Single]Someone please help :???:[/QUOTE]

Try using the Mark All Upgrades -> Smart Upgrade feature in Synaptic, rather than the commnad-line.

---

### Post by Single on 2005-10-26
Doing that Synaptic gives an error message:

> Could not upgrade the system!
Fix broken packages first.

libgl1-mesa-dev and libgl1-mesa-dri are the broken packages.
How to fix it?

---

### Post by psychicdragon on 2005-10-26
Strange, I just installed these through Synaptic successfully.

Try running ```
sudo apt-get -f install
```

---

### Post by Single on 2005-10-26
Here is the output:


ng@u053691m:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libgl1-mesa
The following packages will be upgraded:
  libgl1-mesa
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 282kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-updates/main libgl1-mesa 6.3.2-0ubuntu6breezy1 [282kB]
Fetched 282kB in 0s (782kB/s)

Preconfiguring packages ...
(Reading database ... 106871 files and directories currently installed.)
Preparing to replace libgl1-mesa 6.3.2-0ubuntu6 (using .../libgl1-mesa_6.3.2-0ubuntu6breezy1_i386.deb) ...
Unpacking replacement libgl1-mesa ...
dpkg: error processing /var/cache/apt/archives/libgl1-mesa_6.3.2-0ubuntu6breezy1_i386.deb (--unpack):
 unable to create `./usr/lib/libGL.so.1.2': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libgl1-mesa_6.3.2-0ubuntu6breezy1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ng@u053691m:~$

What should I do?

---

### Post by metoo on 2005-10-26
Not wanting to high-jacking here, but does this mesa stuff interfere with ati or nvidia drivers from the linux-restricted-modules... package?

---

