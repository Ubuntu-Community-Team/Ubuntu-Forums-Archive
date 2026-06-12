---
title: "Can't get root access in GUI (pkexec broken)"
date: 2011-11-24
forum: Desktop Environments
---

### Post by cogcog on 2011-11-24
I'm having so many issues with 11.10. It feels like an alpha release.

The latest thing is that I can no longer enter my password to get root permissions graphically. The policykit agent dialog comes up asking for my password, but the password input field is greyed out.

Opening an application from the command line using "pkexec" has the same effect (I get the dialog, but the input is disabled). However, "gksudo" works just fine: I can type my password in and then the application runs as root.

---

