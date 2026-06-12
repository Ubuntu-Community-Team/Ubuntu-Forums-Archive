---
title: "changing password"
date: 2010-07-18
forum: Desktop Environments
---

### Post by Amy_1990 on 2010-07-18
Hi again,

When i installed ubuntu i gave it a password but now when i try to change it from the me-menu it now has two passwords i don't want this i want it with just one like it was when i installed ubuntu is there a way to do this?

---

### Post by nothingspecial on 2010-07-18
What do you mean you have 2 passwords. Is one for the keyring?

---

### Post by Amy_1990 on 2010-07-18
I'M not sure when i login i have to use the old and then the new password but after that i have to use the new one.But when i install software it only will take the old password.

---

### Post by nothingspecial on 2010-07-18
> **Amy_1990 said:**
> I'M not sure when i login i have to use the old and then the new password but after that i have to use the new one.But when i install software it only will take the old password.

Try typing in your terminal
```

mv ~/.gnome2/keyrings/default.keyring ~key.bak
```
Then log out and back in again. The keyring should ask you for a new password. Set it the same as your new admin password.

I hope I`ve understood what is going on correctly.

---

### Post by mcduck on 2010-07-19
> **nothingspecial said:**
> Try typing in your terminal
```

mv ~/.gnome2/keyrings/default.keyring ~key.bak
```
Then log out and back in again. The keyring should ask you for a new password. Set it the same as your new admin password.

I hope I`ve understood what is going on correctly.

There's no need to get rid of the current keyring change the password. :) The keyring password can be changed in Applications/Accessories/Passwords and Encryption Keys. Just right-click the "passwords:login"-keyring and select "Change Password".

---

### Post by aeiah on 2010-07-19
if you need your old password to login, then that suggests that you never changed your password to begin with (but perhaps changed your keyring one, or something).

you can change your login password (and thus also the password used for sudo) in a terminal with the command:```
passwd
```

---

### Post by dcommini on 2010-07-26
> **aeiah said:**
> 
you can change your login password (and thus also the password used for sudo) in a terminal with the command:```
passwd
```

Sweet, this just helped me with the problem I was having, using the GUI I could not change my password. got it taken care of now... ty;)

---

