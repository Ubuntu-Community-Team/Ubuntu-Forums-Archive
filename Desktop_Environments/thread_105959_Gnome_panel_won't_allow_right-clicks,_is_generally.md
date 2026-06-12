---
title: "Gnome panel won't allow right-clicks, is generally broken"
date: 2005-12-19
forum: Desktop Environments
---

### Post by stalefries on 2005-12-19
I was browsing the web using the new Firefox 1.5, and decided to drag one of the tabs over to organize my tabs. About the same time, I noticed that the Applications, Places, and System menus were gone, as were my application launchers. The panel wouldn't do anything when I rigth-clicked, so I tried a killall gnome-panel. All that did was bring back 2 blank panels, which would not accept right-clicks, and had nothing on them. I tried restarting X, and that didn't change the situation. I tried apt-get removing gnome-panel, then killall gnome-panel, then apt-get installing gnome-panel, and it didn't help at all. The only reason I can launch firefox and write this is because I have a firefox launcher on this osx dock-like applet running from gdesklets. It'd be really helpful if someone could help me get this working. Thanks.

---

### Post by manicka on 2005-12-19
What about a restart

---

### Post by stalefries on 2005-12-19
Restart, as in rebooting? Yeah, I did that too. I forgot about it, though.

---

### Post by stalefries on 2005-12-19
/bump

Any other ideas, anyone?

---

### Post by stalefries on 2005-12-19
I just ran "top", and it showed that gnome-panel was using something like 95% of CPU. It's obviously doing something...

---

### Post by manicka on 2005-12-20
Do you have the deskbar-applet installed any of your panels? Try ininstalling it with Synaptic, then restarting your panel/gnome session

---

### Post by stalefries on 2005-12-20
Yes, it is installed. Do you mean uninstalling it? I'll try.

---

### Post by stalefries on 2005-12-20
[QUOTE=stalefries]Yes, it is installed. Do you mean uninstalling it? I'll try.[/QUOTE]
I just did, but I forgot to killall gnome-panel, and instead just rebooted. I tried logging in as failsafe gnome, since I also forgot to remove deskbar-applet from the startup porgrams in the session setttings. I'm currently posting this from lynx, since I couldn't start firefox, since I couldn't open it from the terminal or from the panel, since neither were available to me. Is there a way to edit the start-up programs from a virtual terminal?

---

### Post by manicka on 2005-12-21
If you uninstalled it just do a normal reboot. You'll get an error message asking you if you want to remove it from the session manager, then you won't see it again.

---

### Post by stalefries on 2005-12-21
I ended up solving it in a different way. See [http://ubuntuforums.org/showthread.php?t=106518&highlight=gnome-panel](http://ubuntuforums.org/showthread.php?t=106518&highlight=gnome-panel)
.

---

