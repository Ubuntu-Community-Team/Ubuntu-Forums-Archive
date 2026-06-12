---
title: "System Updates"
date: 2006-09-23
forum: Desktop Environments
---

### Post by munkydust on 2006-09-23
I'm having problems when I try and install new updates. First of all I get this:

monkey@monkey-desktop:~$ sudo apt-get -f dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade...Done
The following packages will be upgraded:
  automatix xserver-xorg-core
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/3653kB of archives.
After unpacking 4096B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing /var/cache/apt/archives/poppler-utils_0.5.1-0ubuntu7_i386.deb (--unpack):
 files list file for package `poppler-utils' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/poppler-utils_0.5.1-0ubuntu7_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

and then if I try installing them through the  upgrade manager I get this

E: /var/cache/apt/archives/poppler-utils_0.5.1-0ubuntu7_i386.deb: files list file for package `poppler-utils' is missing final newline

I've tried downloading and installing poppler-utils_0.5.1-0ubuntu7_i386.deb again but it just gives me the same error.

Thanks for your help

---

### Post by munkydust on 2006-09-24
any one got any ideas?

---

### Post by dentaku65 on 2006-09-24
Try:

> sudo apt-get clean

Then:

> sudo aptitude update

> sudo aptitude dist-upgrade

---

### Post by munkydust on 2006-09-24
Thank you, but it didn't work. apt-get clean, didn't seem to do anything and when I try the other commands I get the same error about the poppler utils.

---

### Post by lamego on 2006-09-24
Try to remove automatix

---

### Post by arnieboy on 2006-09-24
try doing
```
sudo apt-get remove poppler-utils
```
and then do:
```
sudo apt-get update
sudo apt-get -f install
```

---

### Post by munkydust on 2006-09-25
Nah, none of that works, I just keep getting the same message of the poppler-utils.

Cheers anyway guys

---

### Post by munkydust on 2006-09-26
Anymore ideas from people?

---

### Post by Devilotx on 2006-09-26
open terminal and issue:

sudo dpkg --force-a -i /var/cache/apt/archives/poppler-utils_0.5.1-0ubuntu7_i386.deb

to force the install.

---

### Post by munkydust on 2006-09-27
nope same error

---

### Post by munkydust on 2006-09-27
Well this is a bit of a shit isn't it! :D

I'm going to back everything up and start from scratch me thinks.

---

