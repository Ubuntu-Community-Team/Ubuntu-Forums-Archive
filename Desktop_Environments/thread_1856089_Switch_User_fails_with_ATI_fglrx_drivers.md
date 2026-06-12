---
title: "Switch User fails with ATI fglrx drivers"
date: 2011-10-07
forum: Desktop Environments
---

### Post by nicolasavru on 2011-10-07
Background information:
We have a 12 Dell Vostro 220 workstations with ATI Radeon HD 3450 video cards that have a local user account and are also able to authenticate against an LDAP user (with NFS auto-mounted home directories).

Issue:
After a user does not log off and locks his screen, hitting "Switch User" causes the screen to flash several times, as if the video mode/resolution is being adjusted, after which the screen returns to the Unlock/Switch User dialog. This makes it impossible for anyone else to log in if a user does not log off and the screen locks.

We believe that this is related to the ATI video driver, as we have newer Dell workstations with Nvidia video cards which were imaged from the same image and which do not experience the issue.

This issue is not perfectly reproducible, as it does not every time that the screen is locked. In addition, it we have only observed the issue with LDAP accounts, not with the local account.

System information:
Ubuntu 11.04 x86_64 2.6.38-11
ATI Radeon HD 3450

output of fglrxinfo:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3450
OpenGL version string: 3.3.10665 Compatibility Profile Context

Any suggestions would be appreciated.

---

