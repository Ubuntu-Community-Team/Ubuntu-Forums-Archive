---
title: "cannot remove virtualbox"
date: 2007-01-29
forum: Desktop Environments
---

### Post by MagiSu on 2007-01-29
Hello everyone.

I have met something trouble today. In order to build a virtual dos environment, I installed virtualbox by aptitude. However, it never worked. So I tried to remove it. But Aptitude
 replied:

Removing virtualbox ...
(Kernel module not found)...fail!
invoke-rc.d: initscript virtualbox, action "stop" failed.
dpkg: error processing virtualbox (--purge):
 subprocess pre-removal script returned error exit status 1
-e
Creating group 'vboxusers'. VM users must be member of that group!

No precompiled module for this kernel found -- trying to build one
Messages displayed during module compilation will be logged to /var/log/vbox-install.log
Compilation of kernel module failed, aborting installation
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 virtualbox
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Press return to continue.


What happened? And what can I do now? I can not install/remove anything now...Need I reinstall the whole system?

---

