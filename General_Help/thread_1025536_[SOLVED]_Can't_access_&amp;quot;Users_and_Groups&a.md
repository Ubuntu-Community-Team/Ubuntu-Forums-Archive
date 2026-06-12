---
title: "[SOLVED] Can't access &amp;quot;Users and Groups&amp;quot;"
date: 2008-12-30
forum: General Help
---

### Post by colin.p on 2008-12-30
I am running 8.10 and get the error "User's $HOME/.dmrc file is being ignored. This prevents the default session and launguage from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

I was trying to fix the problem without RTFM, and put my username "colin" as part of the admin group (at least I remember putting a check by "admin"), when that didn't fix anything, I removed myself as an admin. Now I of course have locked myself out. 

Now I have found the thread on how to fix the original error, but when I type "sudo chown colin /home/colin/.dmrc" I get an error "colin is not in the sudoers file.  This incident will be reported." Since I had locked myself out to change my username back to an administrator, how do I allow myself access to be able to get rid of the original error?

Thank you

Colin

---

### Post by albinootje on 2008-12-30
> **colin.p said:**
>  Now I have found the thread on how to fix the original error, but when I type "sudo chown colin /home/colin/.dmrc" I get an error "colin is not in the sudoers file.  This incident will be reported." Since I had locked myself out to change my username back to an administrator, how do I allow myself access to be able to get rid of the original error?


1) Boot into "recovery mode"
2) Choose "root shell prompt"
3) Type in : adduser colin admin
4) Type in : telinit 2

After that your user should be in the admin group, and therefore able to use sudo.

---

### Post by colin.p on 2008-12-30
Thanks, that worked perfectly and I was able to fix the original error as well. 

Colin

---

