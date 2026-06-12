---
title: "nautilus folder settings"
date: 2007-05-23
forum: Desktop Environments
---

### Post by groovomata on 2007-05-23
Hello All!
I was wondering if there is a way to save nautilus folder settings. For instance I regularly view a folder as a list and every time, I have to adjust the columns to be able to see the file information properly. Is there a way to save these settings so that when I go to that folder it remembers my previous adjustments?
I'm using gnome 2.18.1 on feisty.
Thanks,
Erik.

---

### Post by aysiu on 2007-05-23
As far as I know, Gnome doesn't have folder-specific view settings. You may be able to do this in KDE's file manager, however.

---

### Post by groovomata on 2007-05-23
Ya, I'm kind of off KDE and onto gnome now. It seems snappier and nautilus seems more stable than konqueror. Anyways, I like the look better too, though folder specific view settings would be nice. Perhaps there's a config file to be edited, if I only knew which one...?
Thanks, 
Erik.

---

### Post by balia on 2008-01-23
I have the same problem.
I cannot get Nautilus to remember each individual folder settings!
Nautilus seems to be able to handle only one setting for ALL folders.
This is a serious restriction compared to Windows!
Any way around this?
Saw in some other post that using Konqueror instead may be the solution...

---

### Post by RawMustard on 2008-01-24
I think it remembers those settings if you're in spartial mode.  But it's a  retarded way to use a file manager.

---

### Post by metalheart on 2008-01-24
You can open any folder from command line like

```
nautilus /path/to/the/folder -g 800x600
```

where after the -g is the window size. Nautilus will use all available space to display file attributes.

You can hide attributes you don't need (like date and file type) to get more room for filenames.

---

### Post by mcduck on 2008-01-25
> **aysiu said:**
> As far as I know, Gnome doesn't have folder-specific view settings. You may be able to do this in KDE's file manager, however.

Yes it has, but you need to set the folders the way you want using the spatial mode. Any settings made in browser mode affect all folders that don't already have folder-specific settings.

I mostly use spatial mode (after learning couple of simple shortcuts it's way better for most tasks than browser mode is), so I have different icon sizes, view modes, background colors, window sizes and window locations for different folders.

---

