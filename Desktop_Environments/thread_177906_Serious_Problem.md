---
title: "Serious Problem"
date: 2006-05-17
forum: Desktop Environments
---

### Post by g77s80 on 2006-05-17
I installed automatix and since then when I try to install amule I get errors with wxgtk
I tried apt-get-f install but i returns this message:

Preconfiguring packages ...
(Reading database ... 109409 files and directories currently installed.)
Unpacking libwxgtk2.6-0 (from .../libwxgtk2.6-0_2.6.1.1.1ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libwxgtk2.6-0_2.6.1.1.1ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libwx_baseu-2.6.so.0', which is also in package libwxbase2.6
Errors were encountered while processing:
 /var/cache/apt/archives/libwxgtk2.6-0_2.6.1.1.1ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

if any one can help, thanX

---

### Post by hw-tph on 2006-05-17
Several packages can provide the same file, or "own" that particular file. You cannot have two packages installed that provide the same file, so try uninstalling the older one (**sudo aptitude remove libwxbase2.6**) if it is not used by any other program.


Håkan

---

### Post by arnieboy on 2006-05-17
[QUOTE=g77s80]I installed automatix and since then when I try to install amule I get errors with wxgtk
I tried apt-get-f install but i returns this message:

Preconfiguring packages ...
(Reading database ... 109409 files and directories currently installed.)
Unpacking libwxgtk2.6-0 (from .../libwxgtk2.6-0_2.6.1.1.1ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libwxgtk2.6-0_2.6.1.1.1ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libwx_baseu-2.6.so.0', which is also in package libwxbase2.6
Errors were encountered while processing:
 /var/cache/apt/archives/libwxgtk2.6-0_2.6.1.1.1ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

if any one can help, thanX[/QUOTE]
try:
```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/libwxgtk2.6-0_2.6.1.1.1ubuntu2_i386.deb
```

---

