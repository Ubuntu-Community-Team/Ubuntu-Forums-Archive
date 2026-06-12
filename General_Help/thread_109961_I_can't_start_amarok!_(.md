---
title: "I can't start amarok! :("
date: 2005-12-29
forum: General Help
---

### Post by monotux on 2005-12-29
I have no idea why, but a few days ago, amaroK simply stopped starting.
This is the entire error message amarok gives me:
```
amaroK: [Loader] amarokapp probably crashed!
```
So I tried to uninstall amaroK, clean any remaining debs, and reinstall amaroK - still nothing.
I tried to remove all my amarok settings etc - no difference.
So I tried to install amarok from svn, hoping that it would fix something - but it didn't.

I know I'm not the only one having this problem, but no one seems to have any solution for this :(

Anyone having the same problem?
Any ideas how to resolve this?

[http://www.ubuntuforums.org/showthread.php?t=72585](http://www.ubuntuforums.org/showthread.php?t=72585)

---

### Post by mlomker on 2005-12-29
I found [this post]("http://www.ubuntuforums.org/showthread.php?p=596778#post596778"). I also recall someone having an issue with an Nvidia driver once that caused the problem, but my memory is fuzzy and I couldn't find a link for that.

---

### Post by monotux on 2005-12-30
No, it was the nvidia driver that was the problem (WTF?! :confused: )

I reinstalled nvidia the proper ubuntu-way, rebooted, and everything worked - even amarok :D

If anyone is interested, I used the instructions found in /usr/share/doc/nvidia-kernel-source/README.Debian.gz

:)

---

### Post by veloct on 2005-12-30
cool. What version of amarok are you using? 1.3.7 is available through [kubuntu.org/announcements/amarok-1.3.7.php](kubuntu.org/announcements/amarok-1.3.7.php)

---

