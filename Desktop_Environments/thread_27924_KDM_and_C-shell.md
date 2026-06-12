---
title: "KDM and C-shell"
date: 2005-04-18
forum: Desktop Environments
---

### Post by whittycat on 2005-04-18
I have just installed Kubuntu and I have a problem with KDM. I like the C shell so I changed the login shell (by editing /etc/passwd but changing it via the KDE Control Centre behaves the same way) and I then found that I could no longer log in to KDE -- I type in the username and password and it just gives me the login window again. Is there a wrietaroud for this?

Tony Sumner

---

### Post by raoaksha on 2005-07-27
Even I'm having a similar problem. (kdm and tcsh)..
tried changing the default shell for the user to tcsh by manually editing /etc/passwd
and by sudo usermod -s /bin/tcsh <userid>
like whittycat says, get the login window again.

what am i doing wrong here??

---

