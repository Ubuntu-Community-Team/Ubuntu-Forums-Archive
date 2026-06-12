---
title: "i3-wm"
date: 2013-01-10
forum: Desktop Environments
---

### Post by Elitenoname on 2013-01-10
hey, I don't know if this is in the right place but,

anyone use the i3-wm on ubuntu? I am having problems when I launch an application the terminal window still stays open and the applications I opened only is half the screen now is there something I have to do so that the terminal window closes but the application stays running?

---

### Post by ibjsb4 on 2013-01-10
Tiling window managers are not very popular and going to be tough getting support for one.  You may be better off trying some others. 

[https://wiki.archlinux.org/index.php/Comparison_of_Tiling_Window_Managers](https://wiki.archlinux.org/index.php/Comparison_of_Tiling_Window_Managers)

If you are looking for a light WM, I would suggest:

OpenBox

BlackBox

FluxBox

I haven't bothered to look, but I think you will find them all in the software center.

---

### Post by kevinmchapman on 2013-01-10
> **Elitenoname said:**
> hey, I don't know if this is in the right place but,

anyone use the i3-wm on ubuntu? I am having problems when I launch an application the terminal window still stays open and the applications I opened only is half the screen now is there something I have to do so that the terminal window closes but the application stays running?

I take it you are launching the application by typing its name in the original terminal? If so, that's how the tiling works - the screen gets divided by the number of aplications. What you really need is something like dmenu to use as a launcher. Think of it as a command-line-like version of Launchy or Gnome-Do.

This shows the basics:

[https://wiki.archlinux.org/index.php/Dmenu]("https://wiki.archlinux.org/index.php/Dmenu")

---

### Post by Elitenoname on 2013-01-10
i see that dmenue (dwm-tools) is not in the repositories anymore?

---

### Post by kevinmchapman on 2013-01-10
Sorry, I don't use Ubuntu, so was not able to check. Hopefully this is what you need:

[http://pkgs.org/download/dmenu]("http://pkgs.org/download/dmenu")

---

