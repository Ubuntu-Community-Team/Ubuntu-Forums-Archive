---
title: "Acces to default keyring locked"
date: 2009-06-03
forum: General Help
---

### Post by Maysun on 2009-06-03
Now I am really getting frustrated. Nothing seems to work on this computer.
 
I start the computer and now it tells me to give a password, and then I give my password and it keeps being locked.
If I then go to the 'about me' secion and change password section and type in the same password and click 'authenticate' it tells me it is the right password.
 
So what password am I supposed to fill in with this message????:
 
The application 'nm-applet' (/usr/bin/nm-applet) want acces to the default keyring. but it is locked.

---

### Post by lovinglinux on 2009-06-03
Follow this:

> **mcduck said:**
> 
Changing/removing the keyring password is quite easy to do (no need to remove the current keyring or mess with user accounts):

1. open the keyring manager (Applications/Accessories/Passwords and Encryption Keys)

2. Go to Edit/Preferences

3. On the Password Keyrings-tab select the "login"-keyring & click "Change Unlock Password"

Now you can change the keyring password. If you use normal login set the password to same as your login password is to unlock the keyring automatically. If you use automatic login leave the new password fields empty to remove the keyring password.

---

