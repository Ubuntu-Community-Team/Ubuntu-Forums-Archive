---
title: "Small toolbar icons for gnome applications"
date: 2008-12-10
forum: Desktop Environments
---

### Post by golimpio on 2008-12-10
I was looking for a way to change the size of the toolbar icons of GNumeric and AbiWord applications. But I didn't find an application for it (except for the gconf editor).

The solution that worked for me was the follow one:

```
gconftool-2 --set --type=string /desktop/gnome/interface/toolbar_icons_size "small-toolbar"
```

That's change the toolbar size of all gnome applications, what was good for me. Sometimes I need more room on my desktop, mainly when I'm using a small laptop screen.

Anyway, for restoring the default large icons run the follow command:

```
gconftool-2 --set --type=string /desktop/gnome/interface/toolbar_icons_size "large-toolbar"
```


Is there an gnome application (GUI) to do it ?

Thanks

---

### Post by tech9 on 2008-12-10
> **golimpio said:**
> I was looking for a way to change the size of the toolbar icons of GNumeric and AbiWord applications. But I didn't find an application for it (except for the gconf editor).

The solution that worked for me was the follow one:

```
gconftool-2 --set --type=string /desktop/gnome/interface/toolbar_icons_size "small-toolbar"
```That's change the toolbar size of all gnome applications, what was good for me. Sometimes I need more room on my desktop, mainly when I'm using a small laptop screen.

Anyway, for restoring the default large icons run the follow command:

```
gconftool-2 --set --type=string /desktop/gnome/interface/toolbar_icons_size "large-toolbar"
```
Is there an gnome application (GUI) to do it ?

Thanks

gimp

---

### Post by beau.raines on 2010-08-30
There is a GUI Gnome configuration tool [FONT="Courier New"]gconf-editor[/FONT] so that you can make these same kinds of changes.

---

