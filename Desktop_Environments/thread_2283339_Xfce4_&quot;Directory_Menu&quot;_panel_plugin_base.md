---
title: "Xfce4 &quot;Directory Menu&quot; panel plugin base directory can't be set to &quot;File System&quot;"
date: 2015-06-21
forum: Desktop Environments
---

### Post by johsch on 2015-06-21
Adding a "Directory Menu" plugin to the Xfce4 panel and then in its Properties dialogue setting its base directory to "File System" has no effect.  The base directory remains set to my home directory.

This is a fresh new installation of Xubuntu 14.04.2 LTS.  My previous Xubuntu 12.04 LTS did not have this problem.  The setup is practically as-downloaded (2015-06-09).  The only thing I've done to the panel is to move it from the top of the desktop to the bottom.

I have seen the same problem at work where our sysadmin installs Xfce on top of Fedora.

I haven't been able to find a bug report or anyone else reporting the same problem.  Anyone know of a fix?

Thanks!

---

### Post by Toz on 2015-06-21
It has been fixed in the git tree (See: [http://git.xfce.org/xfce/xfce4-panel/commit/?id=361929416c4e9b064085e44ab8a7e2c5d0e315b9]("http://git.xfce.org/xfce/xfce4-panel/commit/?id=361929416c4e9b064085e44ab8a7e2c5d0e315b9")) but hasn't yet been officially released in a packaged version.

[Associated bug report.]("https://bugzilla.xfce.org/show_bug.cgi?id=10331")

---

