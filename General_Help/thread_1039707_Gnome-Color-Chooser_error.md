---
title: "Gnome-Color-Chooser error"
date: 2009-01-14
forum: General Help
---

### Post by IceReaver75 on 2009-01-14
I installed the gnome-color-chooser from their website. I had to compile it and it compiled with no errors but now won't do anything when things are selected.  I ran it through the terminal and it says this inside the terminal.:

Welcome to gnome-color-chooser version 0.2.4 for i686-pc-linux-gnu
then about 30 or so of these comments in a row

(gnome-color-chooser:6722): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

Then at the end it says
Error in accessing /usr/local/share/gtk-engines/: No such file or directory
Couldn't find any engine schema!

Does anyone know how to fix these problems so the color-chooser will work.  Thanks for any help you may have.

---

### Post by gettinoriginal on 2009-01-15
Uninstall the one you compiled via terminal, then install it from Synaptic.

---

### Post by IceReaver75 on 2009-01-15
yeah that is exactly what I did.  Never figured out what went wrong with the compiled version but the one in synaptic works just fine.

---

### Post by gettinoriginal on 2009-01-16
Sometimes in compiling from third party sources, we get the latest/newest which is not necessarily the most stable.  If it is available in Synaptic, it is usually the lastest ***_stable_*** release  :p

---

### Post by JackTheDipper on 2009-01-23
heh, that were even two problems at once. If you're interested in some details, here they are:

1. On Ubuntu(/Debian) you have to compile it with --prefix=/usr because your gtk2-engines package is compiled with that prefix. After that, it is able to configure your installed GTK+ engines.

2. That nothing happened when you click on apply depends on a bug in 0.2.4 (which is fixed in trunk, see this link for more details: [http://gnomecc.sourceforge.net/forum/index.php?topic=19.msg46#msg46](http://gnomecc.sourceforge.net/forum/index.php?topic=19.msg46#msg46) ).

0.2.4 should run fine if you run 0.2.3 on the same computer before, though. The current trunk version should also be pretty stable (as the real development is in another branch currently ;))

Best regards,
JackTheDipper ;-)

---

