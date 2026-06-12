---
title: "[SOLVED] Command to kill application"
date: 2009-01-06
forum: General Help
---

### Post by jose187 on 2009-01-06
I know you can do the Alt+F2 and then type in xkill,

But what i want to do is to create a key shortcut ... such as Ctrl + Esc.

I'm using ubuntu Tweak to do this ... what should i write as a command to make this shortcut possible?

---

### Post by kokkus on 2009-01-06
killall APPLICATIONNAME

BUt you can also add an application killer to your panel.
A little icon you click on to then click on the application window you wanna to kill.

---

### Post by jose187 on 2009-01-06
THanks Kokkus

With that command would i be able to kill ANY application? or just the one that i name?

The objective would be to press Ctrl + Esc and then get the pointer that lets you click on the window you want to terminate... is it even possible?

---

### Post by leveliv on 2009-01-06
you could also add the Force Quit button to your gnome panel and probably KDE panel. That's if you are using them I suspect you are using Gnome though.

---

### Post by kokkus on 2009-01-06
> **jose187 said:**
> THanks Kokkus

With that command would i be able to kill ANY application? or just the one that i name?

The objective would be to press Ctrl + Esc and then get the pointer that lets you click on the window you want to terminate... is it even possible?
just the application u name and that's the sad thing.
YOu have to write killall firefox or killall nautilus etc.

---

### Post by joehte on 2009-01-06
> **jose187 said:**
> THanks Kokkus

With that command would i be able to kill ANY application? or just the one that i name?

The objective would be to press Ctrl + Esc and then get the pointer that lets you click on the window you want to terminate... is it even possible?

Yes that's possible. If you're using Compiz, then open the CompizConfig Settings manager. From General Options and "Commands" tab assign to Commands xkill and to Key bindings Ctrl + Esc.

Then enjoy the killing spree.

If you're not using Compiz, then it can also be done but requires you to use gconf-editor.

---

### Post by jose187 on 2009-01-06
> **joehte said:**
> Yes that's possible. If you're using Compiz, then open the CompizConfig Settings manager. From General Options and "Commands" tab assign to Commands xkill and to Key bindings Ctrl + Esc.

Then enjoy the killing spree.

If you're not using Compiz, then it can also be done but requires you to use gconf-editor.


Thanks... this is 100% what i was after, 
But somehow it doesn't seem to work.
Ive done what you said and then typed in all of these:

"xkill"
"command xkill"
"run xkill"

and none of them do a single thing...what should i write in the command field?

---

### Post by jose187 on 2009-01-06
Ok,

got the answer.

Thanks joehte.

TRhe problpem was the actual shortcut.
For some reason it won't accept the ctrl + esc key combo. I changed this to "ctrl + delete" and it works!

so the command is "xkill" and the keyboard shortcut is "ctrl + delete".

Thanks joehte.

---

