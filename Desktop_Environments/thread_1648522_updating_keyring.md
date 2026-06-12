---
title: "updating keyring"
date: 2010-12-18
forum: Desktop Environments
---

### Post by zander1013 on 2010-12-18
hi,

i changed my account password but now when i log in a keychain manager pops up and asks for the old password to join wifi.

how can i update the keychain password to match the account password please?

thank you.

---

### Post by asmoore82 on 2010-12-18
(tested on Ubuntu 10.04)

Open "Applications -> Accessories -> Passwords"

Right-click the "Passwords: login" keyring and pick "Change Password" at the bottom.


This problem should not happen if you use the "Change Password" button
under "System -> Preferences -> About Me." This is the subtle difference
between an unprivileged user changing their password and an administrator
reseting their password. On a default Ubuntu Desktop installation,
this user and this administrator are the same person/account.

---

### Post by mcduck on 2010-12-19
Are you really still running 8.04 (like your profile says)? 

In that case the right place is Applications/Accessories/Passwords and Encryption Keys.

If you are using 10.10, the tool has been moved to System/Preferences/Passwords and Encryption keys.

---

### Post by zander1013 on 2010-12-19
hello everyone and thank you for your help.

i am using 10.10 now. i just upgraded yesterday.

i used System>Admin>Users and Groups to update my account login password.

the prompt from the Keyring is for my old account password when i login to use the wep password for my wifi.

the password manager suggested by mrduck appears to be for changing the wep password to join my wifi not the old keyring password that is now required to use the wep password to join my wifi.

the Applications>Accessories>Passwords app is not present in that location on my 10.10 distro. and i cannot find it anywhere else in the menus.

however i just tried to change my password using System>Preferences>About Me.

regrettably i am still being prompted for the old (original) account password by the Keyring to join my wifi.

thank you for any farther suggestions you may have.

---

### Post by mcduck on 2010-12-20
> **zander1013 said:**
> so its a bug then?

No.

You are just not following our instructions exactly. ;)

1. Go to System/Preferences/Passwords and Encryption Keys

2. *Right-click* on the "Passwords:login"-keyring. (no left click, you don't want to open the keyring and view it's contents)

3. Select "Change Password" from the popup menu.

4. Type in the old password and set new one to same as your current login password..

---

### Post by zander1013 on 2010-12-20
thank you mrduck.

this thread is solved.:)

---

