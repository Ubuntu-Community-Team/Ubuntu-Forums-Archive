---
title: "Truecrypt 6.1 and Intrepid"
date: 2009-01-27
forum: General Help
---

### Post by psuliin on 2009-01-27
I'm running Xubuntu 8.10, and recently installed Truecrpyt 6.1a.  When I double-click a mounted file it does not open as it should.  Instead I get a "No such file or directory" error.  However the encrypted volume is mounted in the /media directory.  Yet it doesn't show in Thunar.

Any idea what's happening?

---

### Post by adamlau on 2009-01-27
Did you add the following to you sudoers file:

```
%truecrypt ALL=(root) NOPASSWD:/usr/bin/truecrypt
```

And add the appropriate group and user to the group:

```
groupadd truecrypt && gpasswd -a *user* truecrypt
```

Where *user* is your login name?

---

### Post by psuliin on 2009-01-27
Hmm.  No, I haven't tried that.  I had no idea I needed to.  Where is the sudoers file located?

---

### Post by rsay on 2009-02-10
/etc/sudoers

---

