---
title: "/etc/cups location?"
date: 2009-06-22
forum: General Help
---

### Post by Camilia on 2009-06-22
I found that there is an option to change default of cups at /etc/cups. Where do I find this? I have looked in Home files and hidden files.

Object is to over ride command for settings to revert back to colored cartridge. Want to set default to black cartridge. For I have bought 2 black cartridges.

---

### Post by jocko on 2009-06-22
> **Camilia said:**
> I found that there is an option to change default of cups at /etc/cups. Where do I find this? I have looked in Home files and hidden files.

Object is to over ride command for settings to revert back to colored cartridge. Want to set default to black cartridge. For I have bought 2 black cartridges.

You'll find a folder named "cups/" in the folder "/etc/" (which is in the root of the file system)... So the path to the folder is /etc/cups.
If you want to browse there, you open up a nautilus window, choose "Filesystem", and then "etc" and then "cups". Or type "/etc/cups" in the address bar of a nautilus window.

---

### Post by khelben1979 on 2009-06-22
Have you ever looked in the [CUPS wiki document]("http://en.wikipedia.org/wiki/Common_Unix_Printing_System") for information? (I couldn't find anything in it which answered your question, but maybe you will?)

---

### Post by Camilia on 2009-06-22
> **jocko said:**
> You'll find a folder named "cups/" in the folder "/etc/" (which is in the root of the file system)... So the path to the folder is /etc/cups.
If you want to browse there, you open up a nautilus window, choose "Filesystem", and then "etc" and then "cups". Or type "/etc/cups" in the address bar of a nautilus window.

I don't know where to start. Looked in home folder. It is the only folder I see in Places. Open up a nautilus window, where? CUPs folder, where? File system, where?

---

### Post by Shazaam on 2009-06-22
Places>Computer>Filesystem>Etc>cups.
Try this-
Enter this in the addressbar of Firefox...

[http://127.0.0.1:631/](http://127.0.0.1:631/)

It should get you to the cups admin page.

---

### Post by Camilia on 2009-06-22
> **Shazaam said:**
> Places>Computer>Filesystem>Etc>cups.
Try this-
Enter this in the addressbar of Firefox...

[http://127.0.0.1:631/](http://127.0.0.1:631/)

It should get you to the cups admin page.

Found the cups. Now need to figure where to change default cartridge setting.

I have tried in the cups admin page to change the cartridge setting but it always reverts back to color cartridge, which is very low.

---

