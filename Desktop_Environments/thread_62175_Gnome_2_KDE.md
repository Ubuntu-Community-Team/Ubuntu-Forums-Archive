---
title: "Gnome 2 KDE"
date: 2005-09-03
forum: Desktop Environments
---

### Post by benson on 2005-09-03
I have installed Ubuntu in my HD. Yet the current Desktop manager is gnome. Please tell how can i install kubuntu without removing ubuntu. I prefer the KDE desktop rather than gnome yet retaining the GDM login screen I have. Is that possible?
Thanks :)

---

### Post by benson on 2005-09-03
By the way I have the Kubuntu 5.04 install CD  and I don't have internet connection. :(

---

### Post by Havoc on 2005-09-03
Go to synaptic, go to "Edit----->Add CD ROM... on the top bar, and if everything goes well, click on KDE in synaptic and everything will install automatically.

I think.

---

### Post by benson on 2005-09-04
and  this wouldn't affect my GDM login, right? :)

---

### Post by Hobbsee on 2005-09-04
[QUOTE=benson]and  this wouldn't affect my GDM login, right? :)[/QUOTE]

I wouldnt think so, but you should be able to get the kdm off the cd after you get kubuntu, while it installs it gives you an option of which display manager you would like to use.

I dont think it would effect the login per se - as in, you would still use the same username and password you were using before...

---

### Post by Velox Letum on 2005-09-04
Or do a net install:

1) Add *deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main*
to */etc/apt/sources.list*
2) *apt-get update* 
3) *apt-get install kubuntu-desktop*
4) Once downloaded and installed, run *dpkg-reconfigure xserver-xorg* and select kdm as the default display manager

Removing GNOME:

5) Then if you so desire, remove GNOME, however what I did was remove the bulk of GNOME, but I left Synaptic and all the GNOME libraries needed to run FireFox and Synaptic. 
6) If you did the above, or you have other GTK apps, *apt-get install gtk2-engines-gtk-qt*, which is a library for KDE that makes GTK applications look alot better in KDE. It isn't perfect, and some menus get a bit confused, but it works. As for FireFox I decided to just download a Plastik theme from [http://www.kde-look.org](http://www.kde-look.org)  rather than rely on this library.

Notice, while this makes KDE the default login and display manager, you can still click Session and login to GNOME should you so choose to keep GNOME. Also you should still install gtk2-engines-gtk-qt as it makes alot of apps look much better.

---

### Post by benson on 2005-09-12
[QUOTE=Velox Letum] run *dpkg-reconfigure xserver-xorg* and select kdm as the default display manager[/QUOTE]

I tried this... but there's no kdm. but i can "startkde" in gnome console. how will i make kde my desktop manager and gnome my login screen? is that possible? what files do i need to edit? :)

---

