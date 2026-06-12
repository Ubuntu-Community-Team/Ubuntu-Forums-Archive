---
title: "Unable to change theme in Appearance"
date: 2009-03-29
forum: General Help
---

### Post by Ionna on 2009-03-29
I downloaded a few themes the other day from Gnome-Look and installed them. However, one of them caused my Appearance preferences window to crash, and now it's also causing my pidgin to crash as well. It's also stopping me from launching Chatzilla.

How I do remove the theme using either terminal or any other methods? Trying to open the Appearance Preferences window does not work. 

Help!

---

### Post by Ionna on 2009-03-29
Anyone? I remember there was a way to remove themes via terminal, is that possible here?

---

### Post by VCoolio on 2009-03-29
Yes, you can delete themes with rm -r /home/[you]/.themes/themeyouwantdeleted. For safety you may want to rename them: replace 'rm -r' with 'mv'. Not sure if that solves the problem you're having, since this won't affect your settings. If your configuration editor still works you can change themes via desktop > gnome > interface. You can use gtk-theme-switch for commandline (check [this]("http://listento.jaketolbert.com/linux/change-gtk-theme-from-command-line/")).

---

### Post by Ionna on 2009-03-29
Yes! That was what I was looking for, will try it when I get home tonight.

Edit: THANKS!

---

