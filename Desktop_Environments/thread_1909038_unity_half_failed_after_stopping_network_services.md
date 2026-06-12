---
title: "unity half failed after stopping network services"
date: 2012-01-14
forum: Desktop Environments
---

### Post by jeliocranch on 2012-01-14
I've got a server system where I installed ubuntu-desktop.  
 

I stopped networking with:
sudo /etc/init.d/networking stop
and my desktop freaked out:

the unity launcher lost about half the icons (though the links are still active), the gnome 2 panel showed up and the color-scheme half changed to that of the gnome DE, that is some looks like the old ubuntu desktop, and some looks new.

I've checked through the networking script, but don't see any dependencies or parental relations with the DE.  Any thoughts?

Rebooting brings back unity, stopping networking kills it again, but starting networking does not bring it back.

---

### Post by jeliocranch on 2012-01-16
no one else with this issue?

Its pretty annoying to have to reboot or deal.  If anyone knows of the connection between networking and the desktop, It'd be great to hear.

I know networking starts before the desktop, but that's the extent of it.

---

