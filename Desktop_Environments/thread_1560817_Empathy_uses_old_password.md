---
title: "Empathy uses old password"
date: 2010-08-25
forum: Desktop Environments
---

### Post by jrounds on 2010-08-25
On a new user account, I setup empathy to use yahoo messenger.  Shortly thereafter I changed two settings: I now login without using password on startup, and I changed my password for my account.  Now when I start empathy after a reboot it says my key has not been unlocked (expected), but then it doesn't accept my new user account password, but rather uses the old one.  How do I get empathy to start fresh with my current password?

---

### Post by mcduck on 2010-08-25
> **jrounds said:**
> On a new user account, I setup empathy to use yahoo messenger.  Shortly thereafter I changed two settings: I now login without using password on startup, and I changed my password for my account.  Now when I start empathy after a reboot it says my key has not been unlocked (expected), but then it doesn't accept my new user account password, but rather uses the old one.  How do I get empathy to start fresh with my current password?

It's not Empathy that's using the old password, it's Gnome's keyring.

To change the password go to Applications/Accessories/Passwords and Encryption keys. Right-click the "passwords:login"-keyring and select "Change password".

(you can also set the password to empty one, which allows the keyring to unlock without you having to input a password. Sometimes useful if you are using automatic login, although less secure but considering the automatic login it makes no difference)

---

