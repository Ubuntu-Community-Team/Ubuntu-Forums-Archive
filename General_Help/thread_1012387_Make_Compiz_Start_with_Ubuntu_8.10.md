---
title: "Make Compiz Start with Ubuntu 8.10"
date: 2008-12-15
forum: General Help
---

### Post by SilentZoom on 2008-12-15
Hey, I've been looking around the net for this for a few days, but for some reason, I can't make Compiz start when I log in on Ubuntu 8.10. (I can start it from the terminal, however.)

I'm fairly computer literate, but have little to-no coding/terminal experience.  Any help would be appreciated.

I've already tried:
1.Putting a Compiz entry under the sessions manager
2.Changing the entries in the config editor under desktop/gnome/applications/window manager to refer to compiz instead of metacity.

Thanks!

P.S. I'm running Intrepid on a Toshiba Satellite A135- Celeron 1.8ghz, Intel 945GM integrated graphics.

---

### Post by gettinoriginal on 2008-12-15
Hate to over simplify, but what is ticked under appearance, visual effects.  :p

---

### Post by SilentZoom on 2008-12-15
Nothing. I looked at that too and thought it meant it was set as custom? But if that's the problem I feel kinda dumb.  Haha.

---

### Post by AlanR8 on 2008-12-15
I have to ask, why would you want to start Compiz on boot? :confused:

Nice to have but distracting and frustrating in my HUMBLE opinion!!! :p

---

### Post by SilentZoom on 2008-12-15
Does it matter?
It's easier than re-mapping keyboard shortcuts to do the same things Compiz does automatically.  Compiz adds effects that just increase ease-of-use.

---

### Post by SilentZoom on 2008-12-16
So I was looking again at Sessions to see if metacity was loading instead of compiz... There's an entry under the name "Window Manager" with the command "gnome-wm". Is this metacity/is this preventing Compiz from loading?

---

### Post by eternalnewbee on 2008-12-16
> **SilentZoom said:**
> So I was looking again at Sessions to see if metacity was loading instead of compiz... There's an entry under the name "Window Manager" with the command "gnome-wm". Is this metacity/is this preventing Compiz from loading?
Compiz is not loading because you haven't "told it to".
When Compiz is running go to **Sessions > Options**, and click on **Save Currently Running Application**. That should do the trick.

---

### Post by Linux408 on 2008-12-17
System > Preferences > Sessions

you add a new entry, call it whatever you want and add
Code: compiz --replace


is that doesn't work download "Compiz Fusion Icon" form add/remove
it will let you enable or disable compiz with a click of a button.

---

### Post by SilentZoom on 2008-12-19
None of those worked.  I already had fusion-icon installed, but even that won't load from sessions.  I think I'm just going to go for a complete format/re-install on my HD, I wanted to re-install and dual boot XP anyway, I might as well do it now.

---

### Post by eternalnewbee on 2008-12-19
I just noticed, that the command to run compiz hasn't been mentioned...
SilentZoom, press **ALT-F2**, and enter ```
compiz --replace
```

---

### Post by stderr on 2008-12-19
Perhaps I'm being rather naive, but shouldn't the likes of this work?

System -> Preferences -> Sessions

Edit the Window Manager entry from 'gnome-wm' to 'gnome-wm --default-wm compiz'

If you check

```
man gnome-wm
``` 

it's explained.

Failing that, do an Alt+F2 and launch gconf-editor

Navigate to /desktop/gnome/applications/window_manager and set the default key to /usr/bin/compiz

Good luck :)

---

