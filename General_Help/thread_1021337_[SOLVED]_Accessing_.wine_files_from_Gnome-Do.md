---
title: "[SOLVED] Accessing .wine files from Gnome-Do"
date: 2008-12-25
forum: General Help
---

### Post by Valok on 2008-12-25
So I'd like to be able to launch games like World of Warcraft right from gnome-do rather than having a launcher for it.  The only problem is that gnome-do can't seem to find / access any of my WINE files.  Is there some setting I have to play with, or something I have to change to make this possible?

Thanks in advance!

---

### Post by Valok on 2008-12-29
Any tips?

---

### Post by Ng Oon-Ee on 2009-01-04
If you just create a launcher (*.desktop) in your ~/.local/share/applications folder, gnome-do will pick it up when its restarted, and you can launch it using whatever name you put into the 'name' field of the launcher.

The execute line of the launcher should go something like "env WINEPREFIX=*your_wine_prefix* wine *your executable*.exe". If you want specific syntax, tell me how you're currently running your app, and I'll see what I can do to help.

---

### Post by Valok on 2009-01-05
Thanks for the suggestion!  I'll give it a try when I get home, I should be able to figure out the specific syntax as I've made a few other launchers.

Thanks again!

---

### Post by Ng Oon-Ee on 2009-01-05
> **Valok said:**
> Thanks for the suggestion!  I'll give it a try when I get home, I should be able to figure out the specific syntax as I've made a few other launchers.

Thanks again!
You're welcome. Please remember to mark [solved] if it is, etc. etc.

---

### Post by BennBuntu on 2009-01-05
I don't know gnome-do, but for launching steam games, I make a simple script, then put it in /usr/local/bin . Then can launch like any other app.

here's my portal script

```
#!/bin/bash

cd ~/.wine/drive_c/Steam/
WINEDEBUG=fixme-all wine Steam.exe -fullscreen \
    -width 1280 -height 800 -dxlevel 80 -applaunch 400 \
    +map_background none "$@"
```

make sure it's executable and you're set. Make one for each game.

---

### Post by Ng Oon-Ee on 2009-01-05
> **BennBuntu said:**
> I don't know gnome-do, but for launching steam games, I make a simple script, then put it in /usr/local/bin . Then can launch like any other app.

here's my portal script

```
#!/bin/bash

cd ~/.wine/drive_c/Steam/
WINEDEBUG=fixme-all wine Steam.exe -fullscreen \
    -width 1280 -height 800 -dxlevel 80 -applaunch 400 \
    +map_background none "$@"
```

make sure it's executable and you're set. Make one for each game.
Thing is, gnome-do can execute such scripts if they're in some /bin folder, but it'll only show a generic 'script' icon depending on your theme.

Creating a launcher (.desktop) in the appropriate ../applications folder means you can launch the app and have a nice recognizable icon in gnome-do when the appropriate shortcut is selected.

My personal preference (esp with complicated programs with plenty of options) is to have a launcher which points to a script. But not many people are that anal-retentive I guess.

---

### Post by DavidONE on 2009-01-31
A simpler method is to activate the Files and Folders plugin and then add '$HOME/.local/share/applications/wine/Programs' and give it a depth of something like '4' to index everything.

[https://answers.launchpad.net/do/+question/37824](https://answers.launchpad.net/do/+question/37824)

---

