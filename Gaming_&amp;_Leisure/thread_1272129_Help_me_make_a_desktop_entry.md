---
title: "Help me make a desktop entry"
date: 2009-09-21
forum: Gaming &amp; Leisure
---

### Post by joeelmex on 2009-09-21
I am trying to make a Doom3 Desktop entry for my ubuntu menu.  I can load the game fine without a glitch from the terminal.  I now want to make an icon under games but so far I get a little circle thats its trying to load but nothing happens.  I also did chmod x doom3 command to make it executable but that did not help.  This is what I have;

```

[Desktop Entry]
Encoding=UTF-8
Name=Doom3
GenericName=Doom3
Comment=FPS 
Exec=/home/joeelmex/Games/Doom3/doom3
StartupNotify=true
MultipleArgs=true
Type=Application
Categories=Games

```

---

### Post by rCXer on 2009-09-21
This usually works for me...

```

[Desktop Entry]
Name = game
Comment = Description of game
Exec = /path/game
Icon = game-icon.png
Terminal = false
Type = Application
Categories = Application;Game;

```

Maybe you need "Terminal = false"

---

### Post by j7%&lt;RmUg on 2009-09-22
If you look at the freedesktop specs then you will notice you need this:

```

Version=1.0

```

It should go straight under: [Desktop Entry]

---

### Post by joeelmex on 2009-09-22
nisshh where can I find "freedesktop specs" ?  

Thanks

---

### Post by Bölvaður on 2009-09-22
I dont know what commands you used, which would be a good thing to know while helping you.


(for GNOME)
Right click on Applications (on the panel) and then on Edit Menus.
Browse to the place you want the launcher to be (most probable under Games), then click "+ New Item" and have the command exactly the same as the command you used to get it to work. That might not work though, so copy (click on it in nautilus and ctrl+c on it) the file that you are supposed to run and paste it into the command.

Did that work? Yes? now it is popcorn time :popcorn:

---

### Post by rCXer on 2009-09-22
> **Bölvaður said:**
> I dont know what commands you used, which would be a good thing to know while helping you.


(for GNOME)
Right click on Applications (on the panel) and then on Edit Menus.
Browse to the place you want the launcher to be (most probable under Games), then click "+ New Item" and have the command exactly the same as the command you used to get it to work. That might not work though, so copy (click on it in nautilus and ctrl+c on it) the file that you are supposed to run and paste it into the command.

Did that work? Yes? now it is popcorn time :popcorn:

I guess that's probably the easier (and better) way to do this.  I'll have some as well :popcorn:

---

