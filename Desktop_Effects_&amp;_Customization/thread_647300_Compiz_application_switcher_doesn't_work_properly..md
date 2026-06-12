---
title: "Compiz application switcher doesn't work properly."
date: 2007-12-22
forum: Desktop Effects &amp; Customization
---

### Post by Monkbel on 2007-12-22
1. If I set "Visual Effects" to "None", disabling compiz, default application switcher works fine.

2. If I switch to "Extra" or "Custom", compiz starts working. When I click Alt-Tab, all thumbnails are totally white. (see attached screenshot).

3. If I enable or disable Ring Switcher and Shift Switcher in any combinations, nothing changes - switcher looks the same.

4. Alt-Shift-Tab doesn't work. If I go to Application Switcher -> Actions -> Prev Window, I see "Disabled" in key. It's impossible to set something there (using "New accelerator..." or via double-click).

My system is up-to-date. Thanks for your help :)

---

### Post by Monkbel on 2007-12-22
the problem with white thumbnails was solved after restart. problems under 3. and 4. persist :(

---

### Post by Monkbel on 2007-12-22
ok I managed to fix 3. - I found out that by default those switchers react to super+tab rather than alt+tab

and i fixed 4. - writing <Alt><Shift><Tab>. 

thanks :)

---

### Post by Digital Ninja on 2007-12-24
Hi, didnt wanna open a new thread for this short question..

I cant seem to find an information, how can i restart Compiz? Sometimes it stops working and somehow i lose all the effects, cube, app switcher, wabbely windows - everything! Is there something i can write thru the Terminal so that it restarts?

---

### Post by ronmarley1 on 2007-12-24
> **Digital Ninja said:**
> Hi, didnt wanna open a new thread for this short question..

I cant seem to find an information, how can i restart Compiz? Sometimes it stops working and somehow i lose all the effects, cube, app switcher, wabbely windows - everything! Is there something i can write thru the Terminal so that it restarts?

```
compiz --replace
```

---

