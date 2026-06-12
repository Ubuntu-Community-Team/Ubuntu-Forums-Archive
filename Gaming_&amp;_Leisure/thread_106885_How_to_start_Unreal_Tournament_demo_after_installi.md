---
title: "How to start Unreal Tournament demo after installing it?"
date: 2005-12-21
forum: Gaming &amp; Leisure
---

### Post by Leigh on 2005-12-21
I successfully installed the demo version of Unreal Tournament ([http://videogames.yahoo.com/download?eid=332005](http://videogames.yahoo.com/download?eid=332005)) using the built-in script. It has a graphical install procedure which asked where it should be installed, etc. At the end of the installation it asked if I wanted to run the game. I answered "yes" and the game ran successfully. However, now I want to run the game again but I don't know what or how to start it. Could anyone help?

The files were installed in /usr/local/games/ut2004demo directory, but I'm not sure what I should be looking for to run the program.

---

### Post by oldgoat on 2005-12-21
Try taking a look around (alphabetically) in /usr/bin - if you find it you could make a link to it from your desktop or toolbar.

Try on the tool bar 'Places' 'Search for Files...' - chuck in unreal tournament and see what happens.

---

### Post by joshuapurcell on 2005-12-21
The command is **ut2004** from the command prompt. You can create a menu icon if you want using the Application Menu Editor.

---

### Post by Leigh on 2005-12-22
Thanks for the replies. Since I have the demo, the command is **ut2004demo**, trouble is I have to do a **sudo ut2004demo** to get it to run, so I shall have to find the correct permissions to assign.

Thanks again for your help.

---

### Post by joshuapurcell on 2005-12-23
That's weird... I have the demo as well and my command is ut2004. Also, I don't have to use sudo to run the command. I installed the game in the default location, which was my home directory.

---

### Post by Leigh on 2005-12-23
That is strange. The default directory for me was **/usr/local/games/ut2004demo**. I downloaded release 3120 as I couldn't get a later release version that was reliable - in other words, the downloads were corrupted.

---

### Post by nathan43081 on 2005-12-23
The problem wiht needing to run sudo is probably due to installing it as root or another user than you currently are. You can get this fixed by changing the owner on  both the install directory in /usr/local/games/ and also the settings directory that should be in your home directory. The settings directory is something like .ut004 or .ut2004demo. Good luck on getting things working.

---

