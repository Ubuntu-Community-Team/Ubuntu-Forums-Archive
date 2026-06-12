---
title: "compiz help"
date: 2008-01-11
forum: Desktop Environments
---

### Post by n0greenfx on 2008-01-11
how ocme i dont have the custom option on my apearence pane so i can enable desktop cube etc????

---

### Post by PeterJS on 2008-01-11
Have you tried using the Compiz Config Settings Manager (System > Prefereces > Advanced Desktop Settings) to enable more effects?

---

### Post by n0greenfx on 2008-01-11
i dont have the advanced desktop settings option

---

### Post by PeterJS on 2008-01-12
Well then, let's install it:
```

sudo apt-get install compizconfig-settings-manager

```
While you're doing that you might want to check if compiz is installed as well, can't hurt.

---

### Post by n0greenfx on 2008-01-12
ok now i have it enable descktop cube and its not doing anything i have 4 desktops applyed and also set vertical and horizontal to 3 in the genral settings manager when i hit cnrtl alt and and arrow key nothing happens

---

### Post by n0greenfx on 2008-01-12
fire works when i hit super shift click so compize is working just not the cube

---

### Post by PeterJS on 2008-01-12
I assume you have the desktop cube plugin enabled? The rotate cube plugin is also useful. I've never tried to do a cube with a vertical size of anything other than 1.

---

### Post by n0greenfx on 2008-01-12
success i got it lol

now i gotta try and theme this thing any suggestions on themeing easy program to do so

---

### Post by PeterJS on 2008-01-12
The theming engines are built in, GTK controls the widgets, and Emerald controls the window borders and title bars. Emerald themes can be found here:
[http://themes.beryl-project.org/](http://themes.beryl-project.org/)
[http://gnome-look.org/index.php?xcontentmode=102](http://gnome-look.org/index.php?xcontentmode=102)
[http://gnome-look.org/index.php?xcontentmode=103](http://gnome-look.org/index.php?xcontentmode=103)
And GTK2 themes can be found here:
[http://gnome-look.org/index.php?xcontentmode=100](http://gnome-look.org/index.php?xcontentmode=100)

To change the Emerald theme the emerald theme manger is the tool of choice, it can be found at System > Preferences > Emerald Theme Manager.

To change the GTK theme. System > Preferences > Appearances > Customize > Controls (which is the default tab)

---

### Post by n0greenfx on 2008-01-12
when i download these files such as [http://gnome-look.org/content/show.php/Zafir?content=73390](http://gnome-look.org/content/show.php/Zafir?content=73390)

i import it into emreald now how do i apply the theme??

---

### Post by PeterJS on 2008-01-12
You should be able to just select them from that big old list and be good. If that doesn't work open up a terminal and run:
```

ps aux | grep -v grep | grep emerald

```
If nothing shows up that's because emerald isn't working, and you'll need to go look at the window decorator plugin.

---

### Post by n0greenfx on 2008-01-12
ya that command does nothing

---

### Post by n0greenfx on 2008-01-12
i deselected the window decorator from the compiz custom menu now i have no little x button or minimize\maximize button at the top right and ereald sit doesnt apply themes and the command does nothing

---

### Post by PeterJS on 2008-01-12
Having the window decorator plugin enabled is kinda important, the window decorator plugin is supposed to start emerald. On the window decorator setting page there's an option that says command, it should be set to **emerald --replace**. See if that gets it to work. If not you can manually start emerald from the run dialog with the same command.

---

### Post by n0greenfx on 2008-01-13
ok i got emerald to work thanks alot man

---

