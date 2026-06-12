---
title: "How do I make a &quot;floating&quot; gnome-panel?"
date: 2007-12-11
forum: Desktop Environments
---

### Post by I922sParkCir on 2007-12-11
How do I make a "floating" gnome-panel? I would like it to just sit behind any open application on the desktop.

If any one has any idea I would appreciate it.

-Jai

---

### Post by Jadd on 2007-12-11
Not quite sure what you mean... As far as I know, gnome-panel can I only be attached to one of the edges of the screen. Maybe you can do what you're looking for with widgets, desklets or screenlets?

---

### Post by Krydahl on 2007-12-11
If you run gconf-editor and go to apps -> panel ->top_level you'll find a set of extra parameters you can configure for each panel you have, These include x and y displacement parameters. I've never tried it, but setting those to put the panel in the middle of the screen might work.

---

### Post by I922sParkCir on 2007-12-11
I would like the gnome-panel to be like a widget, but with processor scaling, network-manager, gnome-power-manager, and a notification area. I have a laptop with a small so I would like all my apps to be fullscreen.

I thought it'd be easier to find a way to make a floating panel.

-Jai

---

### Post by I922sParkCir on 2007-12-11
> **Krydahl said:**
> If you run gconf-editor and go to apps -> panel ->top_level you'll find a set of extra parameters you can configure for each panel you have, These include x and y displacement parameters. I've never tried it, but setting those to put the panel in the middle of the screen might work.

This works perfectly, thank you. Now how do I make the panel stay out of focus and behind windows.

-Jai

---

### Post by Krydahl on 2007-12-11
Sorry, no idea on that one.

You can change the background colour or make it transparent using the preferences. No idea how you can change it's focus.

---

### Post by Krydahl on 2007-12-11
There's an app called Conky that is maybe more what you're looking for. I've never used it and I gather it's a bit of a pain to set you, but it might be worth a look:

[http://ubuntuforums.org/showthread.php?t=205865&highlight=conky](http://ubuntuforums.org/showthread.php?t=205865&highlight=conky)

---

### Post by lswest on 2007-12-11
conky isnt that hard to set up, i just have a problem that when i start it at boot that it's above any other window, and have to kill it and restart it, but other than that just editing the conkyrc.sample file (comes with conky) works just fine.  if you want i can upload my conkyrc file for ya.

---

### Post by I922sParkCir on 2007-12-11
Conky looks nice, but what I want is exactly this, but behind the application.

-Jai

---

### Post by Blutack on 2007-12-11
To fix conky use a script that starts it after gnome loads, for example mine is
```

#!/bin/bash
sleep 10 && `conky` & `gnome-do --quiet` &

```
which starts conky and gnome-do (awesome app!).  Gnome 2.20 is nasty, I keep thinking about downgrading to feisty again.

---

### Post by I922sParkCir on 2007-12-11
> **Blutack said:**
> To fix conky use a script that starts it after gnome loads, for example mine is
```

#!/bin/bash
sleep 10 && `conky` & `gnome-do --quiet` &

```
That's cool, but I don't really want to use conky. I need the gnome panel applets. Thank you though.

-Jai

---

### Post by Kiri on 2008-04-14
I've got the gnome panel floating, but when its at the top of the screen it reserves the space at the top so that windows wont maximize to the full size. How can I stop it doing this?
I just want it to float at the top above mximized windows

---

### Post by Halter on 2008-04-28
Use auto hide, and in gconf-editor (same location) mentioned above is option to set a size of panel when hidden.

---

### Post by Kiri on 2008-04-30
> **Halter said:**
> Use auto hide, and in gconf-editor (same location) mentioned above is option to set a size of panel when hidden.

Promising solution. But unfortunately it has two problems for me:
1) I can't seem to set the size beyond about 15px (anything above this seems to get ignored), so only half the bar is visable. 
2) The usable desktop space is still defined by the size of the panel so I cant maximize windows to fill the whole screen

---

