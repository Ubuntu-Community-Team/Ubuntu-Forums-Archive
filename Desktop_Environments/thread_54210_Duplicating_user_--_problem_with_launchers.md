---
title: "Duplicating user -- problem with launchers"
date: 2005-08-03
forum: Desktop Environments
---

### Post by reedlaw on 2005-08-03
I am trying to make a user account with customized settings and several desktop launchers in order to copy it to many other accounts.  The problem I have is the launchers appear as "no name" when I copy them to a separate account.  The method I am using to duplicate the user accounts is:
```
tar cvpzf ./user.tgz /home/user
scp user@host:user.tgz
tar xvpzf ./user.tgz -C /home/user
```
Where do launchers reside in my user directory?   Does anyone know the reason for this behavior?

---

### Post by reedlaw on 2005-08-04
I found the answer myself:
The launcher contained a name with a corresponding locale such as:
Name[en_US]=Test

When it was copied, the computer viewing it had a different locale so the name appeared as "No name".  So I resolved it by simply substituting the following line in the launcher file:
Name=Test

---

