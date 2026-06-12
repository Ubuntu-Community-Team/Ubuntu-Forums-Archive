---
title: "Pidgin widget names"
date: 2009-12-01
forum: Desktop Environments
---

### Post by Meneldir on 2009-12-01
Hello everyone. I've being playing around with Pidgin, customizing it a bit.
I've started modifying the theme through a personal theme.xml within $PIDGINHOME/themes/....
I still want to modify some aspects, as the blist background when there is no blist (the app color), where the blist will be loaded. For this, i've got to the conclusion that I must modify a widget style, or create a new one (what I'd like to do) using gtkrc-2.0.
I've changed a lot of times that file (the pidgin specific one), but I haven't seen any changes in the look & feel of Pidgin.

And now, the question:
Does anyone know the names of pidgin widgets?
For example:
```
#An example from pidgin site:
style "NoPidginGroupColor"
{
    bg[ACTIVE]   = "#FFFFFF"
}

widget "*pidgin_blist_treeview" style "NoPidginGroupColor"
```

Thanks in advance guys (and girls!)!.

---

### Post by Meneldir on 2009-12-02
I've used:
```
style "my-style" {
    base[NORMAL] = MYCOLOR
}

widget "*pidgin_blist_treeview" style "my-style"
```
And it worked (but not before), now it's working.
So, although my poblem, to see what I wanted is solved, I'd like to know all the names of the widgets as the thread title says, so, I'll leave it open.
If an admin thinks it does not concern the community, it may be moved somewhere else.

---

