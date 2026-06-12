---
title: "Resource use of KDE apps running on XFCE"
date: 2020-01-14
forum: Desktop Environments
---

### Post by nickstone8-v on 2020-01-14
I have a very old laptop and therefore use the lightweight XFCE desktop via XUbuntu. I have found that this runs faster than KDE which is known to be heavy on resources. However, there are some KDE applications that I would like to install, such as "Okular". Unfortunately, installing these also means installing a long list of dependencies that include KDE library files kinit and kio (and many others). From my point of view, this is not a problem if these library files simply sit on my hard disc and do nothing (until I start Okular). However, if installing them implies any kind of additional overhead whatsoever during normal operation then I don't want them and will go without Okular. So my question is "Will installing Okular (and therefore the many kde library files) slow down my XUbuntu system?". I would be very grateful to anyone who knows the definitive answer to this. (Alternatively, please point me to the best place to ask this question). Many thanks.

---

### Post by CatKiller on 2020-01-14
You are correct the the files sitting on your hard drive will only take up hard drive space. The libraries provided by those packages, but only the ones that are needed to run Okular (or whichever application), will be loaded into RAM when you run Okular and then unloaded (or cached) when you close Okular. They won't otherwise cause any slowdown.

FWIW, when Xfce was using the old GTK2 libraries and KDE was struggling to transition to KDE4 Xubuntu *was* definitively lighter than Kubuntu. Now that Xfce is using the heavier GTK3 and KDE has moved to Plasma 5 they are roughly equivalent in how heavy they are, with Xubuntu using more resources than Kubuntu sometimes. Gnome is still a fatty, though.

---

### Post by Artim on 2020-01-14
It's surprising to find that the newest KDE is much lighter than before, truly rivaling Xfce when it comes to conserving resources!  It won't remain a well-kept secret for much longer, though.  Even the lead developer of [Linux Lite]("http://linuxliteos.com") has been experimenting with KDE/Plasma!

---

### Post by SeijiSensei on 2020-01-15
I'm running the development version of 20.04. It's only using 1.5 GB of my system's memory with Brave Browser and Thunderbird along with a couple of other applications like Dolphin all running.

---

### Post by speartip on 2020-01-15
I'd 2nd the observations regarding KDE. On my 18.04 kubuntu install, the 1st thing I did was uninstall everything akonadi & mysql, & install Thunderbird & Lightning. At boot I'm using 400-500mb Memory, & the system flies on my 13 year old HP Desktop with an i3 processor & integrated HD2000 series Graphics.

---

