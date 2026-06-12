---
title: "XDG_DESKTOP_DIR and smb mount fail"
date: 2010-03-26
forum: Desktop Environments
---

### Post by Bufke on 2010-03-26
I want to mount the Desktop folder in Active Directory to ~/Desktop which I can do with pam_mount.  However it seems to break Gnome's XDG_DESKTOP_DIR and defaults it to ~.

Looking in ~/.config/user-dirs.dirs confirms this.  Does anyone know a solution to this?  My fear is people will save things to the Desktop thinking it's in the share, which is how Windows is set up at my work.  Maybe there is another way to do this?  I'm using likewise-open5 to authenticate to AD on ubuntu 9.10

---

