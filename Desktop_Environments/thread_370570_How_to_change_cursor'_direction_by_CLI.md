---
title: "How to change cursor' direction by CLI"
date: 2007-02-25
forum: Desktop Environments
---

### Post by eexpress on 2007-02-25
Edgy, i386, gnome(metacity)

I often swap my mouse button between left-hand and right-hand.
and within my bash, i add this line, want also change the cursor' direction:
```
xsetroot -cursor_name left_ptr
```
but that only can use the default X cursor theme-"redglass", which i defined at ~/.Xdefaults. I cannot find any gnome-xxx command to do this.
and gconftools with some parameter maybe can do??

I have a lot of cursor sets locate at ~/.icons. and many cursor theme has left and right direction set, such as *Grounation* theme and *Grounation-left*. I want use those one when i swap the mouse buttons.

Seems someone mention modify xorg.conf, add Option 'sw_cursor'. I not test this, for it seems can not change by a bash and take effect real time.

An addtion question: within the opera(QT software), I also want see the effect. see the lovely cursor freely change direction everywhere.
:KS :KS :KS

---

### Post by eexpress on 2007-02-25
$&#9679;  grep '^Xcursor' .Xdefaults 
Xcursor.theme: FlatbedCursors.Green.Huge
Xcursor.size: 16

then "xsetroot -cursor_name left_ptr/right_ptr" can fit me. this is a dumb mothed i think. for now i can not change cursor theme freely.

so now question become: how to change Xcursor and take effect immediatelly.

---

