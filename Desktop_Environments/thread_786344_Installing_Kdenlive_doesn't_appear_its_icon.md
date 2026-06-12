---
title: "Installing Kdenlive doesn't appear its icon"
date: 2008-05-08
forum: Desktop Environments
---

### Post by narcisgarcia on 2008-05-08
I've tried to install Kdenlive in Ubuntu GNU/Linux 8.04 (Hardy Heron) in 2 computers: one with the i386 version, and the other with the AMD64 version.

In both cases the installation process doesn't add a new "Kdenlive" element in the Applications menu. Kdenlive is installed, because I can run it pressing [Alt]+[F2] and writing "kdenlive" command to start the application, but then I need to edit manually the Applications menu to add a launch icon.

---

### Post by loell on 2008-05-09
yeah, thats probably because kdenlive is considered a native kde application and only in a KDE menu enviroment.

---

### Post by narcisgarcia on 2008-05-10
It's okay, but K3b and K9Copy are KDE applications too, and have solved this question.

---

### Post by loell on 2008-05-10
i see, maybe kdenlive is lacking .desktop file if thats the case. a bug most probably.

you can also install the **menu** package, it is suppose to generate menu on programs for all known UI application. but nothing beats editing the menu like you already did. :)

---

