---
title: "Good news for theme customization?"
date: 2012-09-05
forum: Desktop Environments
---

### Post by vasa1 on 2012-09-05
[http://www.webupd8.org/2012/09/customize-gtk3-gtk2-theme-colors-using.html](http://www.webupd8.org/2012/09/customize-gtk3-gtk2-theme-colors-using.html)

And here's a link to Satya's intro: [http://worldofgnome.org/customizing-gtk-themes-just-got-easier/](http://worldofgnome.org/customizing-gtk-themes-just-got-easier/)

---

### Post by uRock on 2012-09-05
Not a support request. Moved to ***Desktop Environments***.

---

### Post by Toz on 2012-09-05
Sure is a nice step forward. Editing the gtk files by hand is cumbersome. It needs to mature quite a bit to cover all of the different gtk widgets and elements. Maybe even start to address application-specific settings.

The challenge will be that gtk is a moving target.

---

### Post by vasa1 on 2012-09-06
> **Toz said:**
> Sure is a nice step forward. Editing the gtk files by hand is cumbersome. It needs to mature quite a bit to cover all of the different gtk widgets and elements. Maybe even start to address application-specific settings.

The challenge will be that gtk is a moving target.

Have you tried it? I'm going to give it a shot ASAP!

As for the moving target bit, I get the impression that they (?) are trying to move to conventional CSS and default "engines". I hope that's a good thing.

---

### Post by vasa1 on 2012-09-06
Installed it.

Right now, there's no provision to select the theme to be modified. I'm assuming it will act on the currently active theme.

---

### Post by vasa1 on 2012-09-06
I just tried it. The settings are saved to ~/.gtkrc-2.0. Since I don't have anything in my ~/.gtkrc-2.0, I had no problem when I reverted because this file was deleted.

---

### Post by Toz on 2012-09-06
> **vasa1 said:**
> I just tried it. The settings are saved to ~/.gtkrc-2.0. Since I don't have anything in my ~/.gtkrc-2.0, I had no problem when I reverted because this file was deleted.

Just ~/.gtkrc-2.0? Nothing to ~/.config/gtk-3.0/ ? That would mean its gtk-2 compliant only.
I'll have to give this a try tonight when I have some free time.

---

### Post by vasa1 on 2012-09-06
> **Toz said:**
> Just ~/.gtkrc-2.0? Nothing to ~/.config/gtk-3.0/ ? That would mean its gtk-2 compliant only.
I'll have to give this a try tonight when I have some free time.
@Toz, that was my hurried look. Also, I noticed that to get things back completely, I had to reboot, not just log out, log in.
Overall, as you said earlier, the options are quite minimal and since I've already gotten used to digging deep, I won't be needing this for some time.

---

