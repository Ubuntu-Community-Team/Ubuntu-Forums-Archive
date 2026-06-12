---
title: "VMWare"
date: 2009-05-12
forum: General Help
---

### Post by kc3 on 2009-05-12
Okay, I tried to install VMWare, I went through the normal process however after it DID install it just said I didn't have permission to run the VMWare file, I uninstalled it and now when I try to reinstall it, it says there's already VMWare installed and it can't uninstall and it aborts. Anyone know what to try???

---

### Post by dbuttera187 on 2009-05-12
does it allow you to type an administrator password when you try? usually when it is about permissions it seems to be root privelages.

---

### Post by kc3 on 2009-05-12
No it doesn't, if I try just to open the player it says that doesn't even exist. Also, it's removed now (properly uninstalled I thought) and won't let me reinstall.

---

### Post by sideffects on 2009-05-12
Did you go into Nautilus and make sure that the folder is gone?

---

### Post by dbuttera187 on 2009-05-13
i don't know if there is any stability issues in doing this or not but i believe there is a sudo command that will let you force an install

---

### Post by kc3 on 2009-05-13
Yeah the directory is totally gone, also I did install it with a sudo command

---

### Post by dcstar on 2009-05-13
> **kc3 said:**
> Okay, I tried to install VMWare, I went through the normal process however after it DID install it just said I didn't have permission to run the VMWare file, I uninstalled it and now when I try to reinstall it, it says there's already VMWare installed and it can't uninstall and it aborts. Anyone know what to try???

Look in the Virtualization forum for answers.

---

### Post by kc3 on 2009-05-13
Oh okay, my bad, I didn't see there was another forum for it.

---

### Post by IamWayne on 2009-05-13
Will someone please explain how to install vmware on jaunty?

---

### Post by kc3 on 2009-05-15
Just fyi, I got it fixed sorta, I deleted the /etc/vmware directory so it now doesn't pick up as installed lol, and I said forget it to VMWare and installed VirtualBox instead :P VirtualBox is MUCH easier of a setup, fully compatible and is a GNU license :D I would definitely recommend it to anyone else trying to figure out VMWare

---

