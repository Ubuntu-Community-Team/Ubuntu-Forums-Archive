---
title: "Keyboard shortcut for moving window to another virtual desktop"
date: 2011-03-18
forum: Desktop Environments
---

### Post by ApocryphalAuthor on 2011-03-18
Hey all,

In (Gnome) Ubuntu there is a keyboard shortcut Ctrl+Alt+Shift+(Up|Down|Left|Right) that allows the user to quickly move a window from one workspace to another.  I've been looking for a similar way to accomplish this in (KDE) Kubuntu.  I know that you can right-click on a window in the Task Manager and use "To Desktop" to move a window, but I'm just curious if the same thing can be accomplished with the keyboard.

Thanks for your help!

---

### Post by Krytarik on 2011-03-19
I neither use KDE nor do I have it installed, so I don't know its built-in features. But if you are using Compiz (desktop effects), you can use its "Put" plugin to achieve that:
- "... -> CompizConfig Settings Manager -> Window Management -> Put"
- enable it, if not already
- choose your desired key combination under the "Put to adjacent viewport" option

Greetings.

---

### Post by ApocryphalAuthor on 2011-03-19
> **Krytarik said:**
> I neither use KDE nor do I have it installed, so I don't know its built-in features. But if you are using Compiz (desktop effects), you can use its "Put" plugin to achieve that:
- "... -> CompizConfig Settings Manager -> Window Management -> Put"
- enable it, if not already
- choose your desired key combination under the "Put to adjacent viewport" option

Greetings.

Thank you very much for the suggestion.  I was aware that I could use Compiz window manager, but right now I'm just trying to familiarize myself with KDE and kwin, so I was really trying to find out if I could accomplish this in kwin.

On a side note to anyone interested.  I found out that you can take the icon of a window in the task manager and drag it onto the icon of the virtual desktop, that window will move the window to that virtual desktop.  

It's a start, but I'm still interested in a keyboard shortcut if anyone knows one.

---

### Post by Krytarik on 2011-03-19
How about this?:
[http://en.wikipedia.org/wiki/Table_of_keyboard_shortcuts#Window_management](http://en.wikipedia.org/wiki/Table_of_keyboard_shortcuts#Window_management)

And those settings?:
"System Settings -> Keyboard & Mouse -> Global Keyboard Shortcuts -> KDE component: KWin"

---

### Post by ApocryphalAuthor on 2011-03-19
Hey thanks for your help!  

I did find it.  In Kubuntu 10.10 it's under:
[LIST]
[*]K-menu->System Setting->Shortcuts and Gestures->Global Keyboard Shortcuts 
[*]Then, in the KDE component drop-down, select KWin
[*]Lastly, the action is Window One Desktop Down, Window One Desktop to the Left, Window One Desktop to the Right, and Window One Desktop Up
[/LIST]
Thanks again for your help.  I'm still getting used to the KDE UI. :shock:

---

