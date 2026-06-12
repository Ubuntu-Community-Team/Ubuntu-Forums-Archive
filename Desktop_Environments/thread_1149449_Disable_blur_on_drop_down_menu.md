---
title: "Disable blur on drop down menu?"
date: 2009-05-05
forum: Desktop Environments
---

### Post by butterdori on 2009-05-05
I've activated the blur on compiz through CCSM. 

ow can I disable the blur on dropdown menus as it's shown on the attachment? 

The 'focus blur windows' looks like this

(type= toolbar | blur | utility | normal | dialog | modaldialog) & !(name=gnome-screensaver | name=.*Screenlet.* | state=skiptaskbar | state=skippager)

oh ubuntu 8.10 btw

---

### Post by benoy4007 on 2009-05-05
Go to Apparance disable compiz and then enable it, with your required effects.

---

### Post by butterdori on 2009-05-05
Hi,

No, restarting it doesn't seem to work...

---

### Post by mcduck on 2009-05-05
The different menu windows are of type "Menu", "PopupMenu" or "DropdownMenu".

```
(type= toolbar | blur | utility | normal | dialog | modaldialog) & !(name=gnome-screensaver | name=.*Screenlet.* | state=skiptaskbar | state=skippager) & !(type=Menu | DropdownMenu | PopupMenu)
```

---

### Post by butterdori on 2009-05-05
> **mcduck said:**
> The different menu windows are of type "Menu", "PopupMenu" or "DropdownMenu".

```
(type= toolbar | blur | utility | normal | dialog | modaldialog) & !(name=gnome-screensaver | name=.*Screenlet.* | state=skiptaskbar | state=skippager) & !(type=Menu | DropdownMenu | PopupMenu)
```

That did the trick. Thanks very much!!

---

### Post by butterdori on 2009-05-05
Scratch that, the problem returns if I minimise it and then maximise the window again....

Could it be a bug?

---

### Post by mcduck on 2009-05-05
That could be a bug indeed.

As Firefox doesn't really use native toolkits for it's graphics (at least directly) it has some issues with menu window types, using wrong widgets in wrong places etc.. 

However I've found those window types to work fine with Firefox, at least for setting menu transparencies, so the bug could be in the blur plugin as well as in Firefox.

edit: Actually I think it's a Firefox bug. Now that I paid some extra attention to Firefox menus, the dropdown box on the address bar doesn't seem to behave correctly. I suppose Firefox must be using some other window type for it.

---

