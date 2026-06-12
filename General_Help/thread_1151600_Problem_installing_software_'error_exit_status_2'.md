---
title: "Problem installing software 'error exit status 2'"
date: 2009-05-07
forum: General Help
---

### Post by map7 on 2009-05-07
I have been running Ubuntu 904 64bit now for a week and today I ran into problems when trying to install a package called 'emacs-goodies-el'

If I try to install it this is what I get:
```
~ $sudo apt-get install emacs-goodies-el
[sudo] password for d110: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
emacs-goodies-el is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 31 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up emacs-goodies-el (29.4-1ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing emacs-goodies-el (--configure):
 subprocess post-installation script returned error exit status 2
Setting up m4 (1.4.11-1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing m4 (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 emacs-goodies-el
 m4
E: Sub-process /usr/bin/dpkg returned an error code (1)
~ $

```

I've tried the following:
 - running apt-get install with a -f option
 - running sudo dpkg --configure -a, then trying to install
 - uninstalling the bad packages

All these options did not help solve the problem.  Although perl-doc was originally a problem package and I could uninstall and reinstall that one package, but the rest I cannot uninstall or reinstall.

What else can I try?

---

### Post by salvachn on 2009-05-07
Try 
> apt-get upgrade
and then try. It might work.

---

### Post by map7 on 2009-05-07
I get errors when running the apt-get upgrade as well:

Could not install 'm4'
The upgrade will continue but the m4 package may be in a not working state. Please consider submitting a bug report about it.

I get the same error for the 'emacs-goodies-el' package.

I still cannot remove or reinstall either of these packages.  I've tried the following commands after the upgrade:
$sudo dpkg --configure -a
$sudo dpkg --configure m4

$sudo apt-get remove -f m4
$sudo apt-get install -f m4

---

