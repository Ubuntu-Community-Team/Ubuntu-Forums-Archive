---
title: "Update Manager, allowing another user to run?"
date: 2006-02-18
forum: Desktop Environments
---

### Post by chris_andrew on 2006-02-18
Hi,

When Update-Manager required updates, one of my users need to be permitted to cary out the update. How do I permit them to do this?  I can do it as the 1st user, which I guess is a *sudo* thing.

Any help appreciated.

Cheers,

Chris.

---

### Post by Florob on 2006-02-18
They have to be added to the admin group, but this will also give them sudo rights etc., but I guess that is okay for you.

Note: This is only true for a breezy install, with a pre-breezy install (even if updated to breezy) you'll have to manually change the sudoers file AFAIK.

---

### Post by chris_andrew on 2006-02-18
Sorted.

Many thanks,

Chris.

---

