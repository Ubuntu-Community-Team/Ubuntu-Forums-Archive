---
title: "Having a problem with f-prot antivirus....."
date: 2006-08-21
forum: Desktop Environments
---

### Post by someguyouknow on 2006-08-21
I was trying to install it via Adept and i get a prompt for different methods of installation.  I choose to download and install and it hangs.  I am assuming that it is no longer available at that location.  So now, i decide i dont want to install it anymore.  But it comes up everytime i use Adept or using konsole to update and such.  I cant even use Automatix right now because of it.  Is there a way i can just cancel that installation?.....

thanks in advance.....

---

### Post by Patrick-Ruff on 2006-08-21
just a question but...why exactly do you need an anti-virus?

---

### Post by arnieboy on 2006-08-21
> **someguyouknow said:**
> I was trying to install it via Adept and i get a prompt for different methods of installation.  I choose to download and install and it hangs.  I am assuming that it is no longer available at that location.  So now, i decide i dont want to install it anymore.  But it comes up everytime i use Adept or using konsole to update and such.  I cant even use Automatix right now because of it.  Is there a way i can just cancel that installation?.....

thanks in advance.....

cancel the installation and make sure adept is gone and then do the following from terminal:
```
sudo apt-get -f install
```
and then run automatix or whatever you want. 
A personal recommendation: **Please DO NOT use adept**. Its buggy as hell. Use synaptic instead.

---

### Post by someguyouknow on 2006-08-21
Thanks!!!
i guess i will get synaptic too.

oh and i installed the antivirus cause i am paranoid. lol

---

