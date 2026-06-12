---
title: "failed install leaves error"
date: 2006-03-13
forum: Desktop Environments
---

### Post by tommyb on 2006-03-13
I had tried several times to install 5.10, and each time it would hang, usually in the CD install.  Last time it hung after the first reboot.  I rebooted, and got a prompt.  After logging in, i tried a "sudo dpkg --configure -a".  The first time I ran it, it hung.  After rebooting, I tried again.  This time it ran thru, ending in an error message:  dpkg: . ./../src/packages.c:191: process_queue: Assertion 'dependtry <= 4'  failed.  E: Sub-process /usr/bin/dpkg exited unexpectedly.
Still, I rebooted, and this time (6th install attempt) got a gui.  I opened a terminal, and ran apt-get upgrade.  a message said 1 package was not fully installed or removed.  It upgraded 48 packages, and ended with the same error as above.  Any ideas what broke, and how to fix?

---

