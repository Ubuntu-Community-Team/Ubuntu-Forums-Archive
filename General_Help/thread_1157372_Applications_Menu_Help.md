---
title: "Applications Menu Help"
date: 2009-05-12
forum: General Help
---

### Post by dphoenixa on 2009-05-12
Ever since I did updated ubuntu to the latest kernal. My application menu shows that I have no applications. It drops and only giving me a sliver of open space. The "Place" menu and "System" menu opens just fine. Is there a way to fix this?

---

### Post by baseface on 2009-05-12
right click on it and select "edit menu" or something like that.

---

### Post by dphoenixa on 2009-05-12
Nothing shows up when I clock edit menu.

---

### Post by stoneage on 2009-05-12
Have you tried looking in System -> Preferences -> Main Menu ?

If there is nothing listed there you could try adding entries.

---

### Post by mazz0 on 2009-05-12
Have you checked in Synaptic that everything's still installed?  Just a guess: you could try selecting a program in Synaptic and telling it to re-install, see if that helps?

---

### Post by dphoenixa on 2009-05-12
Going to System > Preferences > Main Menu does the same as edit menu...nothing.

I keep getting partial upgrade a half hour after I am on my computer even and when I press the "Start Upgrade" it just crashes.

---

### Post by dphoenixa on 2009-05-14
```

mv ~/.config/menus/applications.menu ~/.config/menus/applications.menu.bak

```

That is what did it. My applications came back. YAY!

---

### Post by drdenim on 2009-05-20
wow...that worked perfectly.  This is probably the easiest fix I've ever had to make...heh...Thanks

---

