---
title: "X-Server locks itself out when you change user"
date: 2006-01-19
forum: General Help
---

### Post by zachariah on 2006-01-19
I'm sure there must be something very simple to fix this, but darned if I can figure it out:

Boot up. Log in. Everything works fine.

End current session. KDE logs the current user out.

BUT instead of being greeted by the hi-res Kubuntu logo waiting for the next user to enter their details, it exits to the CLI. You can log in there but when you enter 'startx', X-server refuses to start and says you should delete the file /tmp/.X0-lock.

This being done, X starts up fine and we're back to the KDE desktop.

Special circumstances for this install: It is configured for Active Directory access, so has numerous custom alterations to PAM, kerberos and SMB settings. Though this was the case before and this issue did not arise. I believe this only happened after using sysv-rc-conf to fine-tune startup, but all the changes done have been undone and the X-lock is still occurring.

---

