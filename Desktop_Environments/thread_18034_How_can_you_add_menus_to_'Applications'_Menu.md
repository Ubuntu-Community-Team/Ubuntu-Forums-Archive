---
title: "How can you add menus to 'Applications' Menu?"
date: 2005-03-04
forum: Desktop Environments
---

### Post by Jonathan_ on 2005-03-04
This may sound like a stupid question, but I've looked and cannot see a way to do this:

I want to add an extra 'menu' when you click 'Applications' at the top. Eg 'Website Design software' and then links to various programs within that. How can you do this?

Thanks!

---

### Post by cka on 2005-03-04
If you're still in Warty, go to the run dialog and type "nautilus Applications:///" and you *should* be able to add sub-menus from that.

---

### Post by delltony on 2005-03-04
[QUOTE=Jonathan Steel]This may sound like a stupid question, but I've looked and cannot see a way to do this:

I want to add an extra 'menu' when you click 'Applications' at the top. Eg 'Website Design software' and then links to various programs within that. How can you do this?

Thanks![/QUOTE]
It is a little more complicated now and hopefully they change it in gnome for hoary. Cause i'm assuming your using hoary. the method the other guy posted with application:/// will not work in hoary.

Hoary instructions;
  sudo gedit /etc/xdg/menus/application.menu

you will have entries much like this 
```

<!-- Games -->
  <Menu>
    <Name>Games</Name>
    <Directory>Games.directory</Directory>
    <Include>
      <And>
        <Category>Game</Category>
      </And>
    </Include>
  </Menu> <!-- End Games -->

```

simple add yours like
```

<!--Web Development-->
   <Menu>
    <Name>Web Development Tools</Name>
    <Directory>Webdesign.directory</Directory>
    <Include>
         <And>
            <Category>WebDesign</Category>
         </And>
     </Include>
    </Menu> <!---End of webdesign entry -->

```

now you have to find on your pc where the directory files are do a search for like game.directory.

once you find it make a new file Webdesign.directory and put it there.
then add something like this to it
```

[Desktop Entry]
Encoding=UTF-8
Name=WebDesign
Icon = apple-green

```

now you have a menu item setup with a icon and name and category now to add stuff inside that menu you have to make a desktop file
make a file called webdesign.desktop in the /usr/share/applications folder
put this in there 
```

[Desktop Entry]
                 Encoding=UTF-8
                 Name=My cool webdesign tool
		Comment=media player
		Exec=whatever you wish to execute goes here (e.g. gimp)
		Icon=whatever path to an icon you want (e.g. apple-red)
		Terminal=false
		Type=Application
		Categories=Application;WebDesign;

```

that is it.
now to add more entries to that category just make more desktop files as needed.
I know it is a little complex but thats the only way I have found to do it yet.

---

### Post by kiddo on 2005-03-04
Great! I was looking for that answer all over!
Say, has the ubuntu team said anything about this yet? In the docs or something? I had someone tell me that in debian, there's no such thing as that locked down gnome menu. Is it something that came from Ubuntu's part, or from Gnome 2.10 ?
(edit: I've just read this: [http://www.ubuntuforums.org/showthread.php?t=9007](http://www.ubuntuforums.org/showthread.php?t=9007) )

---

### Post by Jonathan_ on 2005-03-04
Thanks, the "nautilus Applications:///" command worked great :)

---

### Post by kassetra on 2005-03-04
[QUOTE=Jonathan Steel]Thanks, the "nautilus Applications:///" command worked great :)[/QUOTE]

One little note about using Applications:/// ... you *might* want to change the permissions for /usr/share/applications or run the nautilus command as sudo everytime... otherwise it may give you some issues.

---

