---
title: "openbox3 gtk-fonts"
date: 2006-06-03
forum: Desktop Environments
---

### Post by graabein on 2006-06-03
I have looked at the [Ach Linux wiki]("http://wiki.archlinux.org/index.php/Getting_Openbox_Running") and created *.gtkrc.mine* file containing this:

```
# If you want to change the type and size of your fonts, add this to $HOME/.gtkrc.mine

style "user-font"
{
font_name = "Bitstream Vera Sans 8"
}
widget_class "*" style "user-font"
gtk-font-name = "Bitstream Vera Sans 8"

# where "[font-name] [size]" is e.g "Bitstream Vera Sans 9".
# You need to fill in both fields because of backwards compatiblity. 

```

Seems like it doesn't load on startup. My *.xinitrc* looks like this:

```

feh --bg-scale ~/wallpaper.jpg
pypanel &
conky &
exec openbox
```

I do not want to run gnome-settings-daemon since I don't have GNOME installed on my base install. 

Do I have to change file settings to make it executable? Any ideas what to do? 

Cause the fonts are obviously not Bitstream Vera Sans 8 pt. I know I have the font installed cause I looked it up in leafpad and compared it to the application face... Ugh...

---

### Post by IYY on 2006-06-03
One way to do it would be to change the gtkrc file in the theme you are using. To apply a theme without using Gnome, use gtk-theme-switch2.

If you're not using a theme that overrides the font, maybe you could try adding your changes to ~/.gtkrc-2.0.

---

### Post by TheMadArab on 2006-06-04
I suggest using switch2 as well, although if you don't want to, just add this line to your .gtkrc-2.0
```

include "~/.gtkrc-2.0.mine"

```

---

### Post by graabein on 2006-06-06
OK thanks guys, I'll have a look at it tonight. I want my old and busted laptop to look good without coming to a grinding halt.



EDIT: I ran gtk-theme-switch2 and I only had *Raleigh* available. I located its gtkrc file and pasted my font config in there. It works allright!

:)

---

