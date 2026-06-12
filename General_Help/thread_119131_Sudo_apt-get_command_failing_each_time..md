---
title: "Sudo apt-get command failing each time."
date: 2006-01-18
forum: General Help
---

### Post by equal on 2006-01-18
Here's the errors I keep getting each and every time I try to sudo sudo apt-get:

```
phil@ubuntu:~$ sudo apt-get install rar
Password:
Reading package lists... Done
Building dependency tree... Done
rar is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up emacs21 (21.4a-1ubuntu1) ...
emacs-install emacs21
install/cedet-common: Handling install for emacsen flavor emacs21
Loading 00debian-vars...
No /etc/mailname. Reverting to default...
Loading 50dictionaries-common (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-autogen.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-compat.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-edebug.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-loaddefs.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-load.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/ezimage.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/inversion.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/mode-local.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/pprint.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/sformat.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/working.elc
Done
install/dictionaries-common: Byte-compiling for emacsen flavour emacs21
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/debian-ispell.elc
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/ispell.elc
Done
install/eieio: Handling install for emacsen flavor emacs21
Loading 00debian-vars...
No /etc/mailname. Reverting to default...
Loading 50dictionaries-common (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Source file `/usr/share/emacs21/site-lisp/eieio/eieio.el' newer than byte-compiled file
Loading /usr/lib/emacs/21.4/i386-linux/fns-21.4.1-x.el (source)...
Source file `/usr/share/emacs21/site-lisp/eieio/eieio-comp.el' newer than byte-compiled file
Wrote /usr/share/emacs21/site-lisp/eieio/chart.elc
Wrote /usr/share/emacs21/site-lisp/eieio/eieio-base.elc
Wrote /usr/share/emacs21/site-lisp/eieio/eieio-comp.elc
Wrote /usr/share/emacs21/site-lisp/eieio/eieio-custom.elc
Source file `/usr/share/emacs21/site-lisp/eieio/eieio-opt.el' newer than byte-compiled file
Wrote /usr/share/emacs21/site-lisp/eieio/eieio-doc.elc
Wrote /usr/share/emacs21/site-lisp/eieio/eieio.elc
Wrote /usr/share/emacs21/site-lisp/eieio/eieio-loaddefs.elc
Wrote /usr/share/emacs21/site-lisp/eieio/eieio-load.elc
Error loading speedbar... ignored.
Wrote /usr/share/emacs21/site-lisp/eieio/eieio-opt.elc
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/eieio/eieio-speedbar.el:
  !! Wrong type argument ((stringp nil))
Done
emacs-install: /usr/lib/emacsen-common/packages/install/eieio emacs21 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 5.
dpkg: error processing emacs21 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cedet-common:
 cedet-common depends on emacs21 | emacsen; however:
  Package emacs21 is not configured yet.
  Package emacsen is not installed.
  Package emacs21 which provides emacsen is not configured yet.
dpkg: error processing cedet-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eieio:
 eieio depends on emacs21 | emacsen; however:
  Package emacs21 is not configured yet.
  Package emacsen is not installed.
  Package emacs21 which provides emacsen is not configured yet.
dpkg: error processing eieio (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of speedbar:
 speedbar depends on cedet-common; however:
  Package cedet-common is not configured yet.
dpkg: error processing speedbar (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 emacs21
 cedet-common
 eieio
 speedbar
E: Sub-process /usr/bin/dpkg returned an error code (1)
phil@ubuntu:~$

```

I've tried doing a sudo apt-get update, that works fine, but even when my computer tells me there are new updates, it fails to install them correctly. Any ideas guys?

---

### Post by aysiu on 2006-01-18
What's your /etc/apt/sources.list look like?

---

### Post by equal on 2006-01-18
here's my /etc/apt/sources.list

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

## deb [http://public.planetmirror.com/pub/plf/ubuntu/plf/](http://public.planetmirror.com/pub/plf/ubuntu/plf/) breezy free non-free

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free
## deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi
## deb-src [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse
## created by arnieplanetremoved

---

### Post by aysiu on 2006-01-19
Can you try following the instructions in the first link of my signature (don't worry--it backs up your current sources.list) and then doing this? ```
sudo apt-get update
sudo apt-get install rar
```

---

### Post by equal on 2006-01-19
done, I still get the exact same error! sighh...

---

### Post by MacV on 2006-01-19
Any reason why don't you use Synaptic? Also, from what I'm decifering(good grief i can't spell tonight) I see your trying to get emacs21. Why do you need emacs? If it's not truly vital, i;d ignore the update prompts.

---

### Post by newuser111 on 2006-01-19
do **sudo apt-get -f install** and

**sudo apt-get -f dist-upgrade**

also in synaptic you can tell it to fix broken packages and then apply

---

### Post by deadgobby on 2006-01-20
I am too getting the same errors at the terminal and Synaptic. There is no broken packages in Synaptic

E: Sub-process /usr/bin/dpkg returned an error code (1)
doug@gobby:~$ sudo apt-get -f dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up emacs21 (21.4a-1ubuntu1) ...
emacs-install emacs21
install/cedet-common: Handling install for emacsen flavor emacs21
Loading 00debian-vars...
Loading 50dictionaries-common (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-autogen.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-compat.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-edebug.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-loaddefs.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-load.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/ezimage.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/inversion.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/mode-local.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/pprint.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/sformat.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/working.elc
Done
install/dictionaries-common: Byte-compiling for emacsen flavour emacs21
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/debian-ispell.elc
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/ispell.elc
Done
install/eieio: Handling install for emacsen flavor emacs21
Loading 00debian-vars...
Loading 50dictionaries-common (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Source file `/usr/share/emacs21/site-lisp/eieio/eieio.el' newer than byte-compiled file
Loading /usr/lib/emacs/21.4/i386-linux/fns-21.4.1-x.el (source)...
Source file `/usr/share/emacs21/site-lisp/eieio/eieio-comp.el' newer than byte-compiled file
Wrote /usr/share/emacs21/site-lisp/eieio/chart.elc
Wrote /usr/share/emacs21/site-lisp/eieio/eieio-base.elc
Wrote /usr/share/emacs21/site-lisp/eieio/eieio-comp.elc
Wrote /usr/share/emacs21/site-lisp/eieio/eieio-custom.elc
Source file `/usr/share/emacs21/site-lisp/eieio/eieio-opt.el' newer than byte-compiled file
Wrote /usr/share/emacs21/site-lisp/eieio/eieio-doc.elc
Wrote /usr/share/emacs21/site-lisp/eieio/eieio.elc
Wrote /usr/share/emacs21/site-lisp/eieio/eieio-loaddefs.elc
Wrote /usr/share/emacs21/site-lisp/eieio/eieio-load.elc
Error loading speedbar... ignored.
Wrote /usr/share/emacs21/site-lisp/eieio/eieio-opt.elc
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/eieio/eieio-speedbar.el:
  !! Wrong type argument ((stringp nil))
Done
emacs-install: /usr/lib/emacsen-common/packages/install/eieio emacs21 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 5.
dpkg: error processing emacs21 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cedet-common:
 cedet-common depends on emacs21 | emacsen; however:
  Package emacs21 is not configured yet.
  Package emacsen is not installed.
  Package emacs21 which provides emacsen is not configured yet.
dpkg: error processing cedet-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eieio:
 eieio depends on emacs21 | emacsen; however:
  Package emacs21 is not configured yet.
  Package emacsen is not installed.
  Package emacs21 which provides emacsen is not configured yet.
dpkg: error processing eieio (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of speedbar:
 speedbar depends on cedet-common; however:
  Package cedet-common is not configured yet.
dpkg: error processing speedbar (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 emacs21
 cedet-common
 eieio
 speedbar
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by deadgobby on 2006-01-20
I fixedthe problem. I just uninstall emacs21 and reinstall. It worked. ;)

---

### Post by equal on 2006-01-20
!!!

Brilliant. Everything works now. Thanks deadgobby.

---

### Post by equal on 2006-01-20
!!!

Brilliant. Everything works now. Thanks deadgobby.

---

