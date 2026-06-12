---
title: "GDM serious improvement needed!"
date: 2010-01-06
forum: Desktop Environments
---

### Post by alex69 on 2010-01-06
Hi,

I would use this forum to emphasize a major problem of the ubuntu (in all variants) GDM system:

to avoid the frequent password-insertion in my home PC, I used the automatic login option of GDM (one of the few GDM settings still available fron the release 9.10).
But when the boot just finished and I access the desktop, the first window I can see is the one from network-manager, asking me to insert my password to access the network!!

The contradiction is obvious! Ubuntu auto-login system forgive to transmit the active user permissions to other applications asking for them.

I'd like to see this bug fixed from the next ubuntu releases, and I hope this forum is the right place to catch the official developers attention on this important Ubuntu's improvement.

Alex
Italy

---

### Post by gsmanners on 2010-01-06
It sounds to me like Network Manager is asking for your network password. Your user password and network password are two totally different things and really do need separate logins.

---

### Post by mcduck on 2010-01-06
> **alex69 said:**
> Hi,

I would use this forum to emphasize a major problem of the ubuntu (in all variants) GDM system:

to avoid the frequent password-insertion in my home PC, I used the automatic login option of GDM (one of the few GDM settings still available fron the release 9.10).
But when the boot just finished and I access the desktop, the first window I can see is the one from network-manager, asking me to insert my password to access the network!!

The contradiction is obvious! Ubuntu auto-login system forgive to transmit the active user permissions to other applications asking for them.

I'd like to see this bug fixed from the next ubuntu releases, and I hope this forum is the right place to catch the official developers attention on this important Ubuntu's improvement.

Alex
Italy

That has nothing to do with GDM. And it definitely isn't a bug.

You simply have set a keyring password, so you also need to input that password to unlock the keyring at login time.

If you use normal login (with password) and your login & keyring passwords are the same the keyring will be unlocked automatically. If you don't use login password or have different passwords for login and keyring you need to unlock the keyring yourself, there's no way how it could be unlocked automatically for you (wouldn'r make any sense, really, since password protecting something and then unlocking it without that password would be pointless).

If you want to get rid of such security feature all you have to do is to use the Passwords and Encryption Keys-tool found in Applications/Accessories and set your keyring password to empty one (Just right-click the login keyring on the Passwords-tab and select "Change Password". Input your current password and leave fields for new one empty). This will make the keyring manager to store all your passwords and keys unencrypted, so you won't have to unlock the keyring any more.

---

