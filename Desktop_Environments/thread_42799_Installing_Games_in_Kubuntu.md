---
title: "Installing Games in Kubuntu"
date: 2005-06-19
forum: Desktop Environments
---

### Post by SeanMC on 2005-06-19
Hi All,This may seem like a stupid question but I hope someone responds with an answer.

I have installed Kubuntu and am slowly coming to terms with it from Windows, however the problem I have is running games I have installed. I can find the games and install them using Kynaptic no problem - but then if they are not in the menu how do I run them, games like gnu-chess, quake, etc.

I can find references to the games in usr/games but when I click on them either nothing happens or they try to start and then dissapear.

Any help with this would be greatly appreciated!

---

### Post by Iuliux on 2005-06-19
there are 2 modes of installing games into linux:
1) to install games that are made for linux (quake, neverwinter knites, unreal t. 2004, etc)!
2) to install other games with cedega (this is an emulator) google it.

---

### Post by SeanMC on 2005-06-19
Thanks for the reply but that doesn't really answer my question, how do I get the games to run after I have installed them?

Which file is it that actually get them going?

---

### Post by cwaldbieser on 2005-06-19
Many times, if you can find the game program in /usr/games or /usr/bin or /usr/local/games or /usr/local/bin, you just need to open a terminal and type the name of the game.  For example:
```

$ pysol
```

If the game is not located in your path, you may need to type out the whole path:

```
$ /usr/games/pysol
```

If the game does not install a menu option for you, you can add the menu option yourself-- use the SMEG project for Ubuntu ([http://ubuntuforums.org/forumdisplay.php?f=67](http://ubuntuforums.org/forumdisplay.php?f=67)) or kmenuedit for Kubuntu.  Programs like kappfinder for Kubuntu will also help sometimes.

---

### Post by @jens on 2005-06-19
You can open a terminal and simply type the name (eg $ gnu-chess) and enter

or you have a look, where the game is installed (in (k)ubuntu games are located in /usr/games) and then:
right klick on the panel -> add -> special->non-kde->browse to /usr/games/"yourgame" -> klick on "yourgame"->apply->click on the "bogo icon" in the window->the icon menue appears->choose your icon for the game. 
After that you can click "windowish" on the icon on the panel and viola!

Regards,
@jens

---

### Post by ltmon on 2005-06-19
Many games are not well-integrated into the desktop.  They do not install menu shortcuts or desktop icons or anything like that :(.

In this case you often need to find the command to start the game yourself.

For quake open a terminal and type

$> quake

and then enter.

A good trick if you don't know the name is to type your best guess at the first letter or two and then "tab-tab".  This will list all possible commands beginning with that letter.  It makes finding "lost" commands much easier.

Another thing to do is to search for the home site for the game, which should provide instructions and command names in the documentation.

L.

---

