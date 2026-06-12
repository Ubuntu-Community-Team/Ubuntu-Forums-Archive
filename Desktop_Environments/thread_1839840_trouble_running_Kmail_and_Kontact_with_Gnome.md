---
title: "trouble running Kmail and Kontact with Gnome"
date: 2011-09-06
forum: Desktop Environments
---

### Post by SaintDanBert on 2011-09-06
I installed Kmail and Kontact onto my Gnome based Ubuntu Lucid laptop.
(Why I did that is not an issue here.) I used Synaptic and simply applied the packages. Synaptic grabbed a truck load of dependencies.

When I run these apps from an X11 terminal window, I get all sorts of complaint log output about "akonadi" and "nepomuk" -- including report of a seg fault in nepomuk.  I'm surprised at these troubles because apps like K3b and Kate and KNotes work just fine.

Also, /var/log/messages reports all sorts of troubles connecting with MySQL while I'm using Kmail or Kontact.

Before I capture log contents and format for posting here and all that jazz, I wonder if there is some general set of steps that I need to take so that I can use these KDE apps with my Gnome-desktop workstation?

Can anyone help?
~~~ 0;-/ Dan

---

### Post by 2F4U on 2011-09-06
I guess the problem is that the PIM applications are nowadays highly intergrated within the KDE backend (Akonadi, Nepomuk) and it probably be difficult to get things running without a KDE installation.

---

### Post by SaintDanBert on 2011-09-08
I expected that package dependencies would take care of fetching the supporting parts.  Does this say that the dependencies are broken for those packages?

Short of a full install of KDE or "kubuntu-desktop" can someone suggest
packages to install or re-install to fill in whatever is missing?

Thanks,
~~~ 0;-Dan

---

