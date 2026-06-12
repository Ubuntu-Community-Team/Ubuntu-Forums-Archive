---
title: "What's the matter with my GTK here?"
date: 2013-12-11
forum: Desktop Environments
---

### Post by unimous on 2013-12-11
[COLOR=#333333][FONT=UbuntuRegular]Every time I run a gtk program such nautilus, synaptic, those kind of appears again and again but those programs can still run:
[/FONT][/COLOR]
[FONT=courier new](gnome-terminal:589): GLib-GObject-WARNING **: Two different plugins tried to register 'BasicEngineFc'.
(gnome-terminal:589): GLib-GObject-CRITICAL **: g_object_new: assertion 'G_TYPE_IS_OBJECT (object_type)' failed
...[/FONT]

[COLOR=#333333][FONT=UbuntuRegular]What's the matter with it?[/FONT][/COLOR]

---

### Post by vasa1 on 2013-12-11
If the programs run as expected, don't worry! Such messages are not rare although I agree that their appearance can be disconcerting.

---

### Post by vasa1 on 2013-12-12
> **unimous said:**
> Every time I run a gtk program such nautilus, synaptic, those kind of appears again and again but those programs can still run:

```
(gnome-terminal:589): GLib-GObject-WARNING **: Two different plugins tried to register 'BasicEngineFc'.
(gnome-terminal:589): GLib-GObject-CRITICAL **: g_object_new: assertion 'G_TYPE_IS_OBJECT (object_type)' failed
...
```

What's the matter with it?
I find it odd that you see "(gnome-terminal:589):" at the start of the line. My experience has been that the name of the program launched from the terminal and its process number appear instead of the terminal's. In other words, even though you mention synaptic and nautilus, "gnome-terminal" appears in the message.

---

