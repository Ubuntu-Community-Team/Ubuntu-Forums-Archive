---
title: "Full Debian repositories?"
date: 2005-04-26
forum: Desktop Environments
---

### Post by GTKpower on 2005-04-26
How do I gain access to the full Debian repositories ?

Or am I already on them with the Hoary (or Breezy repos)?

---

### Post by bored2k on 2005-04-26
[QUOTE=GTKpower]How do I gain access to the full Debian repositories ?

Or am I already on them with the Hoary (or Breezy repos)?[/QUOTE]
 You can acquire them through a simple google search . But for better stability, you are better off with Ubuntu's universe/multiverse/universe/backports repositories. These are some for the stable branch:

*Debian Mirror List
/etc/apt/sources.list
deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) stable main contrib non-free
deb [http://non-us.debian.org/debian-non-US](http://non-us.debian.org/debian-non-US) stable/non-US main contrib non-free
deb [http://security.debian.org/](http://security.debian.org/) woody/updates main contrib non-free
deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) woody main contrib non-free
deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) testing main contrib non-free
deb [http://non-us.debian.org/debian-non-US](http://non-us.debian.org/debian-non-US) testing/non-US main contrib non-free
deb [http://mirrors.kernel.org/debian](http://mirrors.kernel.org/debian) stable main contrib non-free

---

### Post by az on 2005-04-26
[QUOTE=GTKpower]How do I gain access to the full Debian repositories ?

Or am I already on them with the Hoary (or Breezy repos)?[/QUOTE]

There is very little need to.  Other than the danger of borking your system because of package inconsistencies, most of debian is in Universe.

If you really really need a debian package, install debian, or compile it from the source debs on Ubuntu.
sudo apt-get build-dep ...
sudo apt-get source ...

---

### Post by GTKpower on 2005-04-26
Thanks for the help!

I think I'll stick with the non-borking, universe route.

---

### Post by bored2k on 2005-04-26
[QUOTE=GTKpower]Thanks for the help!

I think I'll stick with the non-borking, universe route.[/QUOTE]
 You can always add multiverse and backport repositories if you want/need more packages. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) [you can add the backports with the following link: [http://backports.ubuntuforums.org/]](http://backports.ubuntuforums.org/])

---

