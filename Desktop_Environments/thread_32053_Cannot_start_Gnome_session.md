---
title: "Cannot start Gnome session"
date: 2005-05-05
forum: Desktop Environments
---

### Post by jmf on 2005-05-05
Please help !!!

Cannot start Gnome session after login using PAM_LDAP, PAM_MOUNT & smbmount
(Note login & mount of homefolder works ok for terminal only session)

gnome-session error is "Unable to lock ICE authority file ~/.ICEauthority"

After searching gnome and x11 source code I find that gnome (ie X11/ICE) is trying to create a sym link on the smbfs homefolder

Is there a version of smbmount which supports sym links ???

Or is there a version of ubuntu/gnome which dosen't require X11/ICE ???

Or is there another solution ???

---

### Post by jmf on 2005-05-10
I found a solution if anyone is interested

Put the following 2 lines in /etc/gdm/Xsession or use PAM_ENV to do it

ICEAUTHORITY="/tmp/ICEauthority-${USER}"
export ICEAUTHORITY

---

### Post by Oliver.Epper on 2006-02-07
THX jmf !!! This was bugging me for two days :( It even made me install SUSE 10 for testing purpose *harhar*.

---

