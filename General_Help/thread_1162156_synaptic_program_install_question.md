---
title: "synaptic program install question"
date: 2009-05-17
forum: General Help
---

### Post by jesse c on 2009-05-17
Why, when i enable some applications in synaptic (this particular time its Wifi Radar) and then restart and try to launch from 'application' menu,do i get a pop up window that tells me it cant launch the app cause no such file exists or something like those words? It must exist somewhere cause it got into the applications/internet menu list

---

### Post by gettinoriginal on 2009-05-18
What happens when you try to run it from terminal ??

---

### Post by jesse c on 2009-05-18
what would be the command to run wifi radar

---

### Post by leifjonny on 2009-05-18
"wifi-radar", but you must run it as root, so it is "sudo wifi-radar".
If you want to find out which files a package has installed using synaptic, search for the installed package right-click it and choose properties->installed files.

As for wifi-radar the executable is located at /usr/sbin/wifi-radar. You can edit the launcher to point to the correct file manually at system->pref->main menu. Mine says "su-to-root -X -c /usr/sbin/wifi-radar".

---

