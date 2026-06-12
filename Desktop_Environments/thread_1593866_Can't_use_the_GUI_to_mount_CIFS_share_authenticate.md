---
title: "Can't use the GUI to mount CIFS share authenticated if it also accepts guest logins"
date: 2010-10-11
forum: Desktop Environments
---

### Post by PaulForgey on 2010-10-11
At least using Ubunto 9.10, it seems impossible to authenticate a connection to a Windows/CIFS share if the server also accepts guest logins (at least to allow enumeration of the available shares). This is not an uncommon setup. In fact SMB file sharing from Mac OS does it this way out of the box by default.

It should be possible to at least re-authenticate once connected. In the "Connect to Server" dialog, even if I fill in the User Name field, there is never any opportunity to authenticate using a password.

Is this a known bug (I couldn't stumble upon the magic search pattern in launchpad if it is), or is there an easy workaround? This seems like a pretty basic deficiency.

---

