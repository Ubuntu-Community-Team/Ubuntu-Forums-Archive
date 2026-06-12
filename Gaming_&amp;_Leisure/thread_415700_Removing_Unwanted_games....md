---
title: "Removing Unwanted games..."
date: 2007-04-20
forum: Gaming &amp; Leisure
---

### Post by des4ij on 2007-04-20
Hey, I just upgraded to Fiesty... I was wondering if there is a way I can remove only certain games from gnome-games... Like I want to keep mines, sudoku, and chess and remove the other ones how can I do that... It wont let me do it through Application manager or Synaptic because they are all in the same package... Thank You

---

### Post by madmetal on 2007-04-20
i dont think its able to remove certain gnome games.. they are one package..
why really remove them? just ignore them if you dont like them...

---

### Post by lluisanunez on 2007-04-20
Yes they're in the same package
You can just remove them from the menu
System >> preferences >> menu layout

---

### Post by des4ij on 2007-04-20
> **madmetal said:**
> i dont think its able to remove certain gnome games.. they are one package..
why really remove them? just ignore them if you dont like them...

well idk i jsut wanna to free some space and make the games menu look neater... but i think i'll jujst remove the icons... thx

---

### Post by ysse on 2007-04-20
You can just hide the menu options you don't want to see: Right-click on the top menus to edit them, and uncheck your most unwanted items in the Game menu.

---

### Post by Bekker on 2007-04-20
Those games are probarly part of the "ubuntu-desktop" package. This is a dummy package depending on all the packages that get installed on a fresh install. So if you remove those games ubuntu-desktop will be broken so you'll have trouble updating to a new version of ubuntu (like gutsy gibbon in the future).
I'd suggest you just keep 'm, they don't take a lot of diskspace and you can remove them from the menu for a more clean look as suggested before.

---

### Post by Perfect Storm on 2007-04-20
In the terminal;
(will remove the default games in Ubuntu and the meta package as bekker descript)

```
sudo aptitude remove gnome-games gnome-games-data gnome-cards-data
```

---

