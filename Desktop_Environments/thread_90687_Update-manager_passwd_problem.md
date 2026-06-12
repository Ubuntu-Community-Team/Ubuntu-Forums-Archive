---
title: "Update-manager passwd problem"
date: 2005-11-15
forum: Desktop Environments
---

### Post by chris_andrew on 2005-11-15
Hi, all.

I have recently installed Breezy.  After the installation, I was prompted bu Gnome's Update-Manager to install some updates (as you'd expect).  I entered the root passwd, but was told it wasn't the correct one, and halted the update process.

The strange thing is that I can open a shell, su to root, dselect and update the system.

I changed the passwd for root, to force an upgrade of the tokens, but still the same problem.  Any ideas?

Thanks,

Chris.

---

### Post by Sheco on 2005-11-15
It's not asking root's password, it's asking for the current user's password.

---

### Post by chris_andrew on 2005-11-15
Dooh!! I'll give it a try.  Will let you know.

Thanks,

Chris.

It worked.  Guess i'll have to add other trusted user to sudo'ers group?

---

