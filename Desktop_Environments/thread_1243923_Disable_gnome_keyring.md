---
title: "Disable gnome keyring?"
date: 2009-08-18
forum: Desktop Environments
---

### Post by TheIdiotThatIsMe on 2009-08-18
Hi, I have setup Ubuntu on a family member's computer, which is shared between two people. I have set them both up with separate accounts, each with their own passwords. The problem I have unfortunately, is that they aren't very technically savy, and whenever the computer connects to the wireless network, it asks for the gnome keyring password, which is set to one of their passwords. However, this confuses the second person because they end up having to use two different passwords, one to login, and then one to connect to the internet (I haven't even gotten started on root, I'm hoping that won't come up). Is there a way to disable the keyring and just have it connect to the wireless without it?

---

### Post by mcduck on 2009-08-19
If their login password is the same as the keyring password, and they use password login, they should never be asked for a keyring password separately. The keyring should be unlocked automatically..

(each use has their own keyring, there's no need to use same keyring password between the users).

So I'd suggest just changing their keyring  passwords so that they are same as the login passwords.

Still, if you for some reason or other don't want to do that, the keyring can't be disabled, but removing the keyring password completely stores the keys unencrypted, and the keyring manager won't ask for password any more. In my opinion this only makes sense if you want to use automatic login instead of typing your password at the login screen.

---

### Post by sola on 2009-08-20
Disabling/emptying the keyring password is the most comfortable. I do it on all of my machines especially because I usually set auto-login to the GDM (in that case a normal, non-empty keyring password would be still asked after the desktop is displayed).

---

