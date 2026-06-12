---
title: "How to delete old Hardy Heron 8.04"
date: 2008-12-04
forum: General Help
---

### Post by Skottie88 on 2008-12-04
Hello committee, I know a little about Ubuntu but this I need to know.  I stalled ubunta 8.04 and wanted to uninstall Python using synaptic manager. Howerver for some reason it uninstalled my complete gnome desktop!!! Dont know why it did this cuz I only selected python to uninstall.  So I no longer have a desktop now but only a black screen with the prompt.  Then I tried to install 7.04 on top of that and thought it would overwrite the 8.04  stuff but it didnt. I keep getting the prompt from the previous installation. How do I uninstall that and start with a fresh install of 7.04. Any help would be appreciated.  Im sure I can do this with my ubuntu CD but dont know which key to press to get to a system setup.

---

### Post by mkvnmtr on 2008-12-04
Sounds like you installed 7.04 into free space. I think you need to go to partition manager and take a screen shot of your drive. Post it up and maybe someone can figure out where your operating systems are installed.

---

### Post by 3rdalbum on 2008-12-04
When you go to install the operating system from the Live CD, tell it to "Use entire disk". This will format the hard disk, erasing all traces of the old copy of Ubuntu.

Additionally, Python is a very necessary component of Gnome and Ubuntu, so deleting Python will also delete your Python-based programs, including lots of Gnome and almost all Ubuntu-specific apps. Synaptic Package Manager would have warned you that it was deleting a whole bunch of other packages, and listed exactly what ones it was deleting.

---

### Post by aggiemarine07 on 2008-12-04
alternatively whenever you uninstalled everything all you would needed to do was type the command "sudo apt-get install ubuntu-desktop" and it would re-installed most, if not all, of the stuff you just removed.

---

