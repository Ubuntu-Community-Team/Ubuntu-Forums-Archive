---
title: "Get high score version of Gnometris"
date: 2009-02-08
forum: Desktop Environments
---

### Post by chenxiaolong on 2009-02-08
I just compiled the gnome-games package because it wouldn't install for some reason. I thought it would be fun to edit some of the source code, so I got rid of all the shapes and created a 4 x 2 shape to see if I could get a really high score. I got 2210000 points on level 12 and then lost. If anyone else wants to play just run the attached file (run "chmod +x gnometris" first then run "./gnometris"). The high score table and the preferences only work if you already have the original version of Gnometris installed. The high scores you get on this version will go to the original game's high score list. Please post back if you get a really high score!:D

---

### Post by chenxiaolong on 2009-02-08
By the way, here's the modified source code I used: [http://www.adrive.com/public/32a2825ccce3de4bfcc28026aef3555c221191551a50b3718eee15bf6a0e4921.html](http://www.adrive.com/public/32a2825ccce3de4bfcc28026aef3555c221191551a50b3718eee15bf6a0e4921.html). It's already compiled, but if you want to edit it, you can do so, then recompile it later (it needs a lot of prerequisite packages to compile and it works for every distro). I edited the blocks.cpp file to remove and change the shapes.

---

