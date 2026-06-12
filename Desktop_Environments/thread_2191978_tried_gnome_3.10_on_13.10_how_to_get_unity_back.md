---
title: "tried gnome 3.10 on 13.10 how to get unity back?"
date: 2013-12-05
forum: Desktop Environments
---

### Post by e3e9c236 on 2013-12-05
hello internet,

i'm running 13.10 and installed gnome 3.10 with the gnome3-next ppa from team gnome, as explained here: [http://www.webupd8.org/2013/09/how-to-install-gnome-310-in-ubuntu-1310.html](http://www.webupd8.org/2013/09/how-to-install-gnome-310-in-ubuntu-1310.html)

i did the ppa purge and now sort of have unity back, but still have the gnome boot screen, the font, the close button for windows on the right side. plus if i minimize an application xorg and the application have around 100% cpu usage.
screenshot: 
[[IMG]http://i.imgur.com/VZzvjp6l.png[/IMG]]("http://imgur.com/VZzvjp6")

i also tried sudo apt-get install unity and sudo apt-get dist-upgrade, but it's already up to date.

i really would appreciate any guidance on how to get unity back. i have my home folder backed up with deja dup, but reinstalling probably means to reconfigure and i'd rather avoid that.

---

### Post by frank18 on 2013-12-05
Did you Log out? unless you deleted UNITY,all you have to do is log out and change the desktop.
otherwise i would reinstall the hole thing. if you have any files that you want to save just save them before reintalling Ubuntu,
that's what i do every time i encounter a problem that will take more time to solve that the full reinstallation.

---

### Post by oldrocker99 on 2013-12-05
GNOME did install gdm, the Gnome display manager, which is the screen you log into.

Do this:

sudo dpkg-reconfigure gdm

You'll be offered a choice of display managers the default Ubuntu one is called ldm.

---

### Post by e3e9c236 on 2013-12-06
> **frank18 said:**
> Did you Log out? unless you deleted UNITY,all you have to do is log out and change the desktop.
otherwise i would reinstall the hole thing. if you have any files that you want to save just save them before reintalling Ubuntu,
that's what i do every time i encounter a problem that will take more time to solve that the full reinstallation.

of course, i rebooted several times, that's why i've seen the boot screen.

> **oldrocker99 said:**
> GNOME did install gdm, the Gnome display manager, which is the screen you log into.

Do this:

sudo dpkg-reconfigure gdm

You'll be offered a choice of display managers the default Ubuntu one is called ldm.

i have already uninstalled gdm and lightdm is active.

---

### Post by Frogs Hair on 2013-12-06
I tried the same ppa on a 13.04 installation and after the ppa purge Unity wasn't running properly. When checking in the synaptic package manager I found the purge had not removed all the upgraded packages. There was mix of packages from different versions of gnome installed on the system. Reinstalling the Ubuntu desktop didn't change anything and using the autoremove command didn't remove the packages.Reinstalling the operating system was quicker than trying to track down and manually change all the affected packages.

---

### Post by Yougo on 2013-12-08
@e3e9c236, If you haven't gone for a complete reinstall yet,  you could run the following command:

```
sudo apt-get install ubuntu-desktop ubuntu-settings
```

this will install all components that make ubuntu work (that may be missing), and set all the settings right, such as buttons on the left.

to make sure you could run again with
```
sudo apt-get install --reinstall ubuntu-desktop ubuntu-settings
```

that said, i'm kind of having the same problem (which sadly won't go away with above commands). i managed to purge most of the gnome stuff, save for some bits:


my global menu isn't working right. de menus show, and are populated with all the menu-items belonging to the app, but all the menuitems are greyed out. HUD works fine though

if i uninstall appmenu, the menus show in the app's window, and work fine. 

so, the in-app menus work, dbus works because HUD is working, but appmenu is only halfway there :(


/edit:
i see your desktop walpaper and icons aren't working. 
make sure nautilus is handling the desktop by checking dconf-editor for settings below:
[IMG]http://ubuntuone.com/5xlNCH2Ipe3GuO7kDBsSei[/IMG]

---

