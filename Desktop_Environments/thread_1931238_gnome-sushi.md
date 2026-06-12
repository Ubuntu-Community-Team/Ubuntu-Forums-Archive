---
title: "gnome-sushi"
date: 2012-02-25
forum: Desktop Environments
---

### Post by bn3232 on 2012-02-25
how can I install gnome-sushi (nautilus preview tool) on ubuntu 11.04 (natty)? I have gnome-shell 3.3.2 installed.
help me plz.

---

### Post by Frogs Hair on 2012-02-25
The link is for is for 11.10 and the application works with nautilus 3.xx . Since 11.04 uses Gnome 2 I'm not sure how you installed the Gnome Shell which runs on top of Gnome 3 available with 11.10 .  

[http://www.webupd8.org/2011/10/using-gloobus-preview-with-nautilus-32.html](http://www.webupd8.org/2011/10/using-gloobus-preview-with-nautilus-32.html)

---

### Post by bn3232 on 2012-02-28
I have installed gnome shell 3.3.2 on my ubuntu 11.04, but gnome-sushi does not exist in my repositories.

---

### Post by Krytarik on 2012-02-28
> **bn3232 said:**
> I have installed gnome shell 3.3.2 on my ubuntu 11.04, but gnome-sushi does not exist in my repositories.
Yeah, there are no packages for Gnome Sushi in the [Gnome-Shell Testing PPA]("https://launchpad.net/%7Ericotz/+archive/testing"), and it seems like the only way you could try is downloading the source and compiling it manually:

[LIST]
[*]Upstream GIT: [http://git.gnome.org/browse/sushi/](http://git.gnome.org/browse/sushi/)
[/LIST]

[LIST]
[*]Launchpad Bazaar: [https://code.launchpad.net/~jbicha/gnome-sushi/sushi]("https://code.launchpad.net/%7Ejbicha/gnome-sushi/sushi")
[/LIST]
Good luck! :P

---

### Post by jbicha on 2012-03-04
GNOME Shell is only supported on Ubuntu 11.10 and higher. As a side benefit, gnome-sushi, gnome-shell, etc. are in the normal Ubuntu 11.10 repositories so they're easy to install.

---

