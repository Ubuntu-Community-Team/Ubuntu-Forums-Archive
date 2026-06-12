---
title: "Silly mistake..."
date: 2009-05-10
forum: General Help
---

### Post by jwkungfu on 2009-05-10
Hello!
Got a silly self-inflicted problem that I can't seem to fix...

I thought I was telling my computer to open all my music files with Rythmbox... (right click, preferences, open with...)
Except now, every time I go (toolbar) Places and pull down (example) Videos... Rythmbox opens up!?!! Try again... Places, Documents.... Rhythmbox opens up??!!

Tried everything I know/can think of.... nada....    :O(

Any help?.... please...  :(  :confused:

john

---

### Post by spiderbatdad on 2009-05-10
Try System>>Preferences>>Preferred Applications>>Multimedia
set to custom.

---

### Post by jwkungfu on 2009-05-10
Thanks for the rapid reply!
I tried what you said and it was already set to custom...?

---

### Post by spiderbatdad on 2009-05-10
sounds like something weird happened in gconf. You can try browsing the config editor in system tools to apps>>nautilus>>preferences>>check always use browser.
or try this in terminal
```
gconftool-2 --type bool --set /apps/nautilus/preferences/always_use_browser true
```

---

### Post by mikewhatever on 2009-05-10
If you use Gutsy, right click on any folder, select Properties and then the Open with tab. Make sure that Open folder entry is the topmost on the list. If you need to open the file manager to get to the folders, press alt+f2 and type **nautilus** into the command line.

---

### Post by jwkungfu on 2009-05-10
I seemed to have messed with the way the Toolbar is operating?
I can open folders through Places, Computer etc etc etc...

It's when I use the mouse, Places, Documents (or Desktop or Videos etc).... Rhythmbox opens up!??

---

