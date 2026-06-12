---
title: "Gnome 3 Instant Message Indicator"
date: 2011-10-25
forum: Desktop Environments
---

### Post by Frogs Hair on 2011-10-25
I would like to remove the instant messenger indicator from the Gnome Shell since I don't use it. I have searched synaptic and the web , but I don't know the package name . Without an IM account enabled the red unavailable indicator appears all the time . If there is another way to disable it that would be great as well . Thanks for your help !

---

### Post by cbowman57 on 2011-10-25
There used to be an noim extension but I don't know if there is currently one that works for gnome 3.2

---

### Post by Frogs Hair on 2011-10-25
> **cbowman57 said:**
> There used to be an noim extension but I don't know if there is currently one that works for gnome 3.2

I found a tar.gz of that package , but it is not included in my extension PPA . It is also being updated .

---

### Post by cbowman57 on 2011-10-25
I'm not certain if it's being updated or not, it seems they made a lot of changes to the panel*.js files in 3.2

If you are willing to live without your user menu you could comment out the userMenu entry in panel.js, around line 36 ```
const STANDARD_STATUS_AREA_SHELL_IMPLEMENTATION = {
    'a11y': imports.ui.status.accessibility.ATIndicator,
    'volume': imports.ui.status.volume.Indicator,
    'battery': imports.ui.status.power.Indicator,
    'keyboard': imports.ui.status.keyboard.XKBIndicator,
   /* 'userMenu': imports.ui.userMenu.UserMenuButton */
```but you might miss some of the other functions.

---

### Post by Frogs Hair on 2011-10-25
Thanks , but I can live with the little red X until another solution comes along . I was hoping it was package I could remove without affecting the rest of the applet .

---

### Post by cbowman57 on 2011-10-25
I'm certain there is a way to do it but it's beyond my abilities. :)

---

### Post by crdlb on 2011-10-25
Red? With no telepathy accounts, I get an unobtrusive dark gray talk balloon icon with a black X.

What icon theme are you using?

---

### Post by Frogs Hair on 2011-10-25
> **crdlb said:**
> Red? With no telepathy accounts, I get an unobtrusive dark gray talk balloon icon with a black X.

What icon theme are you using?

Awoken

---

### Post by Frogs Hair on 2011-10-25
Problem solved by switching to Faenza Wolfe icon theme . Thanks crdlb !! :)

---

