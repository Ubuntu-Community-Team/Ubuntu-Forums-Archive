---
title: "Creating an admin user called 'admin' causes problems"
date: 2009-05-04
forum: General Help
---

### Post by jonboy99 on 2009-05-04
Something i've noticed ever since gutsy, is that if I install the system with the original username (and therefore with admin privileges) called lets say, 'jon', and then once the system is booted up, as 'jon' I create another user called 'admin' and give 'admin' admin privileges, it consistently cocks up my 'jon' user and takes away the admin privileges.  The only way to restore admin privileges is from the console using the adduser command, it can't be done via the gui.

It seems when you create a user with admin privileges, and actually call that user 'admin' it causes problems, yet I haven't read anywhere about why we shouldn't do this.  Is it a bug?

I haven't tried it in jaunty yet, but certainly it happens in gutsy, hardy and ibex.

---

### Post by geirha on 2009-05-04
Yes, it's a known bug. [https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/236305](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/236305)

The group called admin is the group you need to be in if you should be allowed to use sudo. And when you create a user, a group by the same name is created as well, which overwrote the previous admin group when creating a user called admin. It was recently fixed and I remember seeing an update for it for either Hardy or Intrepid very recently.

---

### Post by jonboy99 on 2009-05-04
good to know, thanks.

---

