---
title: "In openbox, I can't change icon theme through gtkrc-2.0"
date: 2010-12-30
forum: Desktop Environments
---

### Post by fwoncn on 2010-12-30
jjHi! I'm using openbox. I can't configure themes and icons in the old way, that is, using Gnome's Appearance dialog. I searched on google and did exactly what it says: downloaded the icon tarball and extract it to /usr/share/icons/, and add this to ~/.gtkrc-2.0:
gtk-icon-theme-name="XXX" (where XXX is the theme's name, equivalent to the folder name in /usr/share/icons/)
And also i have tried the program, lxappearance. It just make things worse.
No matter how I tried, still no luck on that.
Anyone has a clue? Thank you!

And BTW, happy new year to everyone!

EDIT:
I finally found the reason: it's because the remaining Gnome stuff. Two way to solve:
1. remoe gnome-settings-daemon (may bring up side effects)
2. safe to do: fire up "gconf-editor" n' locate /desktop/gnome/interface/icon_theme n' change the value to the name of the icon theme you want

---

### Post by Jose Catre-Vandis on 2010-12-30
Try it with tango, and see if that works:
```
sudo apt-get install tango-icon-theme tango-icon-theme-extras
```
then put

gtk-icon-theme-name = "Tango"

in ~/.gtkrc-2.0

Check your spacing and capitalisation !

---

### Post by fwoncn on 2010-12-30
doesn't change. I bet spacing and capitalization is good.

---

### Post by Jose Catre-Vandis on 2010-12-30
You bet? Please be sure. for tango it requires "Tango"

Are you rebooting? Sometimes a full shutdown is needed (don't ask me why?)

---

### Post by fwoncn on 2010-12-30
Yes I believe everything you mentioned is done. I have rebooted couple of times. Here is the content of my .gtkrc-2.0
```
include "/usr/share/themes/Atolm/gtk-2.0/gtkrc"

style "user-font"
{
  font_name="DroidSans 9"
}
widget_class "*" style "user-font"

gtk-icon-theme-name = "Tango"
```pretty normal.

I took a screen shot to show I've correctly installed the necessary icon theme: [http://imm.io/2PPJ](http://imm.io/2PPJ)

EDIT: And strangely, sometimes when I log in, I can see the right icon set for 1 sec, but after that the default Gnome icon set comes back and takes place.

---

### Post by Jose Catre-Vandis on 2010-12-31
Is you other theme overriding it? Try a .gtkrc-2.0 with just your last line?

Also have a read through here, if you haven't already done so:
[http://urukrama.wordpress.com/openbox-guide/#Gtkthemes](http://urukrama.wordpress.com/openbox-guide/#Gtkthemes)

---

### Post by fwoncn on 2010-12-31
Sigh... Still no effect. I give up for now.

Thank you very much anyway, Jose!

---

### Post by hsa2 on 2011-03-26
You need to show openbox where you keep your gtk settings

add this to your xinitrc
```
export GTK2_RC_FILES="$HOME/.gtkrc-2.0"
```

---

