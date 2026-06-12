---
title: "Panel that won't delete"
date: 2010-10-13
forum: Desktop Environments
---

### Post by Jonny87 on 2010-10-13
I have a panel that I don't want anymore and for some reason when I right click on it, it won't let me delete it. Is there a Way that I can remove it?

---

### Post by TNT1 on 2010-10-13
I have only one panel and the delete option is grayed out, so I have the same problem.

---

### Post by drpjkurian on 2010-10-13
Hi to kill the gnome panel, open the terminal and type
```
pkill gnome-panel
``` you will be getting a normal default gnome panel, Right click it and delete it forever. Let me know whether it works for you...

---

### Post by stinkeye on 2010-10-13
Alt +F2 and run gconf-editor

 go to /desktop/gnome/session/required_components_list

Double click on required_components_list and remove **panel**.

Logout and in for changes.

Now though you won't be able to use the alt+F2 or alt+F1 shortcuts to bring 
up the run dialogue or menu, respectively.

If you need to set it back the way it was, right click on **required_components_list**
and choose **unset key**.

---

### Post by drpjkurian on 2010-10-13
Hi
try this too If you don't want to disable alt+f2 dialog, then you may try a simple trick. Remove everything from unnecessary panel. Open preferences of the panel and make sure it expanded. Then set the background of the panel to transparent. In such case, you won't get rid off it but you won't simply see it

---

### Post by Jonny87 on 2010-10-13
> **drpjkurian said:**
> Hi to kill the gnome panel, open the terminal and type
```
pkill gnome-panel
``` you will be getting a normal default gnome panel, Right click it and delete it forever. Let me know whether it works for you...

Tried this and the panel just kept coming back. I'm wondering if its anything to do with the fact that it is the only panel left as if i add another on it allows me to delete. I'm now using AWN so I don't need the Gnome panel hanging around.

I don't want to disable Alt+F2 as I use it all the time.

Making it transparent seems to be just as annoying as its transparent straight though to the Desktop so when it appears it covers any open window with that portion of the desktop background.

---

### Post by SantaFe on 2010-10-13
Short of right clicking on the taskbar, picking properties, checking show hide buttons & clicking on the left or right hide button so the taskbar slides out of view (except for a little part to click on again), can't think of anything else.  Hehehe maybe combine the transparent Pic solution & this one. :P

---

### Post by stinkeye on 2010-10-14
If you want to maintain Alt+F1/F2 functionality remove all the applets from
 the panel and set it to autohide.
If you set the panel background to black it's less noticeable when hidden.

Then in gconf-editor **/apps/panel/toplevels/top_panel_screen0/unhide_delay**
set it to something like 100000000.

You will have a 1 pixel space at the top that you can't make smaller.

---

### Post by TNT1 on 2010-10-14
So you guys are saying alt-f2 is linked to the panel? That's just wrong. I mean why design it like that?

---

### Post by Jonny87 on 2010-10-14
It does seem like a slight, flaw. I can see that perhaps its a bit of a safety thing as when the last panel is gone you can't right click anything and go add panel. you would suddenly be with out panels leaving you delete you GNOME config folders and let it create a new one on next login.

Though the biggest thing I like about Linux is the ability to customize it to what I want. It would be nice if there was an option turn on or off the panels or someting like that.

---

