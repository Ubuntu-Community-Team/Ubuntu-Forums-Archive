---
title: "Change system fixed width font"
date: 2013-09-03
forum: Desktop Environments
---

### Post by makaze2 on 2013-09-03
No matter where I look, the only thing that anyone knows how to do is change the terminal font. How do I change the system fixed width font from the default Monospace 11 in XFCE?

---

### Post by ajgreeny on 2013-09-03
I am using an android tablet to answer this, but surely you need to go to settings->settings manager->appearance->fonts tab to change all the font settings.
Unfortunately I can't check that for myself at the moment and my memory may be playing tricks on me!

---

### Post by makaze2 on 2013-09-03
> **ajgreeny said:**
> I am using an android tablet to answer this, but surely you need to go to settings->settings manager->appearance->fonts tab to change all the font settings.
Unfortunately I can't check that for myself at the moment and my memory may be playing tricks on me!
There is no fixed width font option. The only font you can edit through the GUI is the main system font.

---

### Post by Toz on 2013-09-03
Where are you seeing this fixed font? A screenshot may help.

---

### Post by makaze2 on 2013-09-03
[IMG]http://i.minus.com/i6ZEDSyKmPp2L.png[/IMG]

It also affects Chrome and other programs. I would like to change this system default instead of changing the settings for individual programs.

---

### Post by Toz on 2013-09-03
I don't think that you're going to find a setting in Xfce that is going to change the system default font (outside of what ajgreeny noted above). Mainly because (in your case) gedit is a gnome app that has its own specific configuration system (and definition of "system fixed width font") and chrome is a 3rd party app that does the same. 

Having said that, you may have some luck by looking into font substition. Font substition is an X-level configuration option that basically substitutes one font for another. I haven't personally experimented with font substition, but here are a few links that may help you get started:
- [https://wiki.ubuntu.com/Fonts]("https://wiki.ubuntu.com/Fonts")
- [http://weirdfellow.wordpress.com/2010/07/20/linux-font-substitutions/]("http://weirdfellow.wordpress.com/2010/07/20/linux-font-substitutions/")
- [http://www.freedesktop.org/software/fontconfig/fontconfig-user.html#AEN134]("http://www.freedesktop.org/software/fontconfig/fontconfig-user.html#AEN134")
- [http://superuser.com/questions/116859/font-substitution-with-fonts-conf]("http://superuser.com/questions/116859/font-substitution-with-fonts-conf")
- [https://wiki.archlinux.org/index.php/Font_Configuration#Replace_fonts]("https://wiki.archlinux.org/index.php/Font_Configuration#Replace_fonts")

---

### Post by makaze2 on 2013-09-03
I want to change the size more than the font-family.

I am disappointed to hear that these problems exist.

---

### Post by vasa1 on 2013-09-03
> **makaze2 said:**
> No matter where I look, the only thing that anyone knows how to do is change the terminal font. How do I change the system fixed width font from the default Monospace 11 in XFCE?

This maybe seem stupid but I'm asking sincerely: 
[LIST]
[*]What do you mean by "system fixed width font"?
[*]In what context do you encounter it?
[*]Where would you like it to be different or to be used?
[/LIST]

---

### Post by makaze2 on 2013-09-03
> **vasa1 said:**
> This maybe seem stupid but I'm asking sincerely: 
[LIST]
[*]What do you mean by "system fixed width font"?
[*]In what context do you encounter it?
[*]Where would you like it to be different or to be used?
[/LIST]

A system-wide default fixed width font. For example, [FONT=courier new]Courier New[/FONT] is the default system fixed width font on Windows.

I encounter it here and in many other programs such as Chrome.

[IMG]http://i.minus.com/i6ZEDSyKmPp2L.png[/IMG]

I would like to know how to change either the font face, the size, or both on a system-wide scale.

Read the thread and see if you have anything to add.

---

### Post by vasa1 on 2013-09-03
> **makaze2 said:**
> ...
Read the thread and see if you have anything to add.
I read the thread.

---

### Post by josh.helzer on 2014-06-18
> **makaze2 said:**
> [IMG]http://i.minus.com/i6ZEDSyKmPp2L.png[/IMG]

It also affects Chrome and other programs. I would like to change this system default instead of changing the settings for individual programs.

I had the same problem.  To change what gedit reports as the "system fixed width font", I found that this worked:

```
gsettings set org.gnome.desktop.interface monospace-font-name 'Monospace 9'
```

I came across this because (at least as of gedit 3.10.4) the Tool Output pane of the External Tools plugin is hard-coded to use this system font, rather than the "Editor font".

You might also be interested in the other font settings that are exposed via gsettings:

```
gsettings list-recursively | grep font
```

---

