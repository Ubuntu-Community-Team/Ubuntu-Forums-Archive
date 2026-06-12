---
title: "Ubuntu and XFCE4 (Solved)"
date: 2005-10-30
forum: Desktop Environments
---

### Post by Terrik on 2005-10-30
Hi all,

I just installed the xubuntu desktop, and XFCE is great, but I have a problem. Synaptic does not have an icon in any of the menus. If I try to add a Synaptic icon manually, it does not work since it needs a password. In Gnome a GUI box would come up and ask for a password when I launched Synaptic, but with XFCE the only way Synaptic works is with 'sudo synaptic', then the password, in the terminal. Can anyone help me add a Synaptic icon just like it works in Gnome? 

Secondly, it would be nice to have an update notifier in my taskbar, like in ubuntu Gnome...is there any way to do that? If not, does apt-get upgrade serve the same function? Thanks.

---

### Post by psychicdragon on 2005-10-30
Hi,

You need to run it as **gksudo synaptic**

---

### Post by Terrik on 2005-10-30
Thanks, worked well.

---

