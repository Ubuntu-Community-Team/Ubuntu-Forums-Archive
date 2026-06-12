---
title: "boot failure (job control turned off)"
date: 2006-05-10
forum: Desktop Environments
---

### Post by hldub on 2006-05-10
I installed ubuntu on my laptop beside windows xp pro. The install went fine and I booted up, logged in, fooled around, set up samba, shut down, logged in again etc etc. I then booted win xp and worked in it for a while. When I tried to log back into ubuntu I got the following message:

target system does not have /sbin/init
...
can't access tty: job control turned off

And then a restricted shell that does very little. A similar problem happened before on the same machine. I installed & used ubuntu successfully. Left it for a while and then found that it would not boot, although for a different reason that I forget.

I have explore2fs set up on windows but have not used it at all.

**EDIT - Actually I think its ext2fsnt (filesystem driver) that I have installed but I'm still not 100% sure. **

Can anyone help?

---

### Post by hldub on 2006-05-10
On further inspection I have discovered that Google Desktop (under windows) has written to the L: drive, which is my ubuntu partition (I'm pretty sure I'm using ext2fs now that I found the driver in system32). The presence of a folder called '/Google Desktop Data' made this pretty clear. I am thinking that this has spoiled my linux filesystem. I'm hoping to be able to fix it so if anyone has any ideas I would be grateful (will search google). Otherwise I will uninstall Google Desktop & reinstall ubuntu ...

---

