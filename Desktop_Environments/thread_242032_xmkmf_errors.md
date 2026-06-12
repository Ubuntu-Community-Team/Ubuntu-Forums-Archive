---
title: "xmkmf errors"
date: 2006-08-23
forum: Desktop Environments
---

### Post by stepheny on 2006-08-23
Hi,
I am an experienced SuSE and Fedora user trying out Ubuntu. It's great! I'm really impressed. I have had a few small difficulties but they were all easily resolved. I have one problem that I cannot resolve though. I am trying to install the WizardPen driver and need to use xmkmf to write a make file, however after typing "xmkmf" or "sudo xmkmf" I get the following errors. I have reinstalled the GCC libraries but this didn't help.

-desktop:~/Downloads/wizardpen-driver-0.5.0$ xmkmf
imake -DUseInstalled -I/etc/X11/config/cf
<stdin>:1:19: error: stdio.h: No such file or directory
<stdin>:2:19: error: ctype.h: No such file or directory
<stdin>: In function ‘main’:
<stdin>:18: error: ‘NULL’ undeclared (first use in this function)
<stdin>:18: error: (Each undeclared identifier is reported only once
<stdin>:18: error: for each function it appears in.)
<stdin>:45: warning: incompatible implicit declaration of built-in function ‘sscanf’
<stdin>:49: warning: incompatible implicit declaration of built-in function ‘printf’
/usr/bin/xmkmf: line 57: 10980 Aborted imake $imake_defines $args

If anyone has any idea what I am doing wrong I would be really grateful.

Regards, Steve.

---

### Post by stepheny on 2006-08-24
I found out what was wrong with xmkmf. The packet "build-essential" needed to be installed.

---

### Post by daller on 2006-09-07
Any problems at all, see this guide:

[https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

---

