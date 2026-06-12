---
title: "Gnome 2.26.1 themes not loading upon restart in Jaunty"
date: 2009-05-11
forum: Desktop Environments
---

### Post by boknoy on 2009-05-11
my theme is not loading automatically upon reboot. it loads only after launching gnome-appearance-properties. any ideas how to correct this?

---

### Post by days_of_ruin on 2009-05-11
> **boknoy said:**
> my theme is not loading automatically upon reboot. it loads only after launching gnome-appearance-properties. any ideas how to correct this?

What do you mean exactly? Do you have the boxy grey "unthemed" widgets?
What kind of theme is it thats not loading?

---

### Post by boknoy on 2009-05-25
I use a customized saved theme, backgrounds, icons downloaded from several websites.It loads okay when selected on appearance preferences.But whenever I reboot my laptop, the configured theme doesn't load automatically.I need to access the appearance preference in order for the selected theme will be loaded.

---

### Post by Michael Knap on 2009-07-23
I have the same problem; however, I do not have a customized theme. Gnome is not loading the theme upon boot *sometimes*. When I start gnome-appearance-properties, my chosen theme is then correctly used. 

The oddest thing about this for me is that this occurs *sometimes* only. I can't seem to isolate a cause.

---

### Post by HungryMan on 2009-09-13
this sucks. GNOME changes my icon set to the **** brown ubuntu, my font size to a ridiculous 10, and the butt ugly default gtk theme. This problem happened after installing kde. I'm looking for the file that kde uses to set the gtk theme.

If you want a hackish workaround, rename your preferred gtk theme's folder in /usr/share/themes/ to Default (you might want to backup the real Default). Also change the "icontheme=" in your theme's theme.index to your preferred icon set.

---

### Post by HungryMan on 2009-09-17
urgh... my volume buttons got screwed too. Now they don't work until I open System>Preferences>Sound.

---

### Post by HungryMan on 2009-09-25
Ok I found the cause of the problem!
Just add
```

gnome-settings-daemon &
``` to your start-up options and everything should work.

---

### Post by som24 on 2009-09-25
[COLOR="DarkGreen"]in my case only cursor is not loading.hoping this will solve my problem too[/COLOR]

---

