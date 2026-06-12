---
title: "Remove unity/gnome, use only a window manager"
date: 2012-04-25
forum: Desktop Environments
---

### Post by ratman1 on 2012-04-25
Hi

I have been distro-hopping for a few years now, on and off between ubuntu, mint, fedora, arch, and even the occasional return to windows. I stuck with mint for the longest, then recently made the switch to arch. Now I am returning to ubuntu, after finding that my skills weren't quite up for arch yet (I kept breaking it!).

During my time with arch, I discovered the idea of having only a window manager without the full blown desktop environment. I am wondering if I could set ubuntu up that way so that instead of loading unity when I log in, I would be presented with openbox (or awesome, fluxbox, icewm, etc).

I know that ubuntu uses an underlying window manager, and has created the desktop environment on top of that. I wish to remove both, and have only the window manager.

Is that possible, after having installed the full ubuntu? Or would it be easier to use the alternate install, and choose not to install all the other stuff.

Thanks,
James

---

### Post by 3Miro on 2012-04-25
You can check here on how to remove various desktop environments. If you want something light, you can try LXDE, which is basically OpenBox with a panel and file manager. You can also just install OpenBox, edit .config/openbox/autostart with the programs that you want to load on startup (i.e. lxpanel, feh, I also like the combination of xcompmgr + avant-windows-navigator).

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by cortman on 2012-04-25
The ISO's are buried back on an obscure help page (go figure), but looks like your best bet would probably be a minimal CD, on top of which you could install X and openbox. Available [here.]("https://help.ubuntu.com/community/Installation/MinimalCD")
Trying to turn a standard Ubuntu installation into a minimal has never worked in the long run for me.

---

