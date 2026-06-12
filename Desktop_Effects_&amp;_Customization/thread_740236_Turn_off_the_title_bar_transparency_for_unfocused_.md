---
title: "Turn off the title bar transparency for unfocused windows"
date: 2008-03-30
forum: Desktop Effects &amp; Customization
---

### Post by svivian on 2008-03-30
I've searched through all the options in Compiz looking for transparency/opacity but can't find any option to stop the title bar for unfocused windows from being semi-transparent.

Anyone know where this setting might be??

---

### Post by 23meg on 2008-04-01
Set the /apps/gwd/metacity_theme_opacity gconf key to 1 to make them fully opaque.

---

### Post by svivian on 2008-04-02
> **23meg said:**
> Set the /apps/gwd/metacity_theme_opacity gconf key to 1 to make them fully opaque.

How do I do that?

---

### Post by BOBSONATOR on 2008-04-02
> **svivian said:**
> How do I do that?

for this you go to alt+f2, gconf-editor, then navigate to the directory he listed. Cheers

Thanks!

---

### Post by svivian on 2008-04-03
Excellent, thanks!
Still don't understand why Ubuntu has this setting, it's not like you can ever see anything useful underneath the title bar - only other title bar text getting in the way!

---

### Post by mozetti on 2008-04-03
> **svivian said:**
> Excellent, thanks!
Still don't understand why Ubuntu has this setting, it's not like you can ever see anything useful underneath the title bar - only other title bar text getting in the way!

It's about choice - what's better: having the option to turn off the setting or being stuck one way or the other?

---

### Post by Fevrin on 2008-05-30
> **mozetti said:**
> It's about choice - what's better: having the option to turn off the setting or being stuck one way or the other?

It's better to have the option--but the default should probably be opaque, not transparent, and at the *least* this option should be in a more obvious place, like the Window Decorator settings of Compiz.

---

