---
title: "Can't update or upgrade via pkg mgr"
date: 2009-08-12
forum: Desktop Environments
---

### Post by bobke on 2009-08-12
When I try to install updates I get a bunch of these:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/e2fslibs_1.39-1ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/e2fslibs_1.39-1ubuntu0.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/e2fsprogs_1.39-1ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/e2fsprogs_1.39-1ubuntu0.1_i386.deb)
  404 Not Found


This has been going on for over six months on Edgy. I'd like to upgrade to 8.0x but can't because of the same. Note: Don't know if this has anything to do with it but - one thing I did notice, upon boot, was that fsck failed, but still booted into x. If I can get this working, can I still get updates for Edgy, or do I have to upgrade to a later version?

---

### Post by drs305 on 2009-08-12
Edgy is no longer supported, which also means the Edgy repositories don't exist at their original location either.

You can either do a clean install of a later release (Hardy or later), try a step-by-step EOL (End of Life) upgrade (not recommended) or stay with Edgy and use the archived repositories.

Here are a few links:
[EOLUpgrades]("https://help.ubuntu.com/community/EOLUpgrades")

[8.04/installation-guide/i386/index.html]("https://help.ubuntu.com/8.04/installation-guide/i386/index.html")

[https://help.ubuntu.com/9.04/installation-guide/i386/index.html]("https://help.ubuntu.com/9.04/installation-guide/i386/index.html")

[https://wiki.ubuntu.com/Releases]("https://wiki.ubuntu.com/Releases")

If you want to stick with Edgy, search for "old-releases" in the forums on how to change your repositories or see how to change the repositories to "old-releases" in the EOL link.

---

### Post by overdrank on 2009-08-12
Hi and as stated in your other [thread]("http://ubuntuforums.org/showthread.php?p=7771771#post7771771") Thread closed.

---

