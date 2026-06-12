---
title: "Is there a guide for changing just specific icons, not the whole icon set?"
date: 2007-03-31
forum: Desktop Effects &amp; Customization
---

### Post by rainwalker on 2007-03-31
I really like the default Human icons, but there are a few I want to change. The problem is, some of them seem to only change when I go into the theme manager and choose a different icon set. It's really annoying, because there are icons I like and ones I don't like.

So is there a guide/howto for changing icons (like the logout/power button one), or does anyone have any advice as to how I should do it?

---

### Post by jlk on 2007-04-02
If you have a look at an Icon theme, say Human in /usr/share/icons/Human you will find a icon-theme.cache file which needs to be updated when you change a icon.  Well this is almost true, since it appears that if you change an icon in "your favorite theme"/scalable/....  you don't need to update the icon-theme.cache file.

Having said that, I changed one of the .png icons and couldn't get to display until I  found the
gtk-update-icon-cache command. Man will tell  you more, but basically after you change an icon run

```
sudo gtk-update-icon-cache –force /usr/share/icons/Human
```

enjoy

---

