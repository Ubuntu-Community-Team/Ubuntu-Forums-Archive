---
title: "how to recover gnome standard shortcut keys ?"
date: 2006-03-07
forum: Desktop Environments
---

### Post by peyu on 2006-03-07
hi everybody,

I was configuring the shortcuts in gnome (Preferences / keyboard shorcuts), and I think I made a mistake, because since then, every time I set the brightness down, my laptop goes to hibernate, which is quite annoying...

I don't have any idea of the shortcut I modified, and I cannot see the key in the keyboard shortcut window because it's a combination (Fn + F6).

Does anybody know how to recover the standard shortcut set ?

Thanks a lot !

---

### Post by aysiu on 2006-03-07
Try this. Go to Applications > Accessories > Terminal and type ```
mv ~/.gconf/apps/metacity/global_keybindings/%gconf.xml ~/.Trash/%gconf.xml
``` You have to log out and log back in before the change will take effect. I just tested it out.

---

### Post by peyu on 2006-03-08
I don't understand.
I did what you say, but it doesn't clear the shortcuts. So I went to Preferences / Keyboard shorcuts, and I disactivated all, but it still goes to hibernate when I do Fn + F6.

And very often, when it wakes up from the hibernation, it crashs.

I tried to stop the acpi service, but the Fn + F6 still "works".

So now, I see only two options : I never set the screen brightness down, or I reinstall Ubuntu... :cry:

---

