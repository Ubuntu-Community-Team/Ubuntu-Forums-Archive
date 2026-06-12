---
title: "Customize the lightdm login dialog?"
date: 2015-08-30
forum: Desktop Environments
---

### Post by chaaderf on 2015-08-30
Hello dear *buntu users!

I've tried to customize my Lubuntu 14.04.3 login screen (lightdm). I've found (and succeed) how to change the wallpaper. But is there a way to change some specs of the login field section too? I mean where there is the drop down menu for user selection and password field? What I'm looking for is the opacity tuning of the whole section, and probably the position on the screen. But it seems I can't find tutorials for that by google (maybe I don't know the correct term/word which to use?), so perhaps someone could help a little bit? Thank you!

---

### Post by Dennis N on 2015-08-30
I'm not aware that you can change the opacity of the login window, but the window position can be set by adding a line in the [greeter] section of:
**/etc/lightdm/lightdm-gtk-greeter.conf** like this:

```
position=50%,center 40%,center
```

Here, **50%,center** is horizontal position, **40%,center** is vertical position. Percentages are measured from left and top edges of the screen. Other values in the [greeter] section can also be modified to suit your preferences - theme, font, clock, etc.

---

### Post by chaaderf on 2015-09-01
Hmm... Thank you! ^^ Perhaps I'll need to think about these things little bit now.

---

