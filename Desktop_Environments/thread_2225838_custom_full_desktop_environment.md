---
title: "custom full desktop environment"
date: 2014-05-23
forum: Desktop Environments
---

### Post by adam31 on 2014-05-23
I've been looking for this for a while, but have had no luck. I know how get a new window manager, but that's all. People seem to be confused with window managers and desktop environments. A window manager is what manages your windows and usually your menu too when alone. What I need help with is a desktop environment, which is the window manager and a file manager with backgrounds, like how linux mint uses caja (I think that was it) to display the desktop with your icons and background. So can anyone show me how to make my own combo for an old computer? I'm trying to save as much resources as possible and rather like JWM and just about any light file manager. Thanks! :)

---

### Post by mcduck on 2014-05-23
Just pick a file manager that has the option for managing the desktop. Nautilus can do it, but if you want lighter option then both PCManFM and Thunar are good choices.

Then all you need to do is set your window manager's startup script (or whatever JWM uses, I'm an OpenBox user ;)) to launch the file manager on login. Check the manual for whatever file manager you choose, for example "pcmanfm --desktop" is the command for starting PCManFM with desktop enabled. (Afterwards you might want to check the file manager's options, PCMAnFM will by default replace right-click menu on desktop with it's own, but you can tell it to use right-click for window manager's menu instead)

Of course window manager + file manager is still quite far away from being a desktop environment, which includes quite a lot more tools and services built to work together. But if you are looking for a lightweight setup then a full desktop environment would be overkill anyway, and just picking the simple tools you need would be a better option.

---

### Post by oldfred on 2014-05-23
Some reference info:
 Comparison of desktop environments - diffences in software
[https://wiki.archlinux.org/index.php/Desktop_Environment](https://wiki.archlinux.org/index.php/Desktop_Environment)
[http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments](http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments)

With Ubuntu full enviroment includes many applications like Firefox, Thunderbird, Libreoffice in Ubuntu, but different packages in other flavors.

Best not to install any of these:

 The key meta packages of Ubuntu are :
ubuntu-base (the whole base system which everybody should install)
ubuntu-desktop (the whole gnome environment)
kubuntu-desktop (the whole kde environment)
xubuntu-desktop (the whole xfce4 environment)
lubuntu-desktop (the whole LXDE desktop environment)
edubuntu-desktop (the whole kids/schools oriented gnome environment)
sudo apt-get install ubuntu-desktop

---

### Post by tgalati4 on 2014-05-23
Linux Mint Mate works pretty well with older hardware.  It uses Caja as a Nautilus fork and it has quite a bit of customizability with respect to the file manager and the desktop environment.  Since it is based on Ubuntu, you get the simplicity of Ubuntu updates with user environment that you expect.

---

