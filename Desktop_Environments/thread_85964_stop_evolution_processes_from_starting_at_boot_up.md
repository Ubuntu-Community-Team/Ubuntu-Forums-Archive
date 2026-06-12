---
title: "stop evolution processes from starting at boot up"
date: 2005-11-03
forum: Desktop Environments
---

### Post by RyanGT on 2005-11-03
I don't use evolution for anything (I use gmail's web interface and keep my calendar in my head).  But I noticed in my system monitor that there are 3 evolution processes that take up a substantial ammount of memory.  They are
evolution-data-server-1.4
evolution-alarm-notify
evolution-exchange-storage

Are there needed by some other system processes?  If not, can I stop them from starting automatically at boot up?  I installed the Boot-Up Manager, but it did not list these processes there for me to deselect.

Thanks,

Ryan

---

### Post by RAOF on 2005-11-04
Evolution-data-server is definately needed by Gnome - it has become/is becomming a bit of an all-purpose backend for a bunch of stuff, including the gnome panels.

I think the other two are unnecessary.  I'm not certain how you could stop them from starting, but as you don't use it you could uninstall evolution using synaptic.  This shouldn't break anything, except (possibly) beagle - it tries to index the evolution mail/contacts/etc by default.

---

### Post by dcstar on 2005-11-04
[QUOTE=RAOF]Evolution-data-server is definitely needed by Gnome - it has become/is becoming a bit of an all-purpose backend for a bunch of stuff, including the gnome panels.

I think the other two are unnecessary.  I'm not certain how you could stop them from starting, but as you don't use it you could uninstall evolution using synaptic.  This shouldn't break anything, except (possibly) beagle - it tries to index the evolution mail/contacts/etc by default.[/QUOTE]
Notify is just that - when an e-mail arrives in Evolution it kicks off the "mail arrived" sound you have specified - you can probably remove it no problems at all.

Exchange is for allowing Evolution access to a Microsoft Exchange server - get rid of it (I have, with no problems whatsoever).

---

### Post by RyanGT on 2005-11-04
When I try to remove evolution-exchange through the Synaptics package manager it says that it can't remove it without also removing the ubuntu-desktop.  That sounds bad, so I have not tried it.  (The same goes for all evolution related packages).

Ryan

---

### Post by Ampersand on 2005-11-04
ubuntu-desktop is just a meta-package. It doesn't affect anything, it just depends on everything that's installed by default, so it's safe to uninstall.

---

### Post by RyanGT on 2005-11-04
Thanks to all.  I first uninstalled evolution-exchange and when that went well I uninstalled evolution itself (I left the data sever).  Everything seems to be fine and I am using less memory.

Thanks,

Ryan

---

### Post by scubajeff on 2005-11-04
I use sylpheed claws for mail. So i had removed the evolution packages. The only one left is the "evolution-data-server-1.4", since it's required by gnome.

---

