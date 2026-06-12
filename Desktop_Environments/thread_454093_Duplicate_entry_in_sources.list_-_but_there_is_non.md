---
title: "Duplicate entry in sources.list - but there is none!"
date: 2007-05-25
forum: Desktop Environments
---

### Post by akvik on 2007-05-25
Hi, when I run sudo aptitude upgrade, I get:

```

W: Duplicate sources.list entry http://se.archive.ubuntu.com feisty/universe Packages (/var/lib/apt/lists/se.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages)

```

But I can't see the duplicate in my sources.list file:
```

# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://se.archive.ubuntu.com/ubuntu feisty main restricted
deb http://se.archive.ubuntu.com/ubuntu feisty-updates main restricted
deb http://security.ubuntu.com/ubuntu feisty-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://se.archive.ubuntu.com/ubuntu feisty universe multiverse
deb http://se.archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse

# beryl
deb http://ubuntu.beryl-project.org feisty main 
# sync
deb http://archive.ubuntustudio.org/ubuntustudio feisty main

```

Does anyone know how to fix it ?

---

### Post by dbott67 on 2007-05-25
It appears as though the repos are also listed in the directory noted in the error (perhaps they are packages to be updated?)

```
dbott@feisty:/var/lib/apt/lists$ ls -all
total 31904
drwxr-xr-x 3 root root    12288 2007-05-25 07:37 .
drwxr-xr-x 5 root root     4096 2007-05-21 16:28 ..
-rw-r--r-- 1 root root     2082 2007-05-16 14:33 archive.canonical.com_ubuntu_dists_feisty-commercial_main_binary-i386_Packages
-rw-r--r-- 1 root root     4878 2007-05-16 16:03 archive.canonical.com_ubuntu_dists_feisty-commercial_Release
-rw-r--r-- 1 root root      191 2007-05-16 16:03 archive.canonical.com_ubuntu_dists_feisty-commercial_Release.gpg
-rw-r--r-- 1 root root    14309 2007-05-19 00:14 archive.ubuntu.com_ubuntu_dists_feisty-backports_main_binary-i386_Packages
-rw-r--r-- 1 root root        0 2007-05-19 00:14 archive.ubuntu.com_ubuntu_dists_feisty-backports_multiverse_binary-i386_Packages
-rw-r--r-- 1 root root    38408 2007-05-19 00:28 archive.ubuntu.com_ubuntu_dists_feisty-backports_Release
-rw-r--r-- 1 root root      191 2007-05-19 00:28 archive.ubuntu.com_ubuntu_dists_feisty-backports_Release.gpg
-rw-r--r-- 1 root root        0 2007-05-19 00:14 archive.ubuntu.com_ubuntu_dists_feisty-backports_restricted_binary-i386_Packages
-rw-r--r-- 1 root root     3727 2007-05-19 00:14 archive.ubuntu.com_ubuntu_dists_feisty-backports_universe_binary-i386_Packages
-rw-r--r-- 1 root root  6116197 2007-04-17 14:10 archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages
-rw-r--r-- 1 root root  1839606 2007-04-17 14:13 archive.ubuntu.com_ubuntu_dists_feisty_main_source_Sources
-rw-r--r-- 1 root root   670194 2007-04-17 14:11 archive.ubuntu.com_ubuntu_dists_feisty_multiverse_binary-i386_Packages
-rw-r--r-- 1 root root   228099 2007-04-17 14:14 archive.ubuntu.com_ubuntu_dists_feisty_multiverse_source_Sources
-rw-r--r-- 1 root root    57158 2007-04-17 14:20 archive.ubuntu.com_ubuntu_dists_feisty_Release
-rw-r--r-- 1 root root      191 2007-04-17 14:20 archive.ubuntu.com_ubuntu_dists_feisty_Release.gpg
-rw-r--r-- 1 root root    32432 2007-04-17 14:10 archive.ubuntu.com_ubuntu_dists_feisty_restricted_binary-i386_Packages
-rw-r--r-- 1 root root     4975 2007-04-17 14:13 archive.ubuntu.com_ubuntu_dists_feisty_restricted_source_Sources
-rw-r--r-- 1 root root   104513 2007-05-24 18:13 archive.ubuntu.com_ubuntu_dists_feisty-security_main_binary-i386_Packages
-rw-r--r-- 1 root root    14794 2007-05-24 18:17 archive.ubuntu.com_ubuntu_dists_feisty-security_main_source_Sources
-rw-r--r-- 1 root root     8663 2007-05-24 18:13 archive.ubuntu.com_ubuntu_dists_feisty-security_multiverse_binary-i386_Packages
-rw-r--r-- 1 root root        0 2007-05-24 18:17 archive.ubuntu.com_ubuntu_dists_feisty-security_multiverse_source_Sources
-rw-r--r-- 1 root root    44697 2007-05-24 18:26 archive.ubuntu.com_ubuntu_dists_feisty-security_Release
-rw-r--r-- 1 root root      191 2007-05-24 18:26 archive.ubuntu.com_ubuntu_dists_feisty-security_Release.gpg
-rw-r--r-- 1 root root    18419 2007-05-24 18:13 archive.ubuntu.com_ubuntu_dists_feisty-security_restricted_binary-i386_Packages
-rw-r--r-- 1 root root     2642 2007-05-24 18:17 archive.ubuntu.com_ubuntu_dists_feisty-security_restricted_source_Sources
-rw-r--r-- 1 root root    33239 2007-05-24 18:13 archive.ubuntu.com_ubuntu_dists_feisty-security_universe_binary-i386_Packages
-rw-r--r-- 1 root root     2892 2007-05-24 18:17 archive.ubuntu.com_ubuntu_dists_feisty-security_universe_source_Sources
-rw-r--r-- 1 root root 17421953 2007-04-17 14:11 archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages
-rw-r--r-- 1 root root  5644181 2007-04-17 14:14 archive.ubuntu.com_ubuntu_dists_feisty_universe_source_Sources
-rw-r--r-- 1 root root   103948 2007-05-25 04:10 archive.ubuntu.com_ubuntu_dists_feisty-updates_main_binary-i386_Packages
-rw-r--r-- 1 root root    16035 2007-05-25 04:16 archive.ubuntu.com_ubuntu_dists_feisty-updates_main_source_Sources
-rw-r--r-- 1 root root     1156 2007-05-25 04:10 archive.ubuntu.com_ubuntu_dists_feisty-updates_multiverse_binary-i386_Packages
-rw-r--r-- 1 root root    32437 2007-05-25 04:25 archive.ubuntu.com_ubuntu_dists_feisty-updates_Release
-rw-r--r-- 1 root root      191 2007-05-25 04:25 archive.ubuntu.com_ubuntu_dists_feisty-updates_Release.gpg
-rw-r--r-- 1 root root        0 2007-05-25 04:10 archive.ubuntu.com_ubuntu_dists_feisty-updates_restricted_binary-i386_Packages
-rw-r--r-- 1 root root        0 2007-05-25 04:16 archive.ubuntu.com_ubuntu_dists_feisty-updates_restricted_source_Sources
-rw-r--r-- 1 root root     3150 2007-05-25 04:10 archive.ubuntu.com_ubuntu_dists_feisty-updates_universe_binary-i386_Packages
-rw-r----- 1 root root        0 2007-05-25 07:35 lock
drwxr-xr-x 2 root root     4096 2007-05-25 07:37 partial
-rw-r--r-- 1 root root    27134 2007-05-19 15:28 www.getautomatix.com_apt_dists_feisty_main_binary-i386_Packages
-rw-r--r-- 1 root root     6738 2007-05-19 15:27 www.getautomatix.com_apt_dists_feisty_Release
-rw-r--r-- 1 root root      189 2007-05-19 15:27 www.getautomatix.com_apt_dists_feisty_Release.gpg
```
```

dbott@feisty:/var/lib/apt/lists$ cat archive.canonical.com_ubuntu_dists_feisty-commercial_main_binary-i386_Packages
Package: vmware-server
Priority: optional
Section: misc
Installed-Size: 127608
Maintainer: VMware Build Team <vmware-builds@vmware.com>
Architecture: i386
Version: 1.0.3-1
Depends: netbase, netkit-inetd | inetd, update-inetd, vmware-server-kernel-modules, libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.9.0), libc6 (>= 2.3.4-1), libexpat1 (>= 1.95.8), libfontconfig1 (>= 2.3.0), libfreetype6 (>= 2.1.5-1), libgcc1 (>= 1:4.0.1), libglib2.0-0 (>= 2.8.0), libgtk2.0-0 (>= 2.8.0), libice6, libjpeg62, libpango1.0-0 (>= 1.10.1), libpng12-0 (>= 1.2.8rel), librsvg2-2 (>= 2.9.5), librsvg2-common (>= 2.9.5), libsm6, libssl0.9.7, libstdc++5 (>= 1:3.3.4-1), libx11-6, libxext6, libxft2 (>> 2.1.1), libxi6, libxml2 (>= 2.6.20), libxrender1, libxt6, libxtst6, zlib1g (>= 1:1.2.1)
Pre-Depends: debconf (>= 0.5) | debconf-2.0
Conflicts: xinetd, vmware-player, libdbus-1-2
Filename: pool/main/v/vmware-server/vmware-server_1.0.3-1_i386.deb
Size: 79434866
MD5sum: 3616ae75480b384811beeed32471381a
Description: Free virtual machine server from VMware
 The free VMware Server lets you run pre-built virtual machines on
 your desktop.  You can run multiple operating systems side-by-side,
 easing the process of software development, testing, and evaluation.
 .
 Virtual machines developed in VMware Workstation or ESX Server can
 be run in VMware Server.
 .
 To run the VMware Server Console, just run /usr/bin/vmware from within X.
 .
 Note: You will also need the VMware Server kernel modules to run vmware.
 These can be built from source from vmware-server -kernel-source, or you
 can install a pre-built vmware-server-kernel-modules package for your kernel.

Package: vmware-server-kernel-source
Priority: optional
Section: misc
Installed-Size: 244
Maintainer: VMware Build Team <vmware-builds@vmware.com>
Architecture: i386
Source: vmware-server
Version: 1.0.3-1
Depends: module-assistant, debhelper, bzip2, gzip
Filename: pool/main/v/vmware-server/vmware-server-kernel-source_1.0.3-1_i386.deb
Size: 195318
MD5sum: 3bd97bed223b7c1ce7c1a3abbdec636f
Description: Kernel modules for VMware Server.

```

Have you closed out of all instances of aptitude, apt-get, Synaptic (or re-booted)?

-Dave

---

### Post by akvik on 2007-05-25
Thanks, 

yes, this error has been with me for some time, I didn't have any synaptic open at the time. and the system is updated. I can still do the updates even with this error.

mine looks like this:
```

:/var/lib/apt/lists$ ls -all
total 24300
drwxr-xr-x 3 root root     8192 2007-05-25 10:57 .
drwxr-xr-x 5 root root     4096 2007-05-25 09:52 ..
-rw-r--r-- 1 root root    39007 2007-05-15 14:09 archive.ubuntustudio.org_ubuntustudio_dists_feisty_main_binary-i386_Packages
-rw-r--r-- 1 root root     1304 2007-05-16 20:42 archive.ubuntustudio.org_ubuntustudio_dists_feisty_Release
-rw-r--r-- 1 root root      189 2007-05-16 20:42 archive.ubuntustudio.org_ubuntustudio_dists_feisty_Release.gpg
-rw-r----- 1 root root        0 2007-05-25 10:57 lock
-rw-r--r-- 1 root root    29990 2007-05-22 13:39 medibuntu.sos-sts.com_repo_dists_feisty_free_binary-i386_Packages
-rw-r--r-- 1 root root     4676 2007-05-22 13:45 medibuntu.sos-sts.com_repo_dists_feisty_free_source_Sources
-rw-r--r-- 1 root root    13259 2007-05-22 13:42 medibuntu.sos-sts.com_repo_dists_feisty_non-free_binary-i386_Packages
-rw-r--r-- 1 root root     3903 2007-05-22 13:45 medibuntu.sos-sts.com_repo_dists_feisty_non-free_source_Sources
-rw-r--r-- 1 root root     7232 2007-05-22 14:07 medibuntu.sos-sts.com_repo_dists_feisty_Release
-rw-r--r-- 1 root root      189 2007-05-22 14:07 medibuntu.sos-sts.com_repo_dists_feisty_Release.gpg
drwxr-xr-x 2 root root     4096 2007-05-25 10:57 partial
-rw-r--r-- 1 root root  6116197 2007-04-17 21:10 se.archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages
-rw-r--r-- 1 root root    13846 2007-02-09 18:14 se.archive.ubuntu.com_ubuntu_dists_feisty_main_i18n_Translation-en%5fGB
-rw-r--r-- 1 root root   670194 2007-04-17 21:11 se.archive.ubuntu.com_ubuntu_dists_feisty_multiverse_binary-i386_Packages
-rw-r--r-- 1 root root     2855 2007-02-09 13:14 se.archive.ubuntu.com_ubuntu_dists_feisty_multiverse_i18n_Translation-en%5fGB
-rw-r--r-- 1 root root    57158 2007-04-17 21:20 se.archive.ubuntu.com_ubuntu_dists_feisty_Release
-rw-r--r-- 1 root root      191 2007-04-17 21:20 se.archive.ubuntu.com_ubuntu_dists_feisty_Release.gpg
-rw-r--r-- 1 root root    32432 2007-04-17 21:10 se.archive.ubuntu.com_ubuntu_dists_feisty_restricted_binary-i386_Packages
-rw-r--r-- 1 root root 17421953 2007-05-24 12:41 se.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages
-rw-r--r-- 1 root root    31089 2007-05-18 13:12 se.archive.ubuntu.com_ubuntu_dists_feisty-updates_main_binary-i386_Packages
-rw-r--r-- 1 root root        0 2007-05-18 13:12 se.archive.ubuntu.com_ubuntu_dists_feisty-updates_multiverse_binary-i386_Packages
-rw-r--r-- 1 root root    32437 2007-05-18 13:28 se.archive.ubuntu.com_ubuntu_dists_feisty-updates_Release
-rw-r--r-- 1 root root      191 2007-05-18 13:28 se.archive.ubuntu.com_ubuntu_dists_feisty-updates_Release.gpg
-rw-r--r-- 1 root root        0 2007-05-18 13:12 se.archive.ubuntu.com_ubuntu_dists_feisty-updates_restricted_binary-i386_Packages
-rw-r--r-- 1 root root        0 2007-05-18 13:12 se.archive.ubuntu.com_ubuntu_dists_feisty-updates_universe_binary-i386_Packages
-rw-r--r-- 1 root root   104513 2007-05-25 01:13 security.ubuntu.com_ubuntu_dists_feisty-security_main_binary-i386_Packages
-rw-r--r-- 1 root root     8663 2007-05-25 01:13 security.ubuntu.com_ubuntu_dists_feisty-security_multiverse_binary-i386_Packages
-rw-r--r-- 1 root root    44697 2007-05-25 01:26 security.ubuntu.com_ubuntu_dists_feisty-security_Release
-rw-r--r-- 1 root root      191 2007-05-25 01:26 security.ubuntu.com_ubuntu_dists_feisty-security_Release.gpg
-rw-r--r-- 1 root root    18419 2007-05-25 01:13 security.ubuntu.com_ubuntu_dists_feisty-security_restricted_binary-i386_Packages
-rw-r--r-- 1 root root    33239 2007-05-25 01:13 security.ubuntu.com_ubuntu_dists_feisty-security_universe_binary-i386_Packages
-rw-r--r-- 1 root root    53263 2007-03-16 16:05 ubuntu.beryl-project.org_dists_feisty_main_binary-i386_Packages
-rw-r--r-- 1 root root     2965 2007-03-16 15:06 ubuntu.beryl-project.org_dists_feisty_Release
-rw-r--r-- 1 root root      191 2007-03-16 15:06 ubuntu.beryl-project.org_dists_feisty_Release.gpg

```

---

### Post by dbott67 on 2007-05-25
Very strange... there does not appear to be a duplicate entry in /var/lib/apt/lists.

I don't know what the next step is.

-Dave

---

### Post by akvik on 2007-05-28
Thanks anyway, I'll probably just have to live with it, but it would be nice to know what  causes it :)

---

