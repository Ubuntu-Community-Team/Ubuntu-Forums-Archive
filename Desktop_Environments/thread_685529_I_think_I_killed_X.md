---
title: "I think I killed X"
date: 2008-02-02
forum: Desktop Environments
---

### Post by Envergure on 2008-02-02
I installed all the packages for Xfce and KDE on top of my existing GNOME installation to see which I liked the best.  I settled on GNOME, but I still had like 200 packaged from KDE and Xfce so I removed them manually, from the Synaptic Package Manager.

Now my windows don't have those orange borders.  I can't resize, minimize, maximize or close windows, or even move them off the top Panel (to get to the menus I have to Ctrl+Alt+Backspace (restart X) and log in again).  The right-click menus in Firefox appear below the Firefox main window and I can't click on them.  Also, I can't switch desktops and nothing shows in the window list.

Any ideas what I did wrong?  I imagine I have to just reinstall whatever package has the styles in it.

Oh, and Alt+Tabbing (switch windows) doesn't work either.  Neither does Alt+F4 (kill the current application).
Oh, one more thing:  I have that "Sticky Notes" applet, and I can move the notes around but they no longer stick to the edges of the screen like they used to.

---

### Post by taurus on 2008-02-02
Maybe try reinstalling ubuntu-desktop again.

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by Envergure on 2008-02-02
That did it, thxD.

Maybe it was because I removed Compiz?

---

