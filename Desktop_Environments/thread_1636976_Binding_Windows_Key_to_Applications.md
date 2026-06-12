---
title: "Binding Windows Key to Applications?"
date: 2010-12-03
forum: Desktop Environments
---

### Post by gunit888 on 2010-12-03
I'm trying to migrate over to Ubuntu, and there is one really useful feature that I would like to replicate in Gnome.  In Windows, I can hit the "Windows" key on my keyboard, which opens up the start menu. 

Is there a way that I can replicate this behaviour in Gnome?  Can I map the Windows key to opening the Applications menu?

---

### Post by Liverbones on 2010-12-03
Well... I have to say, I'm not sure of a way to use the Super key alone to open the GNOME menu. But there are some other great uses for the Super key (especially if you're using Compiz).

But just so you know, the shortcut for the GNOME menu by default is Alt+F1, but if you want to change that (to almost whatever you want, really) you can use Keyboard Shortcuts to do so. Just go to System > Preferences > Keyboard Shortcuts, and go to Desktop > Show the panel's main menu, then enter a new shortcut. Unfortunately, it won't take a single modifier key as the entire shortcut, though.

---

### Post by gunit888 on 2010-12-03
Ah, I see.  It looks like GNOME treats that key as a modal key, like Ctrl, Alt, and Shift.  That's kind of interesting actually.  Seeing as how that's the case, I don't think it would be possible to have it alone do any kind of action.  

For the moment, I mapped the Action "Desktop->Show the panel's main menu" to Mod4+Space, which is reasonably convenient, and sort of close to what I'm used to.  I could also have mapped the Menu key (which I never use), which will work as a single key.  

Thanks for the help and improving my understanding!

---

### Post by gunit888 on 2010-12-03
Out of curiosity, what are some good uses of Super?

---

### Post by asmoore82 on 2010-12-03
For Desktop Effects:

Super+E activates expo

Super + Mouse Wheel Zooms

Super + Middle click & Drags Zooms to Box

I added Super + Tab to be the All Desktops Ring Switcher.

---

### Post by gunit888 on 2010-12-04
Wow this is awesome!  Thanks!  I'm totally geeking out :)

---

### Post by ottabaub on 2011-02-02
The following steps will allow mapping of the main menu to the Windows (Super) key:

[LIST=1]
[*]Run the Configuration Editor (gconf-editor)
[*]Open apps-->metacity-->global_keybindings
[*]Click on the Value of panel_main_menu.
[*]For the new value, enter: Super_L
[*]Close the Configuration Editor
[/LIST]

Now when you press the Windows (Super) key the applications menu will appear.

---

