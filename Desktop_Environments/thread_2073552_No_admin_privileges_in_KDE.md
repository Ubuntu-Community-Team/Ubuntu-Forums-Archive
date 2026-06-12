---
title: "No admin privileges in KDE"
date: 2012-10-19
forum: Desktop Environments
---

### Post by Deucalion29710 on 2012-10-19
I don't seem to have admin privileges in KDE Plasma.  I can't install anything via synaptic or software center.  This is baffeling as I am the only user.  How do I gain admin?

---

### Post by bra|10n on 2012-10-19
Assuming you have installed kubuntu-desktop over xubuntu then the I'd say your issue stems from the menu for both synaptic and software center not calling either application with sudo privileges. 
You should be able to start either from a terminal with *gtksu synaptic* for example...

---

### Post by Deucalion29710 on 2012-10-19
> **bra|10n said:**
> Assuming you have installed kubuntu-desktop over xubuntu then the I'd say your issue stems from the menu for both synaptic and software center not calling either application with sudo privileges. 
You should be able to start either from a terminal with *gtksu synaptic* for example...

Well it all occurred after I installed KDE Plasma.  Looks like I was able to get straight after using gtksu, so now both work right again.

---

