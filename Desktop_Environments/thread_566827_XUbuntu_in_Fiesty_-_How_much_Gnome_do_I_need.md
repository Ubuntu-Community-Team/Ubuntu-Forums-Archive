---
title: "XUbuntu in Fiesty - How much Gnome do I need?"
date: 2007-10-03
forum: Desktop Environments
---

### Post by AustinMarton on 2007-10-03
Hi Everbody!

I've recently switched to XFCE (XUbuntu from Ubuntu), my laptop is running at speeds beyond my wildest dreams. I'm not planning to switch into Gnome again, but I'm under the impression XFCE still uses some of the Gnome libraries or something?

My question is, how much Gnome do I need? Can I remove the Gnome desktop environment without handy-capping my XFCE? (If so how?)

I'm also having a bit of trouble customizing the Applications menu, I'm looking at ~/.config/xfce4/desktop/menu.xml
I can add custom launchers to the main menu, but I can't see (let alone add/remove things from) the existing sub-menus such as "Development", "Games" etc. It seems to have imported them from Gnome.

Cheers,
Oz

---

### Post by Chymera on 2007-10-04
Actually you don't need much of gnome. The problem is that whenever you install a gnome application the dependency manager will want to add half of the gdm libraries. You can delete them manually afterwards, but you have to know EXACTLY what you are doing. 
Then again, if you are so knowledgeable as to be able to tell exactly what you need and what you don't need, why bother with ubuntu? ...you may be better off using gentoo linux, which is built to deal with exactly such issues of customization.

---

### Post by aidanr on 2007-10-04
The launchers you import from gnome can still be edited with alacarte, but personally I just prefer to scrap them (xfce4-menueditor -> delete the system entry) and add lauchers manually. I wouldn't worry about getting rid of the gnome libs, all they'll cost you is a small bit of harddrive space, it won't speed things up getting rid of everything gnome related.

---

### Post by mrazster on 2007-10-04
This might be useful.... :)

[http://forum.xfce.org/index.php?topic=2658.0](http://forum.xfce.org/index.php?topic=2658.0)

---

### Post by AustinMarton on 2007-10-04
Cheers guys! I'm adding and modifying the launchers in /usr/share/applications and it's working splendidly. 

I've got a sub-menu "Other" which has all my applications from Wine and a few others, but they're not in the /usr/share/application directory, any ideas where they might be located?

---

### Post by aidanr on 2007-10-04
probably in ~/.local/share/applications or /usr/local/share/applications

---

### Post by Gremlinzzz on 2007-10-04
I switched to xubuntu from ubuntu gnome and i like it.what i did was before getting updates or installing any programs i updated the kernel. running fast and solid as a rock.2.6.22-12-generic
updated the kernel from this post
[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

---

### Post by Gremlinzzz on 2007-10-04
what i found strange in xubuntu if you want to tweak grub menu the command is.
sudo mousepad /boot/grub/menu.lst
might be good to know.:guitar:

---

