---
title: "firefox"
date: 2009-05-20
forum: General Help
---

### Post by ultratek on 2009-05-20
i type firefox in terminal and i get this: 
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
LoadPlugin: failed to initialize shared library /usr/lib/swfdec-mozilla/libswfdecmozilla.so [/usr/lib/swfdec-mozilla/libswfdecmozilla.so: wrong ELF class: ELFCLASS64]

it starts but no page will load.
problems all started when i did sudo firefox in terminal and monday i erased
/opt/firefox with (rm -rf)
but i believe i got it back that dir

can someone help me? thx

---

### Post by TheExplorer on 2009-05-20
First things first :) How did you install Firefox if you had to remove it from /opt?
You may install it from Synaptic. It's there and you don't have to download it from Mozilla site.
Well, if you did it manually from their site: then remove it from /opt if it's still there (you have to be root to do that), then remove /.mozilla folder in your home dir (you may have to be also root since you started the browser with root privilege). Then install Firefox via Synaptic. It should work.

---

### Post by ultratek on 2009-05-20
i tried removing those directories and then started firefox via terminal after installing through add remove programs and it says in terminal firefox is not installed it can be installed by sudo apt-get ...etc...
then it says it is already newest cannot update?

i had orignally installed from live cd 64bit jaunty ubuntu
i formatted my old 32 bit

but when i ran that sudo firefox in terminal...........man

---

### Post by TheExplorer on 2009-05-21
What do you mean 'you formatted your old 32 bit' ? O_O
Did you remove /.mozilla dir in your home?

---

### Post by ultratek on 2009-05-21
yes i removed the .mozilla... thanks for your help... its seems what you said got me to where i could get everything working...so all is good
=)

---

### Post by The Ginger Kid on 2009-05-21
go to terminal and type:

sudo su
"Your Password"
apt-get autoremove firefox
apt-get install firefox
y
exit :biggrin:

---

