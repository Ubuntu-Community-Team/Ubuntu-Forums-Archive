---
title: "xfce4 + printing = howto?"
date: 2005-06-22
forum: Desktop Environments
---

### Post by buellman on 2005-06-22
hi!

yesterday i did a server-install to get a minimal system and then installed xfce4. now i dont see how i could get my hp laserjet 4 with jetdirect-card to work.
as far as i understand xfce itself doesnt provide any program to setup a printer. so i need to do it via cups what didnt work because the webinterface is "closed" for adminitration tasks.
so i installed the gnome-cups-manager. ok... i've tried to setup my printer and there are some questions left:
1) if i setup up my printer from gnome i have a big choice of drivers to install. what package do i have to install to get all this drivers?
2) i installed my printer with one of the few drivers (one for a laserjet 4) that where present but im not able to print. i tried to print a testpage but nothing happens. maybe there are missing some other packages to get it to work?
3) is there a howto how to get my printer working? if i install gnome and setup my printer it just works great.

dont know what to do to get this printer working. ok... i could install gnome and than configure my printer but i would like to have a pretty clean and simple system.

ok... thanks for any idea.
greets. buellman

---

### Post by intangible on 2005-06-22
What model printer do you have?

You'll need to install that package for the printer drivers, the the gnome-cups-manager should work okay.

---

### Post by buellman on 2005-06-22
[QUOTE=intangible]What model printer do you have?

You'll need to install that package for the printer drivers, the the gnome-cups-manager should work okay.[/QUOTE]

wow... thanks :-) cupsomatic-ppd did the job :-)

many thanks again.
greets. buellman

---

