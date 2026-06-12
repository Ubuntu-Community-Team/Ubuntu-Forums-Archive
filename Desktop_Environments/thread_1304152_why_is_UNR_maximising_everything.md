---
title: "why is UNR maximising everything?"
date: 2009-10-29
forum: Desktop Environments
---

### Post by ricardopresto on 2009-10-29
Hi

Does anyone know how to stop UNR opening every window maximised by default? Usually it's not a problem but with some apps - IDLE for example - even dialog boxes open maximised! Using Compiz at the moment but have the same problem with Metacity.

richard

---

### Post by wilee-nilee on 2009-10-29
> **ricardopresto said:**
> Hi

Does anyone know how to stop UNR opening every window maximised by default? Usually it's not a problem but with some apps - IDLE for example - even dialog boxes open maximised! Using Compiz at the moment but have the same problem with Metacity.

richard

 I believe if you go to the start-up applications in preferences and tick it off, that will fix the maximising. I don't know if you have to log off or restart to get it turned off.

---

### Post by ricardopresto on 2009-10-29
> **wilee-nilee said:**
> I believe if you go to the start-up applications in preferences and tick it off, that will fix the maximising. I don't know if you have to log off or restart to get it turned off.

That's fixed it. Thanks mate :D

---

### Post by gjoellee on 2009-10-29
> **ricardopresto said:**
> Hi

Does anyone know how to stop UNR opening every window maximised by default? Usually it's not a problem but with some apps - IDLE for example - even dialog boxes open maximised! Using Compiz at the moment but have the same problem with Metacity.

richard

I can tell you why... UNR (Ubuntu Netbook Remix) is designed for netbooks. Netbooks have small screens at you save screen space by maximizing every window (same as maximize using F11).

---

### Post by Katalog on 2009-10-29
I don't think you have to completely disable Maximus altogether if you don't want to. I believe there is a setting in gconf editor where you can disable this behavior on a per application basis (i.e. Pidgin), It's just been so long since I've done it that I can't remember exactly where it is. I'll have to poke around and see if I can find it again and report back (in the event anyone's interested).

EDIT: Found it. If you go into gconf editor under "apps" and select "maximus" there is a key that you can edit called "exclude_class". Just right click on it, select "Edit Key" and then click "Add" in the dialog box and you should be able to add a new value for the app that you don't want to be affected.

---

