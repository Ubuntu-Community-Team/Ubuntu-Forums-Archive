---
title: "Search in application menu"
date: 2010-10-06
forum: Desktop Environments
---

### Post by vibrunazo on 2010-10-06
In KDE the main application menu had this really nice and useful search box that I would type the name of the application and press enter to open it. Now that I changed to ubuntu with gnome, there's no search box at the Applications menu by default. And I cannot find anyway to add it anywhere.

Is there any way to add a KDE style search box to the Gnome "Applications" menu?

---

### Post by sanderd17 on 2010-10-06
not KDE style, but gnome-do gives the same functionality.

```

sudo aptitude install gnome-do

```

You can give a shortcut to it to easy execute apps.

---

### Post by vibrunazo on 2010-10-06
I liked it, thanks a lot :)

---

### Post by sanderd17 on 2010-10-06
I just came across something more like the KDE search bar. If you want to view it: [http://www.elementary-project.com/forum/viewtopic.php?f=4&t=105]("http://www.elementary-project.com/forum/viewtopic.php?f=4&t=105")

The installation instructions don't work anymore, the apt-rule has changes. Use

```

sudo add-apt-repository ppa:cardapio-team/unstable
sudo apt-get update
sudo apt-get install cardapio

```

instead.

---

### Post by sanderd17 on 2010-10-06
Oh sorry, forgot to mention, you need to add cardagio to the panel by right clicking on the panel (not on a widget) and selecting "add to panel". Then search for cardagio, check it and remove the old menu from the panel afterwards.

---

