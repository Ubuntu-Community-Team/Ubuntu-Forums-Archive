---
title: "Usplash Fingerprint under Gutsy"
date: 2007-10-26
forum: Desktop Effects &amp; Customization
---

### Post by celticbhoy on 2007-10-26
Looking for help. Have the Fingerprint Usplash boot screen and was all working well until I upgraded to gutsy. I have tried to re-install, as I had to do after any Kernel update but it still wont display right. Does anyone know if this works under Gutsy ????

---

### Post by celticbhoy on 2007-11-04
bump

---

### Post by atagar on 2008-05-09
I just upgraded from Edgy to Hardy and encountered the same problem. It turns out that in addition to adding 'vga=791' to the kernel line in /etc/boot/menu.lst you also need to do the following:

Change the resolution in /etc/usplash.conf to 1024x768
sudo update-initramfs -u -k `uname -r`

---

### Post by celticbhoy on 2008-05-10
Funny enough when I upgraded from Gutsy to Hardy it started to work again!

---

