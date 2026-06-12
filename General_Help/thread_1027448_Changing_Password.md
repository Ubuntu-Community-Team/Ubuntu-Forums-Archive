---
title: "Changing Password"
date: 2009-01-01
forum: General Help
---

### Post by joshh88 on 2009-01-01
I searched and tried the method via user and groups, but that only changed the sign on password. I want to change the sign on password and the administrator password to the same one.

---

### Post by taurus on 2009-01-01
What do you mean you want to make your password and the administration password to be the same?

Are you talking about sudo or root account?

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by MaxIBoy on 2009-01-01
With sudo, you can run root programs using the password of the first account you created. 

Try pulling up a terminal and running "man sudo."

---

### Post by joshh88 on 2009-01-01
Sorry I forgot thats what it is called in Linux yes the root sudo pass

---

### Post by snova on 2009-01-01
> **joshh88 said:**
> Sorry I forgot thats what it is called in Linux yes the root sudo pass

There is only one password, and that's yours. sudo uses the same one.

If you changed your password, sudo will accept this new one as will everything else that requires it.

---

### Post by joshh88 on 2009-01-01
It's not working like that, I login with one and anything in terminal has to have the original password. I must have done something wrong.

---

### Post by joshh88 on 2009-01-14
I know what it is now. Whenever I log in it asks for my old password for the keyring, some reason the keyring is used to start the wireless everytime. So I either need to get it to autofill and never bother me about it or change the keyring password to my new one.

---

### Post by matey3 on 2009-01-14
passwd root
will change the root password.
if you are root of course, if not then sudo or just su
then passwd username

---

