---
title: "Gnome doesnt start after removing Kubuntu"
date: 2008-03-02
forum: Desktop Environments
---

### Post by h3rt3q on 2008-03-02
i did a kubuntu installation earlier. then i find out gnome is much more better (for me).
what i did was removing kde-core and all the kde components. then i installed ubuntu-desktop.

the problem is, my gdm does not start at boot. instead i ended up booting in "no display manager mode" (sorry, i dont know what its called, the one that ask you to login just like when you press ctrl + alt + f1). i have to "/etc/init.d/gdm start" to make it start. i did some searching earlier, but ended up nothing.

i also edited /etc/X11/default-display-manager,
do a "dpkg-reconfigure gdm", and also
log out from gnome -> select session -> gnome. (on a manual gnome start)

im not sure whats wrong. maybe the rc scripts?
some help will be really appreciated.

Regards,
Adam

---

