---
title: "alter environment variables mid-flight"
date: 2010-10-22
forum: Desktop Environments
---

### Post by sonic6567 on 2010-10-22
Hello,

Can anyone please help?

I have variables set in my /etc/environment.

I need them changed without rebooting.  Any answers?

I can change the /etc/environment file but it has already been read and loaded at boot so that doesn't help.

I can override with a bashrc or /etc/profile but that only works for new terminals.

I need programs that run outside a terminal (such as checkgmail, avant-window-navigator, update-manager, etc) to respect the new /etc/environment.

This is all over a proxy issue.  At times I need a proxy enabled. At others, I need it disabled. But I cannot reboot between the change.  Programs like those I mentioned before will not respect a proxy change without a reboot.

Can any advise?

Thank you

---

### Post by sonic6567 on 2010-10-25
bump

---

### Post by 3Miro on 2010-10-25
You don't need to reboot to set proxy in Firefox, I am not sure about other programs. For proxy in particular, doing:
```
 sudo services networkmanager restart 
```
should do the trick (it might be NetworkManager). You can also try to disconnect/connect to the network.

Other than that, I only know the:
```
 source /etc/profile 
```
but I don't know if it will have a global effect.

---

### Post by sonic6567 on 2010-10-25
Thanks for the info.

You are right, those suggestions will work for applications that run under the user area, ie. browser etc.
But that will not work for programs that use the environment - ie, update-manager etc.

I need some way to reset the environment.

---

### Post by sonic6567 on 2010-10-27
bump

---

### Post by sonic6567 on 2010-11-02
bump

---

