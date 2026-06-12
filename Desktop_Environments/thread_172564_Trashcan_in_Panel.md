---
title: "Trashcan in Panel"
date: 2006-05-08
forum: Desktop Environments
---

### Post by VK2XCI on 2006-05-08
Afternoon all,

Another brief question.

Is the trashcan on the Gnome Panel a real or virtual directory? If it's real, where does it live?

 I'd rather have it on the desktop to free up a bit of Panel real estate.

---

### Post by Gannin on 2006-05-08
You should be able to drag the trashcan from the panel to the desktop.

---

### Post by VK2XCI on 2006-05-08
[QUOTE=Gannin]You should be able to drag the trashcan from the panel to the desktop.[/QUOTE]

If only it were that easy, ot even intuitive!
Right click-->move-->drag doesnt work. moves only within the Panel
Left click-->drag simply opens the trash can.

I'm open to all suggestions, but the whole UI is starting to frustrate me more than a little!](*,)

---

### Post by Gannin on 2006-05-08
That's strange.  Left-click and drag works just fine for me.

---

### Post by VK2XCI on 2006-05-08
[QUOTE=Gannin]That's strange.  Left-click and drag works just fine for me.[/QUOTE]

Ummm....OK

Do your apps launch from Panel with a single or double click?

---

### Post by SavageBeginner on 2006-05-08
To get the trash on the desktop, press <Alt>F2 and run ```
gconf-editor
```
Find /apps/nautilus/desktop

Check trash_icon_visible.

---

### Post by VK2XCI on 2006-05-09
[QUOTE=SavageBeginner]To get the trash on the desktop, press <Alt>F2 and run ```
gconf-editor
```
Find /apps/nautilus/desktop

Check trash_icon_visible.[/QUOTE]

Yep, that works. Also explains a lot of other configuration options:cool: 

Should be good for hours of playing:-D

---

