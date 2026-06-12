---
title: "Gnome Menu dirs"
date: 2005-05-11
forum: Desktop Environments
---

### Post by Linforcer on 2005-05-11
It's all nifty the way it's explained everywhere how to add launchers to the existing menus, but I want to manipulate the directories themselves. can anyone tell me how to do it?

---

### Post by Zelut on 2005-05-11
Sounds like you're looking for the gnome menu editor.  Give this a try...

[http://www.ubuntuguide.org/#menu-editor](http://www.ubuntuguide.org/#menu-editor) (install gnome menu editor)

I have no idea why that isn't installed by default...

---

### Post by Linforcer on 2005-05-11
NO, in fact I am not looking for that. I have that. It enables me to create launchers in the dirs that are already in the applications menu.

What I DO want is to manipulate (rename, add, delete) the specific directories witin te Applications wenu.

---

### Post by Alexander Kirillov on 2005-05-11
[QUOTE=Linforcer]NO, in fact I am not looking for that. I have that. It enables me to create launchers in the dirs that are already in the applications menu.

What I DO want is to manipulate (rename, add, delete) the specific directories witin te Applications wenu.[/QUOTE]
 I do not think there is a graphical tool for it - but you can try manually editing corresponding files.

---

### Post by Linforcer on 2005-05-11
*slaps forehead*
*sigh*
Yes, I realize I can do that but what I want to know is WHAT files >.>
I see *.directory files but simply creating them doesn't add them to the menu.

---

### Post by Zelut on 2005-05-11
Sounds like you're getting a little frustrated... I hope we're not making things worse for you  ;-) 

if you've created / edited the .desktop files you will need to restart the gnome-panel for them to show up.  Now you may have already done this but have you run 

# killall gnome-panel

to refresh the panel with any changes you've made?

---

### Post by Linforcer on 2005-05-11
I 'm sorry it was my fault for being unclear :P

but the thing is that I want to create a subsub directory. I want to split Applications > Games   into gnome games and other games

Either way if I cant do that I want to at least just make a Applications > Other games
or something.

Anyway simply creating a *.desktop file in /usr/share/desktop-directories/ is not enough, and yes, I did kill the panel like that after creatdng the desktop file

(yay, I got a cup of ubuntu now xD)

---

### Post by Alexander Kirillov on 2005-05-11
[QUOTE=Linforcer]*slaps forehead*
*sigh*
Yes, I realize I can do that but what I want to know is WHAT files >.>
I see *.directory files but simply creating them doesn't add them to the menu.[/QUOTE]
 Sorry for confusion. You'll need to edit file 
/etc/xdg/menus/applications.menu
which describes the structure of applications menu. Its structure is somewhat confusing; basically, it is a list of all entries that should appear in Applicatins menu. For each submenu, it gives name and list of criteria which applications should be included in the submenu. Note that the actual list of applications is created dynamically, by scanning the list of all .desktop files for all  apps and determining whether a given app satisfies the criteria for inclusion in given submenu. 


Full documentation is here: 
 [http://standards.freedesktop.org/menu-spec/0.9/ar01s04.html](http://standards.freedesktop.org/menu-spec/0.9/ar01s04.html)

---

### Post by Linforcer on 2005-05-11
Thank you!
 I sort of figured the list was created like that looking at the "code" in the .desktop files. I'm sure I'll find out how to do waht I want now ^^

Me love you long time.

---

### Post by Linforcer on 2005-05-12
Well, I succeeded.

Though now the Menu editor does not work because it feels my applications.menu isn't a valid menu file. (perhaps it wasn't designed to handle deeper submenus or maybe I've been sloppy)

The Games section now says:

```
<!-- I split the Games menu into the smaller Games that 
   come with Gnome and the bigger (better) ones I installed
   I create .desktop files myself witd the "Othergame category>

  <!-- Games -->
  <Menu>
     <Name>Games</Name>
     <Directory>Games.directory</Directory>

     <!-- Gnome Games -->
     <Menu>
       <Name>Games/Gnome Games</Name>
       <Directory>GnomeGames.directory</Directory>
       <Include>
         <And>
           <Category>Game</Category>
         </And>
       </Include>
     </Menu> <!-- End Gnome Games -->
   
     <Menu>
       <Name>Games/Other Games</Name>
       <Directory>Othergames.directory</Directory>
       <Include>
         <And>
           <Category>Othergame</Category>
         </And>
       </Include>
     </Menu> <!-- End Other Games -->
  </Menu> <!-- End Games>
```

---

### Post by Alexander Kirillov on 2005-05-12
[QUOTE=Linforcer]Well, I succeeded.

Though now the Menu editor does not work because it feels my applications.menu isn't a valid menu file. (perhaps it wasn't designed to handle deeper submenus or maybe I've been sloppy)
[/QUOTE]

You made a mistake in closing comments. Comments should end with -->, not just >

---

