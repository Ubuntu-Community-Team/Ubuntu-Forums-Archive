---
title: "Restoring splash screen"
date: 2008-09-28
forum: Desktop Environments
---

### Post by CharmCityCrab on 2008-09-28
I installed a KDE desktop to use occasionally, and it has replaced my existing "Ubuntu" splash screen at boot with a "Kubuntu" screen, with that same bar at the bottom indicating it was working.  The same is true when I tell it to shut down.  Since I usually use gnome, I prefer the old Ubuntu splash screen.  Anyone know how to restore the splash screen I want without removing KDE?

---

### Post by koba101 on 2008-09-28
install startup manager and startup-tasks, you can find the right configuration there i guess if not try removing the splash screen and then putting back again

---

### Post by CharmCityCrab on 2008-09-29
> **koba101 said:**
> install startup manager and startup-tasks, you can find the right configuration there

Thanks! :)  There is an option in the startup manager gui you recommended to change what I was looking to change.

---

### Post by cptnfool on 2008-12-10
Whats say I attempted to change it using terminal by changing the soft link at /etc/alternatives/usplash.so 
I was hoping that if i pointed it at another theme, it would work, but now, linking it to the themes from /usr/lib/usplash, where the old and new ones are, seems to leave me with a broken softlink.  
i tried using startup manager to fix this, but when it finds the broken softlink during setup, it exits.  
Could anyone tell me how i could solve this problem and get my ubuntu logo back at boot?  Thanks in advance

---

