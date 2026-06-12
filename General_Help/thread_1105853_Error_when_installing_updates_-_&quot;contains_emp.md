---
title: "Error when installing updates - &quot;contains empty filename&quot;"
date: 2009-03-25
forum: General Help
---

### Post by Sunships on 2009-03-25
Hello, I get this error whenever I try and install updates, or anything via synaptic. Any idea how to fix it?

```
E: /var/cache/apt/archives/libgs8_8.61.dfsg.1-1ubuntu3.1_i386.deb: files list file for package `ubuntu-gdm-themes' contains empty filename
```

Does "E:" simply denote the beginning of an error message?

Thanks for your help, once again Ubuntu forum folk!

---

### Post by Sunships on 2009-03-25
Here is the complete error text from the terminal panel:

```
(Reading database ... dpkg: error processing /var/cache/apt/archives/libgs8_8.61.dfsg.1-1ubuntu3.1_i386.deb (--unpack):
 files list file for package `ubuntu-gdm-themes' contains empty filename
Errors were encountered while processing:
 /var/cache/apt/archives/libgs8_8.61.dfsg.1-1ubuntu3.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```

---

### Post by dcstar on 2009-03-25
> **Sunships said:**
> Here is the complete error text from the terminal panel:

```
(Reading database ... dpkg: error processing /var/cache/apt/archives/**libgs8_8.61.dfsg.1-1ubuntu3.1_i386.deb** (--unpack):
 files list file for package `ubuntu-gdm-themes' contains empty filename
Errors were encountered while processing:
 /var/cache/apt/archives/libgs8_8.61.dfsg.1-1ubuntu3.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```

Uninstall that package ( libgs8 ) in Synaptic, then delete that file and then reinstall the package:

```
sudo rm /var/cache/apt/archives/libgs8_8.61.dfsg.1-1ubuntu3.1_i386.deb
```

You may have to try the same thing with ubuntu-gdm-themes package.

---

### Post by Sunships on 2009-03-25
Thanks David,

The first removal went fine, but I still received the same error when updating, so I attempted to remove the ubuntu-gdm-themes package as advised. Here is the result:

```
[Command]:~$ sudo apt-get remove ubuntu-gdm-themes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  sqlite libgtkhtml3.16-cil libmono-cairo2.0-cil libflickrnet2.1.5-cil winbind
  sqlite3
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  ubuntu-artwork ubuntu-desktop ubuntu-gdm-themes
0 upgraded, 0 newly installed, 3 to remove and 5 not upgraded.
After this operation, 3600kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing ubuntu-desktop (--remove):
 files list file for package `ubuntu-gdm-themes' contains empty filename
E: Sub-process /usr/bin/dpkg exited unexpectedly
```

---

### Post by Sunships on 2009-03-26
Problem still unresolved.

---

### Post by Sunships on 2009-03-26
Bump.

---

### Post by Sunships on 2009-03-28
Still no takers?

---

### Post by Sunships on 2009-03-28
Alright, I'm currently unable to install anything from synaptic because of this error so time to start over with a fresh install. :(

---

### Post by dcstar on 2009-03-28
> **Sunships said:**
> Alright, I'm currently unable to install anything from synaptic because of this error so time to start over with a fresh install. :(

[http://ubuntuforums.org/showthread.php?t=591910](http://ubuntuforums.org/showthread.php?t=591910)

---

### Post by ethoxyethaan on 2009-03-28
try running:

gksu /usr/bin/software-properties-gtk

change the "download from" to a diffrent mirror.

try:

apt-get autoremove && apt-get autoclean && apt-get install -f && apt-get update && apt-get upgrade

---

### Post by Sidewinder1 on 2009-03-28
Your profile says 6.10 Edgy; perhaps that's the problem as Edgy's no longer supported. If I've made a totally ridiculous assumption, my humblest apology.
Side

---

### Post by Sunships on 2009-03-29
Hi, thanks for the replies everyone! Haven't done anything too rash yet re: re-installing.

David, I tried following the instructions in the linked thread, but with no change.

Likewise for ethoxyethaan's directions.

Typically I get the same error:

```
files list file for package `ubuntu-gdm-themes' contains empty filename
E: Sub-process /usr/bin/dpkg exited unexpectedly
```

Sidwinder1, I upgraded to 8.04 a few weeks ago and completely forgot to update my profile. Apologies if that confused anyone!

---

