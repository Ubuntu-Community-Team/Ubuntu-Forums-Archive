---
title: "Changing default applications for i3 session"
date: 2016-09-01
forum: Desktop Environments
---

### Post by l3th4lbr2 on 2016-09-01
Hi,

I installed Lubuntu but want to use i3wm without breaking LXDE. The problem is that stuff like the file manager, desktop background, network, power management etc and also default applications for music, web, video, PDF etc are still LXDE's defaults when i use i3wm and I don't know how to change these properly without changing those for LXDE. Can somebody explain how to do this, where to find the config files etc? Also, I use a Lenovo laptop with Nvidia optimus, I don't want to break the bumblebee configuration either.

Thank you!

---

### Post by sudodus on 2016-09-01
Welcome to the Ubuntu Forums :-)

I think it is best to install another operating system alongside Lubuntu. Start from the Ubuntu **mini.iso** in BIOS or **Ubuntu Server amd64** in UEFI mode, and install the program packages you need, for example xinit and xterm plus i3wm. Then you reboot (and it should give you a working graphical desktop, at least if i3wm is as complete as for example fluxbox or openbox). After that you can add the program packages you want.

The advantage is that you avoid a messy system with two desktop environments, but it means that you have to reinstall the graphics drivers etc.

---

### Post by l3th4lbr2 on 2016-09-01
Yeah that sounds like an idea. Could two installations share a same (partial) home directory (mainly for documents and videogames)?

---

### Post by sudodus on 2016-09-01
Yes, but again, it will be messy, so I would not recommend it. Instead I suggest that you create a *separate **data** partition*, where you store your private data: documents, music, pictures, video. That way your home directories will be rather small.

---

### Post by vasa1 on 2016-09-01
Nice question!

Looks like OP wants to have a customized desktop environment. In which case, [https://www.linuxvoice.com/create-your-own-desktop-environment/](https://www.linuxvoice.com/create-your-own-desktop-environment/) may be an interesting read.

All the best and let us know how things go in any case.

---

### Post by oldos2er on 2016-09-03
i3 is a window manager; it has no default applications in the sense that a DE does. Use dmenu ($mod-d) to launch applications, or create keyboard shortcuts for apps. i3's config file is ~/.i3/config.

---

