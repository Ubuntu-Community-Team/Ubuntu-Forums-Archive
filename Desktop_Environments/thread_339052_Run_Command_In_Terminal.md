---
title: "Run Command In Terminal?"
date: 2007-01-15
forum: Desktop Environments
---

### Post by hammackj on 2007-01-15
Hello,

My question is simple, I am trying to change the default window size of the gnome-terminal to 80x25, i can modify the shortcuts and wrapper file to do it but my custom menu items that use the Run Command In Terminal check do not read those files/settings. 

Does anyone know where or how to change the absolute default terminal size? 

I have found the code that changes this on line 1811 of terminal-window.c but I am curious to know if there is a less hackish way to fix this.


Thank you,

hammackj

---

### Post by mcduck on 2007-01-15
You could use something like this in a laucher: 'gnome-terminal --geometry 46x18'

Alternatively you can use 'gnome-terminal --geometry 46x18-65+50' to also set the position of the terminal window.

To get a geometry line resize the terminal to the size you want and move the window where you want it to appear, and run 'xwininfo' in a terminal & click on the terminal window. It will output a lot of info about the terminal window, and the geometry appears around the end of the output.

---

### Post by hammackj on 2007-01-15
that does not make a perm change to the launch. 

the launch icon and the "launch in terminal" option from the menu editor call different instances of gnome terminal.

editing the code fixed the problem for me, hopefully a later release will offer external settings for terminal window size in gconf or something.


thanks

---

