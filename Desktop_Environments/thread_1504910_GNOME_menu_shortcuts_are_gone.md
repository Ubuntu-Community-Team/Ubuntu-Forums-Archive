---
title: "GNOME menu shortcuts are gone"
date: 2010-06-08
forum: Desktop Environments
---

### Post by stairmast0r on 2010-06-08
So yesterday I was moving some launchers in the menu editor, going a bit too fast, and I accidentally hit delete on the "Internet" menu.  In an attempt to get it back, I deleted ~/.local/share/applications and ~/.gconf/apps/panel, assuming they'd be automatically replaced.  I ran the updater today and it updated gnome-panel, so I $ killall gnome-panel 'd just in case, and once again nothing.  I have all the custom launchers from ~/.local/share/applications saved onto my desktop, but right now I need all the original launchers back.  I don't even have the software management launcher!  It just shows me a little tiny black stripe because it's completely empty.  BTW, I'm running Lucid 64.

---

### Post by stairmast0r on 2010-06-09
Anyone?

---

### Post by resolv_25 on 2010-06-09
Did you check out your trash?
(let say from nautilus)

---

### Post by stairmast0r on 2010-06-09
I deleted it from the menu editing...menu.  It wouldn't have gone to the trash.
I just checked to be sure and it wasn't there.  I'm not even hoping to restore all my shortcuts anymore, I'm just trying to get back the default ones, and possibly the ones for my other apps I've installed via apt if possible.

---

### Post by stairmast0r on 2010-06-10
I still have no idea what to do...

---

### Post by Dustin2128 on 2010-06-10
visual person, sorry but could you give me a screenshot of your problem? Also it's never a good idea to delete something assuming it will be replaced automatically, led me to enough headaches ](*,).... What exactly did you do in your menu editor to delete the internet menu? Without knowing more about your problem and not having used the menu editor in a while, I'd assume the best course of action would be to create a new menu folder, name it internet and put all your net-related programs in there... and it'd also probably be prudent to restore those files you deleted, because if you deleted those with nautilus, they *would* go into the trash bin.

---

### Post by gingivere0 on 2010-06-10
Right-click on the black bar that you have and click add to panel.  Look for Menu bar and click to add that.  Everything else that you deleted from your bar can be put back by right-clicking and re-adding them to the panel.  Hope this works :)

---

### Post by kerry_s on 2010-06-10
right click the menu-> edit menus
on the bottom click "revert"
log out & back in

---

### Post by stairmast0r on 2010-06-12
I think Revert only undoes changes that were made since you opened the editor.  Also, When I said they wouldn't be moved to the trash, I meant the internet menu that was deleted via the editor, not the config files.  I tried to take a screenshot but it won't let me while I have the menu dropped down.  Final "also", I deleted them with rm.  I'm starting to lose hope of getting this back at all.  The problem now isn't that I lost the internet menu, but the ENTIRE menu.  Things appear to be enabled on the editor, but they don't show up.

---

### Post by stairmast0r on 2010-06-13
Guys?

---

