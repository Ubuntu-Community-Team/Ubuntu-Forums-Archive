---
title: "setting default umask with gdm"
date: 2005-11-17
forum: Desktop Environments
---

### Post by TizianoTissino on 2005-11-17
Hi folks,

I need to set a different default umask for my users.
I installed libpam-umask and added the following line to /etc/pam.d/common-session:

session required        pam_umask.so umask=0007

This works fine using login, but doesn't work with gdm.

Indeed, I noted that files created trought nautilus have mod=0600, while 
files created in a gnome-terminal shell have mod=644.

It's a bug on gdm or am I missing something?

---

### Post by TizianoTissino on 2005-11-18
I solved in some way the problem, adding the file .gnomerc on each user profile. On that file, I add the following line:
umask 0007

However, I think gdm should take better care of PAM settings...

---

### Post by andmer on 2006-04-13
hi Tiziano,
could u tel me where do I find the file .gnomerc and how do I add it to eah user profile.

I have a big problem with umask. I exported a share directory with NFS (it works) but I would like that each user had the permission to create new file with umask 0002.

Thank u

ciao

Andrea

---

### Post by andmer on 2006-04-14
as a matter of fact I added the line umask 0002 to the end of /etc/X11/Xsession.d/55gnome-session_gnomerc and the global umask has change also in gdm session.

Ciao

Andrea

---

### Post by Lirritan on 2006-04-21
It does works perfecly.  

Thanks Andrea.

Lirritan

---

