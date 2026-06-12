---
title: "[SOLVED] Synaptic completely screwed up..."
date: 2008-02-27
forum: Desktop Environments
---

### Post by Aanidaani on 2008-02-27
Okay, so i recently updated to alpha 4 of Heron and apparently the package anjuta-common has some issues with the release. I tried cleaning up and repairing my package list after it failed to install the latest version of anjuta-common, but here's the error I get:

```
steven@steven-desktop:/var/lib/dpkg$ sudo apt-get install -f
[sudo] password for steven:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libflickrnet2.1.5-cil python-pyopenssl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  anjuta-common
The following packages will be upgraded:
  anjuta-common
1 upgraded, 0 newly installed, 0 to remove and 37 not upgraded.
2 not fully installed or removed.
Need to get 0B/4322kB of archives.
After this operation, 360kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
(Reading database ... 171997 files and directories currently installed.)
Preparing to replace anjuta-common 2:2.3.4-0ubuntu1 (using .../anjuta-common_2%3a2.3.5-0ubuntu1_all.deb) ...
Unpacking replacement anjuta-common ...
gtk-update-icon-cache: The generated cache was invalid.
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
gtk-update-icon-cache: The generated cache was invalid.
dpkg: error processing /var/cache/apt/archives/anjuta-common_2%3a2.3.5-0ubuntu1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
gtk-update-icon-cache: The generated cache was invalid.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/anjuta-common_2%3a2.3.5-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have no idea what to do and Synaptic won't install updates for any other packages until this resvoled. Can anyone help me?

---

### Post by rouge568 on 2008-02-27
You may not be able to fix this: Hardy is still in Alpha and is NOT meant for regular use. 
You could always try removing the package, installing your updates, and trying to install it again.

---

### Post by Aanidaani on 2008-02-27
I tried removing the package but I kept getting errors. I ultimately ended up removing the entry for the file from /var/lib/dpkg/status. I made a backup of the list in case I have any problems, but after removing the entry and cleaning up synaptic everything works fine.

---

### Post by juandadamo on 2008-05-11
I have the same problem: just upgrading from Gutsy to Hardy and
I get the annoying gtk-update-icon-cache: The generated cache was invalid.
every time I use the synaptic: 15 min of hard disk work and some packages(kile, kpowersave) that cannot be configured.
I've tried to uninstall them but the error persists. (apt-get or synaptic way)
I've tried [http://ubuntuforums.org/showthread.php?t=661797](http://ubuntuforums.org/showthread.php?t=661797) but I see no graphic file in my /usr/share/icons/.

Please help...

---

### Post by juandadamo on 2008-05-11
> **juandadamo said:**
> I have the same problem: just upgrading from Gutsy to Hardy and
I get the annoying gtk-update-icon-cache: The generated cache was invalid.
every time I use the synaptic: 15 min of hard disk work and some packages(kile, kpowersave) that cannot be configured.
I've tried to uninstall them but the error persists. (apt-get or synaptic way)
I've tried [http://ubuntuforums.org/showthread.php?t=661797](http://ubuntuforums.org/showthread.php?t=661797) but I see no graphic file in my /usr/share/icons/.

Please help...


Find out solving the problem. The solution in 
[http://forums.gentoo.org/viewtopic-t-596363.html?sid=7cd23f4e65884795289decf7e922eb29](http://forums.gentoo.org/viewtopic-t-596363.html?sid=7cd23f4e65884795289decf7e922eb29)

---

