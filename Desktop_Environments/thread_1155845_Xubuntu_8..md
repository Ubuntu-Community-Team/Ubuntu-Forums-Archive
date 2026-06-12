---
title: "Xubuntu 8."
date: 2009-05-11
forum: Desktop Environments
---

### Post by mltom on 2009-05-11
I created a user signon, but lately when one signs on as the user; up at the top, the 'application', bar is not there. Thats where I usually go to find my browser. If its accidently hidden, how does one make it reappear?

tks
tom

---

### Post by Lampi on 2009-05-11
this **IS** a new user, right? so you didn't change a lot in configuration and desktop appearance before this happened?

Well, something messed up your config entries in /home/signon/.config. I experienced the same some while ago - the easiest way is to terminate Xsession of this user, and then backup + rename /home/signon/.config, so XFCE won't see it if you login user signon again next time.

XFCE will recreate the .config directory for you. Like this you'll get a completely fresh desktop configuration.

---

