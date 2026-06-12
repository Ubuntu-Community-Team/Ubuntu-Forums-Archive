---
title: "Fonts in folders, Desktop, and many apps turned to squares after upgrade"
date: 2008-04-29
forum: Desktop Environments
---

### Post by tux259 on 2008-04-29
I am trying to attach a screenshot, but I am unable due to the fact that it is too large and all of the menu options in GIMP are squares and I can't recall exactly which is which.

Anyway, this occurred while I was upgrading from 7.04 to 7.10.  I thought it was going to go away.  It hasn't.

For some odd reason, the 'Applications, Places, System' menus DO have fonts, but nearly everything else does not.  All files on the desktop are a series of squares.  All files within folders.  Most applications are having the same problem, and even if the app itself doesn't, the label for it does.

Defoma says the following sets are installed: xfont postscript type1 truetype

Additionally, I've tried using sudo apt-get install fontconfig-config and no luck there.

I'm guessing I'm missing some fonts, but was hoping someone could walk me through how to get them and where to put them, as I am very, very lost.  And I have finals soon.. so this is freaking me out. Haha.

Thanks!

---

### Post by Perpetual on 2008-04-29
> **tux259 said:**
> I am trying to attach a screenshot, but I am unable due to the fact that it is too large and all of the menu options in GIMP are squares and I can't recall exactly which is which.

Anyway, this occurred while I was upgrading from 7.04 to 7.10.  I thought it was going to go away.  It hasn't.

For some odd reason, the 'Applications, Places, System' menus DO have fonts, but nearly everything else does not.  All files on the desktop are a series of squares.  All files within folders.  Most applications are having the same problem, and even if the app itself doesn't, the label for it does.

Defoma says the following sets are installed: xfont postscript type1 truetype

Additionally, I've tried using sudo apt-get install fontconfig-config and no luck there.

I'm guessing I'm missing some fonts, but was hoping someone could walk me through how to get them and where to put them, as I am very, very lost.  And I have finals soon.. so this is freaking me out. Haha.

Thanks!

I assume you have rebooted?  I have had this happen when upgrading Debian Testing to Debian Sid and possibly with Fedora.  After a reboot it was fixed.

---

### Post by tux259 on 2008-04-29
I have restarted multiple times, and the problem remains consistent.

---

### Post by Perpetual on 2008-04-29
> **tux259 said:**
> I have restarted multiple times, and the problem remains consistent.

Try ```
dpkg-reconfigure fontconfig
``` and reboot.

---

### Post by tux259 on 2008-04-29
No luck.

I am unable to open the 'Language Support' app from the System menu in 8.04.  I was thinking that maybe it isn't set to English for some strange reason?  Anyway, it just crashes and I can't read the error because it is a bunch of squares.

Thanks for the help so far, though.

---

### Post by tux259 on 2008-04-29
Update:

This is what I get when I try to open things with gedit via Terminal

"(gedit:9033): Pango-WARNING **: pango_shape called with bad font, expect ugly output

(gedit:9033): Pango-WARNING **: pango_font_get_glyph_extents called with null font argument, expect ugly output

(gedit:9033): Pango-WARNING **: pango_font_get_metrics called with null font argument, expect ugly output
"

Is that error of any use in diagnosing the problem?

Thanks again.

When I tried to change the language through Gnome (I can't select anything from the login screen.. it's all boxes), I got the following error message

I used the command /usr/bin/gnome-language-selector and got...

"  File "/usr/bin/gnome-language-selector", line 6, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
ImportError: /usr/lib/libpangocairo-1.0.so.0: undefined symbol: pango_renderer_get_layout"

---

### Post by tux259 on 2008-04-30
Last post before I attempt to back up what data I can and just wipe it and start over.

[IMG]http://www.mustangmods.com/ims/u/627/784/235837.gif[/IMG]

---

### Post by rdeml on 2008-07-07
I am having the same error when I try to run update-manager:
Traceback (most recent call last):
  File "/usr/bin/gnome-language-selector", line 6, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
ImportError: /usr/lib/libpangocairo-1.0.so.0: undefined symbol: pango_renderer_get_layout


Did you get a resolution to this problem?

---

