---
title: "xfce panel doesn't load for user"
date: 2008-07-26
forum: Desktop Environments
---

### Post by qe2eqe on 2008-07-26
User Admin has sudo privilege. User D is restricted. When Admin loads and uses 'switch user' to get to User D, the xfce panel loads. When Admin is fully logged out, User D logs on with no xfce panel.
Should I file a bug report?

---

### Post by him610 on 2008-07-26
I am running Xubuntu 8.04 which uses the XFCE user interface on two machines which I booted up a few minutes ago. Neither one has the XFCE panels present, not the upper one nor the lower one.

This is a bug for sure.

---

### Post by him610 on 2008-07-26
Re: Bug #53897 in Launchpad

> By default, XFce saves your settings when you exit it. If the taskbar was gone when you exited XFce, it won't appear the next time you start XFce. So doing Alt-F2 and typing xfce4-panel will make the XFce panel reappear and if it's there when you exit, it'll be there the next time you start. At least that's how it's supposed to work.

This remedy worked for me.

---

### Post by crewkid89 on 2008-08-19
Thanks this just worked for me.  I have been trying to get this to work for a few days.  My problem was that the session manager wasn't saving the sessions at shutdown so every time I logged in the panel was missing.  Make sure you check your settings manager for this if anyone is still having problems.

---

