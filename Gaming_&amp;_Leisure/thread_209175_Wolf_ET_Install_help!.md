---
title: "Wolf ET Install help!?"
date: 2006-07-04
forum: Gaming &amp; Leisure
---

### Post by NJboi21 on 2006-07-04
Hi, I am new to gnome so I have a problem with installing a linux game.

Problem:

The game is a linux game called Wolfenstien ET, I downloaded it and the extension is    called .run but Ubuntu has an error when I try to run it, an extractor program comes up and has errors, how to u install a .run game is my real question 

THANKS
NJboi21

---

### Post by dresnu on 2006-07-04
check this thread [http://www.ubuntuforums.org/showthread.php?t=196246](http://www.ubuntuforums.org/showthread.php?t=196246) if it can help you.

---

### Post by pharcyde on 2006-07-04
Check these links out.  They may be able to help you.

[http://help.ubuntu.com/community/Games/Native/ReturnToCastleWolfensteinEnemyTerritory](http://help.ubuntu.com/community/Games/Native/ReturnToCastleWolfensteinEnemyTerritory)
[http://help.ubuntu.com/community/EnemyTerritory](http://help.ubuntu.com/community/EnemyTerritory)

---

### Post by B0rsuk on 2006-07-05
You didn't make it clear what kind of error you get. If you get an error while trying to run it, check links above. But if you have problem with 'extraction failed' ....
**Here's the fix**

The problem with installer is caused by fact that by default linux uses /tmp directory to store temporary files (like when unpacking something). Before contents of archive are moved to right directory, they stay for a while in /tmp dir. **The problem arises because this particular archive/installer is very big, and may not fit into your /tmp directory.**
To remedy that, use:
```
./File_Name_Of_ET_Installer --target /directory/where/you/wish/it/installed
```
And it should be done. That's how I fixed it.

I have a habit of installing binary/third party games in my /home/b0rsuk/Gry directory.
-------
By the way: as far as I remember, you can read about the --target option by running et installer with --help option.

---

