---
title: "Changing gtk theme only changes gtk3 themes and not gtk2. Help. . ."
date: 2013-02-08
forum: Desktop Environments
---

### Post by Macfunky on 2013-02-08
I installed KDE to try it out. While i liked it, i didn't want to keep it so i deleted everything it installed after a few days (i installed from the terminal and made note of all packages it installed. When deleting, i deleted everything it installed. I figured this would be the best way to get it back to exactly how it was before i installed it). While i was using it, i had been changing the gtk themes from the KDE settings manager. 

Fast forward a few days to when i decided to delete everything it installed and go back to using gnome shell. I started up the gnome tweak tool to change my gtk theme. It did so but only for gtk3 programs. I'm not sure why none of my gtk2 themes won't change aswell. 

I installed GTK ChTheme to see if this would make a difference. It did indeed change my gtk2 themes but now if i want to change themes i have to use both programs to do it. 

That wasn't a massive deal as i don't change themes much but today i noticed while using Ardour that the theme looked a bit odd. The menus were larger, scrollbars were narrow. I reinstalled it but it didn't seem to make a difference so i started to think it was to do with the problem with gtk2 themes. I believe it is as gtk2 themes with wide scrollbars show up with narrow scrollbars when i change them using Gtk ChTheme so i definitely think that something weird has happened since using KDE and changing the gtk themes from within it. Anyone come across this issue before or have any suggestions on things to try to get it back to how it was before all this happened? Thanks

---

### Post by Frogs Hair on 2013-02-08
If you didn't already you might want to try the remove Kubuntu command at the link . [http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu) 

I remember trying the Kubuntu desktop and removing everything was difficult. After running the command at the link there were a number of packages which I removed with the synaptic package manager.  

After that try the following. ```
sudo apt-get install --reinstall ubuntu-desktop 
```

---

### Post by Macfunky on 2013-02-08
> **Frogs Hair said:**
> If you didn't already you might want to try the remove Kubuntu command at the link . [http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu) 

I remember trying the Kubuntu desktop and removing everything was difficult. After running the command at the link there were a number of packages which I removed with the synaptic package manager.  

After that try the following. ```
sudo apt-get install --reinstall ubuntu-desktop 
```

I saw that link and had done that before. This time, when I installed it i made a copy of all the packages it installed from the terminal and when i went to uninstall it, i did an apt-remove of every package. It should have been exactly the way it was before i installed but it isn't. I did try that command from the link again to see if i missed anything but it told me that it couldn't find any of the packages so everything is uninstalled. I guess that messing around with gtk themes from within kde has changed something but it's obvious what.

---

