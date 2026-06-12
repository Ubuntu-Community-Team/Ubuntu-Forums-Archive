---
title: "KDE Doesnt Offer Shutdown Options With Compiz-Fusion 0.7 Installed"
date: 2008-04-03
forum: Desktop Environments
---

### Post by Brando569 on 2008-04-03
Im using kubuntu gutsy and when i use compiz fusion 0.7 it doesnt give me any options to shutdown from inside my session. i have to logout and then shutdown, its pretty annoying. anyone know how to fix this?

---

### Post by luisromangz on 2008-04-04
Are you using XGL? It does offer it when using Compiz over X.org with AIGLX.

---

### Post by Brando569 on 2008-04-04
im not at my pc right now but i believe i am, is there anyway to fix this other than uninstalling xgl?

---

### Post by luisromangz on 2008-04-04
I think so, but I haven't used it because although I had the same problem so I started using the newer ATI driver with AIGLX support to get rid of it.

---

### Post by Brando569 on 2008-04-04
im using nvidia drivers and someone told me to install xgl i believe cuz compiz 0.7 was being slow. i really need to get this fixed because its really annoying.

---

### Post by luisromangz on 2008-04-05
If you are using the Nvida drivers you should be able to use AIGLX. XGL is a hack, it may be faster, but it doesn't expose all the functionality of the real X server and is intended to be used only if your drivers/video card doesn't support AIGLX.

---

### Post by gareth80 on 2008-04-05
Are you using KDE? I don't know if this helps, but I had the same problem using KDE and Compiz with Mandriva, i.e. no shutdown option form inside a session. I found that changing the login manager from the KDE one to the Gnome one worked and full log off, hibernate and shut down options worked fine. This has no adverse effect on the system.

---

