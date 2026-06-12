---
title: "link to game in start menu"
date: 2005-09-13
forum: Desktop Environments
---

### Post by tranquility base on 2005-09-13
I just installed the game, Chromium.  Now, how do I make a link with an icon to it in the Applications --> Games folder so that I can get to it quickly, as with the other games that are already installed?

Thanks in advance for helpful replies.

---

### Post by frodon on 2005-09-13
My way is to create a script to run your game like that : ```
cd the_repertory_where_the_game_is
cedega Chromium.exe -opengl
```Save this script where you want as Chromium.run for exemple and the run this command to make the script executable : ```
sudo chmod +x Chromium.run
```So running this script wiil launch the game.
All you have to do now is to install [smeg](http://ubuntuguide.org/#menu-editor) and then use it to create a shortcut (which will launch this script) where you want in the gnome menu.

---

### Post by cwaldbieser on 2005-09-13
[QUOTE=frodon]My way is to create a script to run your game like that : ```
cd the_repertory_where_the_game_is
cedega Chromium.exe -opengl
```Save this script where you want as Chromium.run for exemple and the run this command to make the script executable : ```
sudo chmod +x Chromium.run
```So running this script wiil launch the game.
All you have to do now is to install [smeg](http://ubuntuguide.org/#menu-editor) and then use it to create a shortcut (which will launch this script) where you want in the gnome menu.[/QUOTE]
chromium is available natively on Ubuntu, so you don't need to use cedega, but creating a script and linking that in the menu is still a valid option.

---

