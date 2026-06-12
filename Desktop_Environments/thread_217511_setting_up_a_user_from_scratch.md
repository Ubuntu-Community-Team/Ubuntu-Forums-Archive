---
title: "setting up a user from scratch"
date: 2006-07-17
forum: Desktop Environments
---

### Post by Blutack on 2006-07-17
I used an alternative install cd to install to my dell inspiron 2200.  However the installer kept crashing at random points during install (possibly due to power management?).  Anyhow, with a combination of the kubuntu cd and knoppix I managed to install the rest of kubuntu-desktop and ubuntu-minimal.  My system now works fine.  I added a user using recovery mode and the command adduser.  However, I had to manually add myself to groups dvd, audio, plugdev etc.  I have a standard (updated) install of breezy.  What groups should my user be in to have a secure and yet usable system?  Or is there a script to do it?  Users and groups crashes in kcontrol.  I also do not have a shadow file, though I managed to edit sudoers.  Many thanks in advance.

---

### Post by aysiu on 2006-07-17
You should belong to:
```
adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin
```

---

### Post by Blutack on 2006-07-20
Brilliant!  Many thanks.  There is absolutely no documentation I could find about this on the web anywhere.

---

