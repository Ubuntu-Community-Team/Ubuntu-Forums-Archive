---
title: "desktop effects and fast user switching."
date: 2007-12-27
forum: Desktop Effects &amp; Customization
---

### Post by notquitemichael on 2007-12-27
Hey,
  and apologies if this has already been asked: i couldn't find it.

Does anyone else have the following problem, and if so have they managed to fix it?

When running compiz desktop effects on one user account, if i fast-user-switch to another account the desktop effects cannot be enabled (comes up with an error to that effect if done through desktop-appearance.)

Therefore it would seem that compiz is limited to a single concurrent user? Is this the case, or is it just my machine.

Worth noting that both accounts, if logged in separately, run compiz fine on their own. 

---

I'm running a Dell N series laptop, official with Ubuntu. The video drivers a Intel i810, so i'm begining to think it may be memory related? 

Thanks,

Michael

---

### Post by Forlong on 2007-12-27
It's just not possible. Compiz is still running on the first user's X-server. You have to log that one out before using the effects on somebody else's account.

---

### Post by notquitemichael on 2007-12-27
well it's good to know it's not strictly a bug. although it is a tad annoying.
does anyone know if it is possible to get the fast-user-switching applet to run a script before switching (i.e. to change the windowmanger back to metacity, map the windows etc.) and then just after the switch (i.e. to turn on compiz, dbus the windows back to their original place on the cube?)
i'm pretty sure i know how to script it, (well, might have to investigate about the window mapping,) just don't know enough about how the user-switching actually works.
would be a useful inclusion.,

---

### Post by Forlong on 2007-12-27
Just switching to Metacity doesn't help. You have to log the first user out. There's no way around it.
If it's important to you, file a feature request at bugzilla.gnome.org (but frankly I doubt they can do something about this).

---

