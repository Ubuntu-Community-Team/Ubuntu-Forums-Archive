---
title: "apt errors - openoffice error?"
date: 2005-05-21
forum: Desktop Environments
---

### Post by Samer on 2005-05-21
Every time I run apt, I get a bunch of weird errors...Some of it seems related to openoffice, but that runs fine.  Any idea?

> samer@porky:~$ sudo apt-get install menu
Reading package lists... Done
Building dependency tree... Done
menu is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
37 not fully installed or removed.
Need to get 0B/3659kB of archives.
After unpacking 0B of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
(Reading database ... 59389 files and directories currently installed.)
Preparing to replace openoffice.org-l10n-en 1.1.3-8ubuntu2 (using .../openoffice.org-l10n-en_1.1.3-8ubuntu2_all.deb) ...
Unpacking replacement openoffice.org-l10n-en ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
run-parts: /usr/share/openoffice.org-debian-files/hooks/postrm.d/prelink exited with return code 1
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
run-parts: /usr/share/openoffice.org-debian-files/hooks/postrm.d/prelink exited with return code 1
dpkg: error processing /var/cache/apt/archives/openoffice.org-l10n-en_1.1.3-8ubuntu2_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
run-parts: /usr/share/openoffice.org-debian-files/hooks/postrm.d/prelink exited with return code 1
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Preparing to replace openoffice.org-kde 1.1.3-8ubuntu2 (using .../openoffice.org-kde_1.1.3-8ubuntu2_i386.deb) ...
Unpacking replacement openoffice.org-kde ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
run-parts: /usr/share/openoffice.org-debian-files/hooks/postrm.d/prelink exited with return code 1
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
run-parts: /usr/share/openoffice.org-debian-files/hooks/postrm.d/prelink exited with return code 1
dpkg: error processing /var/cache/apt/archives/openoffice.org-kde_1.1.3-8ubuntu2_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
run-parts: /usr/share/openoffice.org-debian-files/hooks/postrm.d/prelink exited with return code 1
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-l10n-en_1.1.3-8ubuntu2_all.deb
 /var/cache/apt/archives/openoffice.org-kde_1.1.3-8ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by SGC on 2005-05-21
I'am not sure , but it seems that you have broken packages, try the following to fix them:

apt-get -f install

make sure there is no other package managment tool (synaptic, kynaptic,..) open while doing so.

---

### Post by Samer on 2005-05-21
apt-get -f install had the same problems...Is there some way I can override this with dpkg?

---

### Post by Xian on 2005-05-21
Open a terminal and input the following:

```
$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/openoffice.org-l10n-en_1.1.3-8ubuntu2_all.deb
$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/openoffice.org-kde_1.1.3-8ubuntu2_i386.deb
```

Then do a couple of more commands to clean up:

```
$ sudo dpkg --configure -a
$ sudo apt-get -f install
```

---

### Post by Samer on 2005-05-21
Ack, more errors!  The only programs I have open are Konqueror and a free Konsole, but it says a process is locking /var/cache/debconf/config.dat

> samer@porky:~$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/openoffice
.org-l10n-en_1.1.3-8ubuntu2_all.deb
(Reading database ... 59427 files and directories currently installed.)
Preparing to replace openoffice.org-l10n-en 1.1.3-8ubuntu2 (using .../openoffice
.org-l10n-en_1.1.3-8ubuntu2_all.deb) ...
Unpacking replacement openoffice.org-l10n-en ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another p                                           rocess
run-parts: /usr/share/openoffice.org-debian-files/hooks/postrm.d/prelink exited                                            with return code 1
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another p                                           rocess
run-parts: /usr/share/openoffice.org-debian-files/hooks/postrm.d/prelink exited                                            with return code 1
dpkg: error processing /var/cache/apt/archives/openoffice.org-l10n-en_1.1.3-8ubu                                           ntu2_all.deb (--install):
 subprocess new post-removal script returned error exit status 1
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another p                                           rocess
run-parts: /usr/share/openoffice.org-debian-files/hooks/postrm.d/prelink exited                                            with return code 1
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-l10n-en_1.1.3-8ubuntu2_all.deb


---

### Post by Xian on 2005-05-21
Try rebooting the computer at this point.
Make sure there's not a OOo starter in your panel, and then again:
```
$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/openoffice.org-l10n-en_1.1.3-8ubuntu2_all.deb
```

---

### Post by Samer on 2005-05-21
Xian, your "Windows" solution worked.   :D  Thanks and w0ot, now things are moving along nicely.

-Samer

PS: I'm also a Xian from Kansas.

---

### Post by Xian on 2005-05-21
Greets from Wichita. :)

---

