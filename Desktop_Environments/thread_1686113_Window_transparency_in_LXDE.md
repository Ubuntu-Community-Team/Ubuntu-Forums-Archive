---
title: "Window transparency in LXDE?"
date: 2011-02-11
forum: Desktop Environments
---

### Post by whatthefunk on 2011-02-11
I've been tweaking my desktop and noticed that I can't make windows transparent in Lubuntu.  For example, I use the Guake terminal.  It has a transparency option so that you can see through it.  Even if I set it at the highest transparency level, I still can't see through it.  If I set a background image and set the transparency to high, the picture gets less visible, but I still cant see through it.  Is there anything I can do about this?  Thanks.

---

### Post by 3Miro on 2011-02-11
Lubuntu used the LXDE desktop environment and the OpenBox windows manager. LXDE is designed to be a very light-weight environment and windows transparency does require system resources. OpenBox does not support "native" transparency.

Some programs (like LXTerminal), do come with "fake" transparency option. They will read the desktop background image and merge it with the program windows, but this works only for the background, fake transparency will not show the content of a window underneath. Overall very few programs support fake transparency since it is not very useful, most program rely on the window manager to handle such things.

If you want to get full transparency, you can use another window manager (like Metacity, XFWM4 or Compiz), which will probably come at the expense of system resources. Alternatively, you can use a "hack" into the Xserver itself:

[https://wiki.archlinux.org/index.php/Openbox#Window_transparency](https://wiki.archlinux.org/index.php/Openbox#Window_transparency)

However, don't do this unless you know what you are doing, it can potentially mess your system.

---

### Post by whatthefunk on 2011-02-11
Thanks 3Miro.  The transparency is not that big of an issue..I was just curious as to why it didnt work, especially since the default LXTerminal has a transparency option.  Anyway, you answered my questions.  Thanks.

---

