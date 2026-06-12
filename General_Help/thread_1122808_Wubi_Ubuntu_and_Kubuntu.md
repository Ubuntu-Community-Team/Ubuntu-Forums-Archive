---
title: "Wubi: Ubuntu and Kubuntu"
date: 2009-04-11
forum: General Help
---

### Post by xr4v3nx on 2009-04-11
Hello guys!

Details:
• My host OS is Windows XP
• I installed Wubi and chose Ubuntu to install
• What happens if I run Wubi again to install Kubuntu?
• Is it possible in the first place? To have 2 (virtual) operating systems using Wubi?
• If not, how can I use Wubi to install another virtual OS?

Thanks guys!:popcorn:

---

### Post by Tipped OuT on 2009-04-11
If I'm not mistaken, if you try to do that, it will unistall Ubuntu first then install Kubuntu. So no, it's not possible to have both as a triple boot with Wubi, unless you manually create 2 more partitions and install Ubuntu on one and Kubuntu on the other.

---

### Post by abn91c on 2009-04-11
not possible, what you need to do is ```
sudo apt-get install kubuntu-desktop
``` then select it under sessions in the login screen

---

### Post by Tipped OuT on 2009-04-11
The above comment also works. But if you wanted 2 separate OS's then you need to create 2 partitions to install them on. The above comment allows you to install KDE desktop environment in Ubuntu as a session option. Kubuntu is the same exact thing as Ubuntu, it just uses the KDE desktop environment as default.

---

### Post by xr4v3nx on 2009-04-12
is that it guys?oh..i just want to try out kubuntu..thanks for the replies guys..i appreciate it..

---

