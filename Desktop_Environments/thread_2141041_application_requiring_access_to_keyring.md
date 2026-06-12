---
title: "application requiring access to keyring"
date: 2013-05-01
forum: Desktop Environments
---

### Post by naseeem on 2013-05-01
hi,
i'm new to ubuntu , iv'e installed ubuntu 13.04 on separate clean partition .
almost every time i logon i get a message saying :
"an application needs access to the keyring please enter password to confirm"  or something like that .
does anyone have any idea ???

---

### Post by mcduck on 2013-05-02
Well, it's exactly what the message is saying. The keyring is used to securely storage passwords, encryption keys and other such information for various applications. And the message is telling you that some application is trying to access this information, and requires you to input your password to unlock the keyring.

As long as you use normal login with password, and your keyring password is set to same as your login password, the keyring should be unlocked automatically when you log in. Otherwise, if you use automatic login without a password, or have a different passwords for login and keyring, you'll need to unlock the keyring manually first time some program needs to access it.

If you are using a password-free login, you probably don't feel like you'd need the security keyring offers, so you may as well set the keyring password to empty one, which will allow programs to access it without having to ask for your confirmation.

...And if you are using login with password, but have changed your login password recently, simply changing the keyring password to match the login one should get the automatic unlocking working again.

In either case the tool to manage your keyring and change it's password is called "Passwords and Keys", and once take a look at the left side panel, under the "Passwords" section there should be an item called "Login". Right-click it and select "Change Password".

---

