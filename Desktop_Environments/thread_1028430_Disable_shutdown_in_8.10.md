---
title: "Disable shutdown in 8.10"
date: 2009-01-02
forum: Desktop Environments
---

### Post by jackocleebrown on 2009-01-02
Hello,

I have a computer which is used by several remote users at once (using freenx).

With previous versions of Ubuntu it was possible to prevent users from shutting-down or restarting the system by removing the "actions menu" option in the login window settings (SystemMenu=false in gdm.conf).

However with 8.10 and the introduction of the combined user-switching/guest-login panel applet this approach no longer works.

I have seen some solutions using the policykit to modify the authorizations required for shutdown but it appears that these settings are not universally obeyed (it is still possible to shutdown the machine from system-shutdown).

Is there another approach to this problem?
Do all these functions ultimately call /sbin/halt or /sbin/shutdown perhaps I can limit the permissions on these?


Thanks, Jack.

---

