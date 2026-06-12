---
title: "Xfce style system monitor panel plugin in Gnome?"
date: 2008-01-28
forum: Desktop Effects &amp; Customization
---

### Post by Euan17 on 2008-01-28
Hi, i've tried out ubuntu and xubuntu (i originally heard the Xfce desktop was better for older computers but now i hear that gnome isn't as heavy as it used to be, anyway...) and i really liked the look of the Xfce desktop but it lacked some features (dragging selection boxes, an easy method to mount network drives) so i decided to go back to ubuntu but i really like the the system monitor panel pluggin with Xfce. it was the one that just showed a bar of each item and a lable next to it (CPU,  RAM, SWAP, Battery) i think the battery one was seperate but i liked how it showed the percentage and time remaining without having to hover over it. is there a similar pluggin for the gnome desktop?
thanks

edit: these are the pluggins i was talking about (links below) is there anything similar available for gnome? if not how easy would it be to port them myself?
[http://goodies.xfce.org/projects/panel-plugins/xfce4-systemload-plugin](http://goodies.xfce.org/projects/panel-plugins/xfce4-systemload-plugin)
[http://goodies.xfce.org/projects/panel-plugins/xfce4-battery-plugin](http://goodies.xfce.org/projects/panel-plugins/xfce4-battery-plugin)

---

### Post by jslmg on 2008-01-30
I'm looking for an answer to this too--getting the XFCE panel to work in Gnome. Is that possible?

Or, closer to Euan's question, getting XFCE panel plugins to work in Gnome panels, like the system monitor or the weather plugin. Is that possible?

---

### Post by Tenken on 2008-01-30
Euan17, gnome panel has it's own battery monitor called Power Manager, it also has a CPU monitor but it's not like the xfce one. [Here]("http://www.gnomefiles.org/subcategory.php?sub_cat_id=154") is a link with some panel applets.

jslmg, you can run the xfce panel in gnome by doing this in a terminal

```
sudo apt-get install xfce4-panel
```

to run it, hit Alt+F2 and type

```
xfce4-panel
```

Depending on how you gnome panels are set up the xfce panel my appear above/below them.

---

### Post by jslmg on 2008-01-30
> **Tenken said:**
> Euan17, gnome panel has it's own battery monitor called Power Manager, it also has a CPU monitor but it's not like the xfce one. [Here]("http://www.gnomefiles.org/subcategory.php?sub_cat_id=154") is a link with some panel applets.

jslmg, you can run the xfce panel in gnome by doing this in a terminal

```
sudo apt-get install xfce4-panel
```

to run it, hit Alt+F2 and type

```
xfce4-panel
```

Depending on how you gnome panels are set up the xfce panel my appear above/below them.

Yep, as simple as that. Euan17, you might try running the XFCE panel within Gnome instead of the Gnome panel, so you get all the great XFCE goodies you want. That's what I'd like to do.

As for me, I'll keep this in mind, though it looks as if I'll have to change my desktop theme to do it. I'm using iMetal, the Mac-like theme, with the panel on top. The XFCE panel, in its default state at least, does not render that well in this theme. The weather plugin, particularly, needs more pixel space than the iMetal theme provides.

I'll keep working on it, though.

Thanks, Tenken.

---

