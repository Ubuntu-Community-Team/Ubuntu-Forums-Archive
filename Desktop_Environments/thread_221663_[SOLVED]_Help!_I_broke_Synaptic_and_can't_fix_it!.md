---
title: "[SOLVED] Help! I broke Synaptic and can't fix it!"
date: 2006-07-23
forum: Desktop Environments
---

### Post by bbrg548 on 2006-07-23
I was trying to install Armagetron Advanced (because Armagetron stopped working and is out of date). I could only find an .rpm file, so I converted it to a .deb file with alien.
When I ran it, it opened in GDebi. On trying to install it I got:

(Reading database ... 97580 files and directories currently installed.)
/var/lib/dpkg/info/armagetronad.prerm: line 2: /share/games/armagetronad/scripts /sysinstall: No such file or directory
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: line 2: /share/games/armagetronad/scripts/sysinstall : No such file or directory
dpkg: error processing armagetronad_0.2.8.2-2_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/armagetronad.postinst: line 2: /share/games/armagetronad/scri pts/sysinstall: No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 armagetronad_0.2.8.2-2_i386.deb

Now, when I run Synaptic, I don't have any packages listed and I get the following errors:

E:The package armagetronad needs to be reinstalled, but I can't find and archive for it.
E:Internal error opening cache (1). Please report.

When I try:
  sudo apt-get install -f
from the terminal, I get:

Reading package lists... Done
Building dependency tree... Done
E: The package armagetronad needs to be reinstalled, but I can't find an archive for it.

When I try:
  sudo apt-get update
it appears to work correctly, but I still have the same error from Synaptic.

Please, help! :(

---

### Post by cwaldbieser on 2006-07-23
> **bbrg548 said:**
> I was trying to install Armagetron Advanced (because Armagetron stopped working and is out of date). I could only find an .rpm file, so I converted it to a .deb file with alien.
When I ran it, it opened in GDebi. On trying to install it I got:

(Reading database ... 97580 files and directories currently installed.)
/var/lib/dpkg/info/armagetronad.prerm: line 2: /share/games/armagetronad/scripts /sysinstall: No such file or directory
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: line 2: /share/games/armagetronad/scripts/sysinstall : No such file or directory
dpkg: error processing armagetronad_0.2.8.2-2_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/armagetronad.postinst: line 2: /share/games/armagetronad/scri pts/sysinstall: No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 armagetronad_0.2.8.2-2_i386.deb

Now, when I run Synaptic, I don't have any packages listed and I get the following errors:

E:The package armagetronad needs to be reinstalled, but I can't find and archive for it.
E:Internal error opening cache (1). Please report.

When I try:
  sudo apt-get install -f
from the terminal, I get:

Reading package lists... Done
Building dependency tree... Done
E: The package armagetronad needs to be reinstalled, but I can't find an archive for it.

When I try:
  sudo apt-get update
it appears to work correctly, but I still have the same error from Synaptic.

Please, help! :(

There are a couple apt-get options you could try.  I would probably start with "$sudo apt-get --fix-broken".

---

### Post by bbrg548 on 2006-07-23
> **cwaldbieser said:**
> There are a couple apt-get options you could try.  I would probably start with "$sudo apt-get --fix-broken".

All that does is bring up the list of commands, lile --fix-broken is not a valid option (and it's not listed).

---

### Post by carlalex on 2006-07-23
Try "sudo dpkg --configure -a"

Carl

---

### Post by bbrg548 on 2006-07-24
> **carlalex said:**
> Try "sudo dpkg --configure -a"

Carl

Thanks, when I do that I get:
dpkg: error processing armagetronad (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 armagetronad

When I try to reinstall Armagetron, I get the same errors as before.

---

### Post by bbrg548 on 2006-07-26
I fixed it!

I had to delete the armagetronad sections of:
/var/lib/dpkg/available
/var/lib/dpkg/status

after doing that I did:
sudo apt-get update
sudo apt-get install -f

Everything seems to be working ok now.

---

### Post by LordMau on 2006-07-30
> **bbrg548 said:**
> I fixed it!

I had to delete the armagetronad sections of:
/var/lib/dpkg/available
/var/lib/dpkg/status

after doing that I did:
sudo apt-get update
sudo apt-get install -f

Everything seems to be working ok now.

Excellent tip, worked for me on a different package (xfprot). Although I believe there are loose files lying about related to the unclean install which needs to be manually cleaned up.

Thanks!

---

### Post by guru369 on 2006-07-30
> **bbrg548 said:**
> I fixed it!

I had to delete the armagetronad sections of:
/var/lib/dpkg/available
/var/lib/dpkg/status

after doing that I did:
sudo apt-get update
sudo apt-get install -f

Everything seems to be working ok now.

Please add [SOLVED] to your initial thread title. It will help others find answers as well...

dekela

---

