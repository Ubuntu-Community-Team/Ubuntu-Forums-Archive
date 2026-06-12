---
title: "Libreoffice looks ugly after KDE removal"
date: 2014-06-17
forum: Desktop Environments
---

### Post by tarun-hellknight on 2014-06-17
Hello.

I installed kubuntu-desktop last week just to try it out. Today, I removed the kubuntu-desktop environment and after the removal I entered following commands. I also tried deleting the **.config/Libreoffice** folder but all in vain.

> [B]sudo apt-get install ubuntu-desktop
sudo apt-get install libreoffice-gnome[/B]
This automatically installed **libreoffice-gtk **

But the problem is that Libreoffice is still using KDE/QT for display which looks out of place in Unity. Can you please tell me what am I doing wrong here?[IMG]https://dl.dropboxusercontent.com/u/34188735/Libreoffice.png[/IMG]

---

### Post by tarun-hellknight on 2014-06-17
EDIT: Never mind, I just solved it :). Turns out, all I had to do was to remove **gtk2-engines-oxygen** and restart LibreOffice. That's it.

---

