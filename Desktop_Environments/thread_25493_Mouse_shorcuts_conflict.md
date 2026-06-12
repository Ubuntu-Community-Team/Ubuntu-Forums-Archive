---
title: "Mouse shorcuts conflict"
date: 2005-04-10
forum: Desktop Environments
---

### Post by efbie on 2005-04-10
Hello ! 
I just upgraded to hoary and i have a big problem.
A new mouse shortcut has been set. If i press <alt>+Right Mouse button, it opens the window menu.

the problem is that it is also the shortcut of an essential tool in blender. and i can't change blender hotkeys. 

I looked in the keyboard shortcuts list but changing the 'Activate window menu" shorctut doesn't supress the mouse shortcut.

Is there a way to completely disable these kinds of shortcuts ? 

thank you :)

---

### Post by Nis on 2005-04-10
I don't get this behavior so something must have been set locally.  Try checking under /apps/metacity using the "Configuration Manager"

Edit:  I do get this behavior when I hover over a window.  I just misunderstood your problem.  I would still check the above though.

---

### Post by rmunn on 2006-07-20
This is a bit of an old thread, but I ran into the same problem, so I figured I'd post my solution here so that anyone else searching for this could find it.

First of all, a quick note about the Configuration Editor, a.k.a. gconf-editor. As of a recent version of GNOME (2.14, I think), it's been hidden in the GNOME menus by default, because it's a little intimidating to someone who doesn't know how to use it, and the System->Preferences menu is meant to be more user-friendly. However, sometimes there's no preferences dialog for what you want to change, and you need the Configuration Editor. To unhide it, you can run the Alacarte Menu Editor (under Applications->Accessories) and check the Configuration Editor checkbox (under System Tools).

Or, you could just skip all that and run gconf-editor from the command line, like I did. :D

Anyway, once I had gconf-editor up and running, I quickly found the configuration key I needed to change: mouse_button_modifier, under /apps/metacity/general. It was set to "<Alt>". I set mine to "<Meta>" (on most keyboards, that'll be the Windows-logo key between Ctrl and Alt), since that's not used for any Blender shortcuts that I know of.

Voila: now I can use the loop-select tool in Blender. Hurrah! :cool:

---

### Post by Backharlow on 2007-10-02
I also recently had a related issue where the Blender mouse modifier "Control" (i.e. Ctrl) was conflicting with Metacity shortcut binding. Reconfiguring Metacity settings in gconf-editor didn't work but after working with Blender further I realized that I could bounce Shift, Ctrl, Mouse, then release shift, to effect what should just be Ctrl, Mouse. This is to execute the "snap to whole units" function in the 3d viewport.

---

### Post by idkwot on 2007-10-02
> **rmunn said:**
> This is a bit of an old thread, but I ran into the same problem, so I figured I'd post my solution here so that anyone else searching for this could find it.

First of all, a quick note about the Configuration Editor, a.k.a. gconf-editor. As of a recent version of GNOME (2.14, I think), it's been hidden in the GNOME menus by default, because it's a little intimidating to someone who doesn't know how to use it, and the System->Preferences menu is meant to be more user-friendly. However, sometimes there's no preferences dialog for what you want to change, and you need the Configuration Editor. To unhide it, you can run the Alacarte Menu Editor (under Applications->Accessories) and check the Configuration Editor checkbox (under System Tools).

Or, you could just skip all that and run gconf-editor from the command line, like I did. :D

Anyway, once I had gconf-editor up and running, I quickly found the configuration key I needed to change: mouse_button_modifier, under /apps/metacity/general. It was set to "<Alt>". I set mine to "<Meta>" (on most keyboards, that'll be the Windows-logo key between Ctrl and Alt), since that's not used for any Blender shortcuts that I know of.

Voila: now I can use the loop-select tool in Blender. Hurrah! :cool:

couldnt have said it better myself

---

### Post by Backharlow on 2007-11-07
Thanks idkwot, that helped out too.

---

### Post by ewomer on 2008-01-24
on a generic us 105 keyboard i had to change <Alt> to <Super> because <Meta> would not work

---

### Post by kurageart on 2008-06-01
mmm just tryng xubuntu... very cool, i must say... but hot to disable this alt rmb shortcut??? any idea?

---

