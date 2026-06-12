---
title: "pekwm + gtk"
date: 2008-05-17
forum: Desktop Environments
---

### Post by Miller12 on 2008-05-17
I am having trouble changing my gtk theme when using pekwm. 

I did a CLI of 7.10 and got pekwm 0.1.5 from the repos. Using urukrama's guide ([here]("http://ubuntuforums.org/showthread.php?t=662204")) I've got pekwm running, I've got a background and have started to edit the menu. I cannot for the life of me get the gtk theme to change and stay working. The things I have tried are from urukrama's blog:

Created a .gtkrc-2.0 file which doesn't work.
Installed gtk-chtheme and gtk-theme-switch which will not change the theme.
Running gnome-settings-daemon will change the gtk but it does with errors and is not a permanent fix. 

the theme I want to use requires gtk-engines-pixmap and altough I have it installed through synaptic, I get a pixmap not found error in xsession-errors.

I am sure it has something to do with my inital setup of the OS and the correct things are not being loaded since this was my first attempt at doing a CLI and using a *box WM.

Thank you.

---

### Post by urukrama on 2008-05-18
I'm not sure what causes the problem. Is it only that pixmap theme that doesn't load, or are other themes also not working?

What errors does xsession-errors list? Can you post the contents of that file here?

---

### Post by Miller12 on 2008-05-18
The last time I started up the gtk theme actually started but there were still errors - ie. the slider bar and text being the wrong color (highlighted white text on a white background)

This is my .gtkrc-2.0
```

# &#8212; THEME AUTO-WRITTEN DO NOT EDIT
include &#8220;/home/ryan/.themes/BlackWhite/gtk-2.0/gtkrc&#8221;

# &#8212; THEME AUTO-WRITTEN DO NOT EDIT
```

This is the xsession-errors:

```
(process:5143): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:5147): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
 *** WARNING: Menu missing border texture BOTTOMRIGHT UNFOCUSED
TRYING TO USE UNDEFINED VARIABLE: $term
TRYING TO USE UNDEFINED VARIABLE: $term
TRYING TO USE UNDEFINED VARIABLE: $term
TRYING TO USE UNDEFINED VARIABLE: $term
/home/ryan/.gtkrc-2.0:2: error: unexpected character `\342', expected string constant

** (gnome-settings-daemon:5210): WARNING **: Module GnomeSettingsModuleScreensaver could not be started
/home/ryan/.gtkrc-2.0:2: error: unexpected character `\342', expected string constant

(gnome-settings-daemon:5210): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-settings-daemon:5210): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-settings-daemon:5210): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-settings-daemon:5210): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-settings-daemon:5210): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-settings-daemon:5210): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-settings-daemon:5210): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-settings-daemon:5210): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-settings-daemon:5210): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-settings-daemon:5210): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-settings-daemon:5210): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-settings-daemon:5210): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-settings-daemon:5210): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-settings-daemon:5210): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-settings-daemon:5210): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-settings-daemon:5210): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-settings-daemon:5210): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-settings-daemon:5210): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-settings-daemon:5210): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-settings-daemon:5210): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-settings-daemon:5210): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-settings-daemon:5210): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-settings-daemon:5210): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-settings-daemon:5210): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-settings-daemon:5210): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-settings-daemon:5210): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-settings-daemon:5210): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192
/home/ryan/.gtkrc-2.0:2: error: unexpected character `\342', expected string constant

(thunar:5221): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(thunar:5221): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(thunar:5221): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(thunar:5221): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(thunar:5221): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(thunar:5221): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(thunar:5221): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(thunar:5221): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(thunar:5221): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(thunar:5221): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(thunar:5221): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(thunar:5221): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(thunar:5221): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(thunar:5221): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(thunar:5221): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(thunar:5221): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(thunar:5221): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(thunar:5221): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(thunar:5221): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(thunar:5221): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(thunar:5221): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(thunar:5221): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(thunar:5221): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(thunar:5221): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(thunar:5221): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(thunar:5221): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(thunar:5221): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
/home/ryan/.gtkrc-2.0:2: error: unexpected character `\342', expected string constant

(gedit:5230): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5230): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5230): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5230): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5230): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5230): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5230): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5230): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5230): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5230): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5230): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5230): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5230): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5230): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5230): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5230): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5230): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5230): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5230): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5230): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5230): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5230): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5230): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5230): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5230): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5230): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5230): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
```

I've tried three themes and they all ask for 'pixmap'.

Thank you.

---

### Post by kerry_s on 2008-05-18
try removing it and installing it again.
[B]sudo apt-get remove --purge gtk-engines-pixmap
sudo apt-get install gtk-engines-pixmap[/B]

---

### Post by Miller12 on 2008-05-18
> **kerry_s said:**
> try removing it and installing it again.
[B]sudo apt-get remove --purge gtk-engines-pixmap
sudo apt-get install gtk-engines-pixmap[/B]

No luck.

Here is what mine looks like:
[http://img381.imageshack.us/img381/7343/screen2mu1.png]("http://img381.imageshack.us/img381/7343/screen2mu1.png")

This is what it should look like:
[BlackWhite by lyrae]("http://www.gnome-look.org/content/show.php/BlackWhite?content=68803")

---

### Post by kerry_s on 2008-05-18
did you do this part?

> 
I have included a black menubar as shown on the second screenshot.
To use it, open BlackWhite/gtk-2.0/gtkrc and uncomment "include menubar-black.rc"
and then add a comment to "include menubar.rc"


other than that i have no idea, been up all night, so i'll look closer later.

---

### Post by Miller12 on 2008-05-18
For some reason I was thinking that was for the panel...duh. Unfortunately it did not help.

---

### Post by urukrama on 2008-05-20
Do you have *gtk2-engines-pixbuf* and *gtk-engines-pixmap* installed (both in the repositories)?

---

