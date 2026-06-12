---
title: "Thunderbird crash"
date: 2014-05-01
forum: Desktop Environments
---

### Post by jacksmith on 2014-05-01
Hi, 

I can't launch thunderbird anymore.
When I start it, it crash immediately.

When starting in command line, I get the following message :

 > thunderbird -safe-mode
Unable to create socket
Unable to create TCP socket
/usr/lib/gio/modules/libgiogconf.so: Ne peut ouvrir le fichier d'objet partagé: Trop de fichiers ouverts

(thunderbird:20484): GLib-GObject-WARNING **: Fatal error - Could not reload previously loaded plugin '(unknown)'


Does somebody have an idea ?

Thanks in advance.

---

### Post by ajgreeny on 2014-05-01
Is this following today's update of TB (it was updated on 12.04)?  If so, see what happens if you rename the hidden .thunderbird in your home as .thunderbirdbak and restart TB.  If it starts OK there is something in your personal configuration that is crashing TB.

Any add-ons enabled?

---

