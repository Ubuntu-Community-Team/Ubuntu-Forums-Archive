---
title: "Minimal Install"
date: 2009-01-24
forum: General Help
---

### Post by IceReaver75 on 2009-01-24
How would I go about installing just a base gnome system with using the minimal install disk.  I want to install a base system and just install what I want.  Thank you for your help.

---

### Post by gjoellee on 2009-01-24
> **IceReaver75 said:**
> How would I go about installing just a base gnome system with using the minimal install disk.  I want to install a base system and just install what I want.  Thank you for your help.

So you want just GNOME and not Ubuntu right? Then download the minimal cd ISO and burn it to a CD or DVD. The boot with the CD inside. When it comes to "Boot:" hit the enter button. When yo reach the menu click on "Commandline Install" or you wil install the the whole Ubuntu.

Then go trhough the text based installer, and when it is installed and you have started you should drop into command shell. Login with your username and password. Then to install gnome use this command: ```
sudo apt-get install gnome
``` when finshed reboot and you should go straight to the login screen and you should have the BASE GNOME system.

NOTE: Ubuntu has modified some packages and therefore you will have the Ubuntu theme on login screen, and no selected default theme in GNOME, but it is just to change it.

---

