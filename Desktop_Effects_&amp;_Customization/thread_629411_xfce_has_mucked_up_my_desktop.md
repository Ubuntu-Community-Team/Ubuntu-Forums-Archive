---
title: "xfce has mucked up my desktop"
date: 2007-12-02
forum: Desktop Effects &amp; Customization
---

### Post by grindboy on 2007-12-02
OK... I've got a brand new squeaky clean installation of 7.10, I installed all the updates and then I went to enable desktop effects, I clicked on advanced desktop effects and I've ended up with xfce not compiz fusion. Now onto the problem, thinking it would revert back to the ubuntu desktop I asked xfce not to manage the desktop. Now I've got no task panes (top or bottom bars), I can't right click to bring up menus, I have got Launcher (whatever that is?) running and though pure fluke I can get into firefox by asking launcher for its help pages.

All I want is the bog standard Ubuntu desktop back so that I can follow one of the numerous online tutorials and get compiz fusion running.

Hope someone can help otherwise I'm back to using Vista :(

Would the easiest way to solve this be to do a clean install?

---

### Post by xlinuks on 2007-12-02
If you have Xubuntu, I would install the Gnome desktop
```

http://ubuntuforums.org/showthread.php?t=520384

```
there's gonna be quite a lot to download though, then log off, and at the login screen I would choose to use the GDM (Gnome Desktop Manager) by default, now log in, IMO anything should work under Gnome...

---

### Post by xlinuks on 2007-12-02
Just a quick note, instead of
sudo aptitude update && sudo aptitude install gnome-desktop
You _might_ need to type
sudo aptitude update && sudo aptitude install gnome
(this is from my experience, under Ubuntu there seems to be no "sudo apt-get install kde-desktop" anymore, but just "sudo apt-get install kde")

---

### Post by grindboy on 2007-12-02
No I'm running just plain old Ubuntu 7.10. I can't get access to the terminal or anything in the current state my desktop is in! Would a full reinstallation work?

---

### Post by xlinuks on 2007-12-02
A reinstallation would help for sure, if you need the terminal Alt+F2 to bring up the "Run application" program, then "gnome-terminal" to get the terminal.

---

### Post by grindboy on 2007-12-02
Is there a run program command to bring up the normal task panes?

---

### Post by grindboy on 2007-12-02
OK gonna try a fresh install, Thanks for all your help xlinuks

---

### Post by xlinuks on 2007-12-02
"gnome-panel" adds a panel.."alacarte" allows for editing menus,..

---

### Post by xlinuks on 2007-12-02
For nothing..

---

### Post by bapoumba on 2007-12-02
@ grindboy: can you log out from your session ?
At GDM, you'll have the choice to start again on GNOME (I think it is the session menu).
No need to reinstall.

---

### Post by xlinuks on 2007-12-02
I guess he can't hear us, he's prolly reinstalling the OS by now :)

---

### Post by bapoumba on 2007-12-02
> **xlinuks said:**
> I guess he can't hear us, he's prolly reinstalling the OS by now :)

Maybe ^^

---

