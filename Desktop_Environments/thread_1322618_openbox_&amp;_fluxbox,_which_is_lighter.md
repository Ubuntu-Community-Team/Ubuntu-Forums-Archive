---
title: "openbox &amp; fluxbox, which is lighter?"
date: 2009-11-11
forum: Desktop Environments
---

### Post by henryfranz2005 on 2009-11-11
hello guys! I just want to clear this question on my head. Which is lighter? Fluxbox or openbox? btw I have a low mem system. Intel Celeron D with 192 megs of ram thanks!

---

### Post by TenPlus1 on 2009-11-11
I use OpenBox with FbPanel and it only consumes 62mb memory...

---

### Post by RedSquirrel on 2009-11-11
I don't think one is significantly lighter than the other. However, I find openbox is a bit *smoother*, for example, when switching workspaces.

---

### Post by EzeAris on 2009-11-11
I've used both of them, really, I think that Fluxbox is lighter.. but I prefer much more OpenBox, there isn't lot of difference when I say "lighter" that's why i prefered Openbox.

By the way, try with LXDE, is a very good GUI :)

---

### Post by Dullstar on 2009-11-11
I tried LXDE once, didn't really like it, but it sure is a lot better than fluxbox!  I don't know anything about the system requirements of XFCE, but if your system can handle that, I would recommend that.  I have my doubts that it could handle GNOME or KDE.

---

### Post by ColdLunch on 2009-11-11
How would I go about installing Openbox?

I don't want to get rid of Gnome though.  I want the option to use Gnome or Openbox in the login screen.
Is that possible? Thanks! :)

---

### Post by RedSquirrel on 2009-11-11
> **ColdLunch said:**
> How would I go about installing Openbox?

I don't want to get rid of Gnome though.  I want the option to use Gnome or Openbox in the login screen.
Is that possible? Thanks! :)
```
sudo apt-get install openbox
```You will have the option to run either GNOME or Openbox at the login screen.


Edit: You might want to install menu and obconf as well:

```
sudo apt-get install menu obconf
```

Edit #2: In addition to running GNOME or Openbox, you should likely have the option at the login screen to run GNOME with Openbox as the window manager. (I haven't used GNOME for a while, but I imagine that's still the way it works.)

---

