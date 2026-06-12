---
title: "desktop, round guages, clear mac style taskbar?"
date: 2005-07-04
forum: Desktop Environments
---

### Post by Digitallysick on 2005-07-04
looking through some of the ubuntu desktops, ive seen some great stuff, like the round gauges for ram, cpu, lan, etc, is that karamba?? also seen the mac style clear task bar, what are these things and how do i get get them?

---

### Post by tread on 2005-07-04
gdesklets.
Install gdesklets through apt-get, don't install the gdesklets-data package though .. that is horribly out of date. Instead, go over to the gdesklets website (google it :)) and install the desklets you want. Installation is easy, you just start gdesklets, and it has a menu item to install new desklets.

Another option for a mac style toolbar is engage, there is a howto on e17 somewhere on the forum. Look into that. Have fun :)

---

### Post by udha on 2005-07-04
[QUOTE=tread]gdesklets.
Install gdesklets through apt-get, don't install the gdesklets-data package though .. that is horribly out of date. Instead, go over to the gdesklets website (google it :)) and install the desklets you want. Installation is easy, you just start gdesklets, and it has a menu item to install new desklets.

Another option for a mac style toolbar is engage, there is a howto on e17 somewhere on the forum. Look into that. Have fun :)[/QUOTE]
 when I try to install gdesklets it warns of over 10 packages that have to be removed, another 10 or more to upgrade, and a bunch more to add, why does it need to remove packages? they are:
dbus-1
dbus-glib-1
evolution
evolution-exchange
gaim
gedit
gnome-media
gnome-vlc
gnome-volume-manager
hal
libnautilus-burn1
nautilus-cd-burner
sound-juice
totem
totem-gstreamer
ubuntu-desktop
update-notifier
vlc
wxvlc


it's pretty clear that I need some of those, why does it mark them for removal?

---

### Post by tread on 2005-07-04
Huh? Thats weird, on my system installing gdesklets just adds 3 more packages. Have you been using any other repositories which might have messed up dependencies?

---

### Post by udha on 2005-07-12
[QUOTE=tread]Huh? Thats weird, on my system installing gdesklets just adds 3 more packages. Have you been using any other repositories which might have messed up dependencies?[/QUOTE]
 yeah don't worry about it, I did an apt-get upgrade instead of update, that with a borked sources.list file and 5.10 (ww) in development it totally messed everything up.

---

### Post by kiwiboyus on 2005-07-12
Does anyone know of somewhere else to download the actual desklets? 
Their site seems to be down since yesterday  :???:

---

