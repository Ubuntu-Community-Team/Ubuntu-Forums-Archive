---
title: "Change icons, lettering"
date: 2008-06-02
forum: Desktop Environments
---

### Post by mopalia on 2008-06-02
I need to change the lettering below icons to plain solid black, no shadows. I also want simpler icons: no thumbnails/previews (especially not in .pdf or .jpg files), no colored panels in .odt icons -just really plain rectangles, like the message icon above.  Everything in Gnome Art is too fussy or obtrusive.  Any help? 
Running Gnome Heron (Hardy)

---

### Post by Dylnuge on 2008-06-02
In your Visual Settings (under 8.04, right click on the desktop and choose the settings choice), you can shut off desktop effects.

If that isn't what's bothering you, there is a Fonts option inside your preferences menu, changing the system font may help.

-Dylnuge

---

### Post by mopalia on 2008-06-02
Thanks, I've done all that.  The Fonts menu does not affect the fonts inder the icons.  The effects menu doesn't relate to any of that, either.  This took pretty deep manipulation in Windows under the Folders options, and it doesn't seem to be simple in Ubuntu, either.

---

### Post by mopalia on 2008-06-02
> **Dylnuge said:**
> In your Visual Settings (under 8.04, right click on the desktop and choose the settings choice), you can shut off desktop effects.

If that isn't what's bothering you, there is a Fonts option inside your preferences menu, changing the system font may help.

-Dylnuge

 Re: Change icons, lettering
Thanks, I've done all that. The Fonts menu does not affect the fonts under the icons. The effects menu doesn't relate to any of that, either. This took pretty deep manipulation in Windows under the Folders options, and it doesn't seem to be simple in Ubuntu, either.

---

### Post by Dylnuge on 2008-06-02
Did you change the font rendering type in Preferences -> Appearances -> Customize -> Fonts?

---

### Post by mopalia on 2008-06-03
> **Dylnuge said:**
> Did you change the font rendering type in Preferences -> Appearances -> Customize -> Fonts?

Yes.  It doesn't affect the font under the icons on the desktop.

---

### Post by mcduck on 2008-06-03
The icon text shadows can be disabled with by creating a ".gtkrc-2.0"-file in your home directory and adding a couple of lines there..

```
style "desktop-icon"
{
  NautilusIconContainer::frame_text = 1
  text[NORMAL] = "#000000"
  NautilusIconContainer::normal_alpha = 0
  NautilusIconContainer::highlight_alpha = 255
  NautilusIconContainer::dark_info_color = "#222266"
  NautilusIconContainer::light_info_color = "#dddddd"
}
class "GtkWidget" style "desktop-icon"
```

Actually that piece of code allows you to define icon text colors and text container opacity as well, but the important trick here is enabling the text container and then setting it's opacity to 0 to make it invisible. Enabling the container will disable the shadowed text..

---

### Post by mopalia on 2008-06-03
Score!  Thank you, mcduck, you have made me very happy.  You are my hero.

---

