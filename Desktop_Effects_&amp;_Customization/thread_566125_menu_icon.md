---
title: "menu icon"
date: 2007-10-03
forum: Desktop Effects &amp; Customization
---

### Post by ferronica on 2007-10-03
can anyone please tell me how to change main menu icon i tried lot nothing happend changing distributor-logo.png or replacing ot help :(

---

### Post by Eman64 on 2007-10-06
Run
```
gconf-editor
```
Go to "apps >> panel >> objects", find the object thats tooltip is "Main Menu", enter the location of the icon you want to use into the custom icon field, check the box at that says "use_custom_icon" and then you should be good.
If the icon doesn't show up at first you may have to use this command
```
killall gnome-panel
```

Goodluck,
Emmett

---

