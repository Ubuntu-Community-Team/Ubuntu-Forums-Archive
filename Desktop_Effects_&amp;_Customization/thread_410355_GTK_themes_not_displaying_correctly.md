---
title: "GTK themes not displaying correctly"
date: 2007-04-15
forum: Desktop Effects &amp; Customization
---

### Post by dominicd on 2007-04-15
For some reason, themes I newly install for GTK 2.X are not displaying correctly, namely the slider and buttons/tabs look weird like the theme "Gray" for controls. Newly installed icons work fine, it's the controls that aren't showing correctly. Any ideas? I checked my GTK version and it seems right?

my output for dpkg -l | grep gtk is:

```

ii  apport-gtk                                 0.28                                 GTK frontend for the apport crash report sys
ii  gtk2-engines                               2.8.1-0ubuntu1                       theme engines for GTK+ 2.x
ii  gtk2-engines-ubuntulooks                   0.9.12-2                             'ubuntulooks' theme for GTK+ 2.x
ii  gtkhtml3.8                                 3.12.1-0ubuntu1                      HTML rendering/editing library - bonobo comp
ii  human-gtk-theme                            0.2-0ubuntu1                         Edgy GDM themes
ii  ia32-libs-gtk                              22                                   gtk+ ia32 shared libraries for with OpenOffi
ii  libgtk2-perl                               1.121-1ubuntu1                       Perl interface to the 2.x series of the Gimp
ii  libgtk2.0-0                                2.10.6-0ubuntu1                      The GTK+ graphical user interface library
ii  libgtk2.0-bin                              2.10.6-0ubuntu1                      The programs for the GTK+ graphical user int
ii  libgtk2.0-cil                              2.10.0-0ubuntu2                      CLI binding for the GTK+ toolkit 2.10
ii  libgtk2.0-common                           2.10.6-0ubuntu1                      Common files for the GTK+ graphical user int
ii  libgtkhtml2-0                              2.11.0-1build1                       HTML rendering/editing library - runtime fil
ii  libgtkhtml3.8-15                           3.12.1-0ubuntu1                      HTML rendering/editing library - runtime fil
ii  libgtksourceview-common                    1.8.1-0ubuntu1                       common files for the GTK+ syntax highlightin
ii  libgtksourceview1.0-0                      1.8.1-0ubuntu1                       shared libraries for the GTK+ syntax highlig
ii  libgtkspell0                               2.0.10-3                             a spell-checking addon for GTK's TextView wi
ii  libwxgtk2.6-0                              2.6.3.2.1.5ubuntu0.1                 wxWidgets Cross-platform C++ GUI toolkit (GT
ii  openoffice.org-gtk                         2.0.4-0ubuntu2                       GTK Integration for OpenOffice.org (Widgets,
ii  python-gtk2                                2.10.3-0ubuntu3                      Python bindings for the GTK+ widget set
ii  python-gtkhtml2                            2.14.2-0ubuntu6                      Python bindings for the GtkHTML2 library
ii  scim-gtk2-immodule                         1.4.4-4ubuntu6                       GTK+2 input method module with SCIM as backe

```

Any ideas?

---

### Post by kairu0 on 2007-04-15
GTK themes often require an "engine" to render the widgets. It looks like the only one you have installed is "gtk2-engines-ubuntulooks."

Find out which engine your theme uses, then search gnome-looks.org for "Engine" to download it.

---

### Post by aidanr on 2007-04-15
you probably need gtk2-engines-pixbuf, you can install it through synaptic

---

### Post by dominicd on 2007-04-15
Yes that's it! It works now. Thanks guys!

---

