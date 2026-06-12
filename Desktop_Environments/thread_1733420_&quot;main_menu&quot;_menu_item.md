---
title: "&quot;main menu&quot; menu item"
date: 2011-04-19
forum: Desktop Environments
---

### Post by shukalo83 on 2011-04-19
Hello.

When I click "System>Preferences>Main Menu" nothing happens.

I am running Lucid 64bit.

Can you help me with this please?

---

### Post by Frogs Hair on 2011-04-19
Hi and welcome 

I don't know the cause of the problem . Try to right click the menu text and select edit menus and see if it opens that way. If it does try the menu icon again.

---

### Post by Copper Bezel on 2011-04-19
Also, try running alacarte from terminal (that's the main menu editor app itself.) If it runs, we can change the item for Main Menu itself. If it doesn't, we'll troubleshoot from there.

---

### Post by shukalo83 on 2011-04-20
> **Copper Bezel said:**
> Also, try running alacarte from terminal (that's the main menu editor app itself.) If it runs, we can change the item for Main Menu itself. If it doesn't, we'll troubleshoot from there.

Right click methot did not help. Nothing happened. Alacart did work but as "sudo alacarte". Maybe there lies the problem?
With sudo alacarte I managed to edit some stuff in menu so I can consider this tread solved.

Thank You.

---

### Post by Copper Bezel on 2011-04-20
Whoa, that's fairly weird. Your menu should *not* be owned by root. Does anyone know where this data is stored?

---

### Post by Krytarik on 2011-04-20
> **Copper Bezel said:**
> Whoa, that's fairly weird. Your menu should *not* be owned by root. Does anyone know where this data is stored?
The menu setup is stored in "~/.config/menus", the *.desktop files specified in it are in "~/.local/share/applications".

Also, I would expect that you change the menus of 'root' if you invoke "sudo".

---

