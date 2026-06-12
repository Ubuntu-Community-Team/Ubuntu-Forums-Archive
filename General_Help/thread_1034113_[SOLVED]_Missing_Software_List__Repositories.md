---
title: "[SOLVED] Missing Software List / Repositories"
date: 2009-01-08
forum: General Help
---

### Post by subzero.amir on 2009-01-08
I installed adobeAIR and the uninstalled it. Right after that, when I go to Add/remove... EVERYTHING is missing...
Why is that happening?


What I have done to try to fix the problem:
1. Change Repositories sources from Synaptic
2. Reload repositories
3. countless reboot
4. Did this sudo apt-get update -o Acquire::http::No-Cache=True
5. Did this sudo apt-get update

Please help. Thks.

---

### Post by gettinoriginal on 2009-01-08
Check synaptic and make sure that "gnome-app-install" is installed, it may have been uninstalled when you did your changes.  Even if it shows that it is installed, check it for reinstall and click apply.

---

### Post by subzero.amir on 2009-01-08
YES.............. YOU DA MAN........
Quick reply and right to the point....
This is one of the reason I switch completely from Windows 2 months ago...
Thks man...

---

### Post by gettinoriginal on 2009-01-08
Glad to help, and welcome to Ubuntu :popcorn:

---

