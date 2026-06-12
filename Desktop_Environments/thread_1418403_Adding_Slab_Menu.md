---
title: "Adding Slab Menu"
date: 2010-02-28
forum: Desktop Environments
---

### Post by craig10x on 2010-02-28
Hi:  I read some blogs that you can an add "a mint like slab menu" or actually more specifically a slab menu that is similar to what OpenSuse uses on their gnome (except designed to work in Ubuntu)...
     
They mentioned something about entering: apt-get-install-gnome main menu in the terminal and it would get added on to the list you see when you "right click" on a panel..and then you can add it on....Anyone use this?  Is  that how it is done?
I didn't see the install option for it in the package manager (i am on 9.10)....
    
Also, when it is installed...do you have access to the normally turned off Ubuntu Control Panel?  Or do you have to enable it first before installing the Slab Menu?

---

### Post by celica6 on 2010-03-14
Yes, you can do
```
sudo apt-get install gnome-main-menu
```
to get this menu. It is also in synaptic if you search for gnome-main-menu. You'll have to logout after install, login, right click on your control panel, and it should be there as Main Menu with a computer icon (not the one with the Ubuntu icon).

However, I've found this menu to be pretty cumbersome, and the search bar doesn't do automatic filtering. I've found that the linux mint menu works pretty well on Ubuntu, and is much nicer than normal Slab. You can download:
[HTML]http://packages.linuxmint.com/pool/main/m/mint-translations/mint-translations_2010.02.02_all.deb[/HTML]
[HTML]http://packages.linuxmint.com/pool/main/m/mint-common/mint-common_1.0.5_all.deb[/HTML]
[HTML]http://packages.linuxmint.com/pool/main/m/mintmenu/mintmenu_4.9.4_all.deb[/HTML]

and install them in that order (all other dependencies should be in the normal Ubuntu repositories). Right click the panel, Add to Panel, and mintMenu should be there. You can then right click the menu icon once it's on your panel, select preferences, and change the name, icon, and various other things. The keyboard shortcut for it is <Ctrl>+<Windows key>.

---

