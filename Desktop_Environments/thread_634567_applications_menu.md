---
title: "applications menu"
date: 2007-12-07
forum: Desktop Environments
---

### Post by monoufo on 2007-12-07
ok, so we all have the wonderful gnome applications menu, which somehow keeps everything nice and organized on its own.  I don't access mine directly, I use an awn applet to access the main menu.

Any ways, I want to know how to move things around and make short cuts to new programs and things like that. It takes 6 clicks to launch a windows game under wine, and it should take only 3.  I want to copy the icon for the windows game to the game section.  I know where the start menu is on windows, but can't find it for gnome.

---

### Post by conehead77 on 2007-12-07
right click on the application menu, then select "edit menu"
click on the "games" menu on the left
click on "new entry" on the upper right
for "name" you can choose the name you want
the command would be sthg like "wine ~/.wine/etcetc/your_game.exe" for a game with wine. i dont know the exact path, but you will know it as you already started the game before

i hope this is what you were looking for

---

### Post by monoufo on 2007-12-07
I was hoping there was another way to do it, maybe a manual method.  In order to use that method, I'd have to open up a gnome-panl and add the menu.  My applet doesn't support rightclicking.

---

### Post by conehead77 on 2007-12-07
i searched a little about editing menus. i guess you need to create a file in /usr/share/applications , but im just guessing :)

take a look at this thread: [http://ubuntuforums.org/showthread.php?t=346869](http://ubuntuforums.org/showthread.php?t=346869)
especially post #16

im going to bed now, so good luck!

---

### Post by monoufo on 2007-12-08
thank you, that post 16 really helped.  I know a little bit about /usr/share/applications, but I hadn't found ~/.local/share/applications before, and didn't understand the catergories system.  

All i had to do was find the .desktop file in the above directory, and add Categories=Game;  

that's much easier than creating a new .desktop file. I can recategorize all my wine apps now.  I also figured out how to get a file browser link by unhiding it.

---

