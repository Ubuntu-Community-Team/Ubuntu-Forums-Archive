---
title: "XDM says &quot;insecure session&quot;"
date: 2005-05-10
forum: Desktop Environments
---

### Post by agenkin on 2005-05-10
My XDM (that's vanilla XDM, not GDM/KDM) displays the following message at the top of the login box "This is an insecure session".  That is before any user name/password are even entered.

What could that mean?

---

### Post by shakin on 2005-05-10
[QUOTE=agenkin]My XDM (that's vanilla XDM, not GDM/KDM) displays the following message at the top of the login box "This is an insecure session".  That is before any user name/password are even entered.

What could that mean?[/QUOTE]

The session in insecure about itself. Try running an ePsychiatrist program on it.

No, what I think it actually means is that the session is not encrypted. Since X is network transparent it would make a difference on a network login, but for local login it's not an issue.

---

