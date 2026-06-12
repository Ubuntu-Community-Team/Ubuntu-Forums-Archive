---
title: "Blackbox on feisty fawn"
date: 2007-04-30
forum: Desktop Environments
---

### Post by rustysail on 2007-04-30
Hey guys

I'm trying to install blackbox on feisty as a fun project but I'm having issues. Everything seems to be working except for the menu.

When i right click on the desktop all I get is xterm; restart; exit.
I tried creating a .blackboxrc in my home folder and directing it to a menu file at .blackbox/menu.

Does anyone have any suggestions?
Thanks,
Rusty

---

### Post by Sally on 2007-05-16
I'm having the same issue: I didn't have a config file and attempts to create one failed. Does anyone have a (very basic) step-by-step for getting this set up?

---

### Post by RedSquirrel on 2007-05-18
Hmm. I'm not sure how the menu is setup in Blackbox, but it's possible you'll get something from running:

```
sudo update-menus
```

on the command line.

Is there a special reason you're using Blackbox? Development has stopped on it. You might enjoy Fluxbox instead since it's in active development.

```
sudo apt-get install fluxbox
```

---

### Post by Harii on 2007-06-11
i think - lighter is better. Who needs all that eye candy.
We need a blackbuntu

---

### Post by ynnhoj on 2007-06-11
you're probably better off with openbox, or maybe fluxbox or pekwm.

i take it you've read the [official documentation](http://blackboxwm.sourceforge.net/BlackboxDocumentation#OfficialDocumentation) already?

---

