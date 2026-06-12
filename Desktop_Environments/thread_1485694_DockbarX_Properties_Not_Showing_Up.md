---
title: "DockbarX Properties Not Showing Up"
date: 2010-05-17
forum: Desktop Environments
---

### Post by Spike-X on 2010-05-17
I'm experiencing a strange problem with DockbarX. After having it installed for a week or two, all of a sudden it 'lost' its theme, and I can't get the Properties window to show up when I right click>Properties. Not sure what's going on here, has anyone else experienced this problem?

---

### Post by M7S on 2010-05-17
If you have the last version of dockbarx, you can run the preference window from the terminal to see what the error is (and post it here).

dbx_preference.py

It's the first time I've heard about themes suddenly disappearing.


M7S,
DockbarX developer

---

### Post by Spike-X on 2010-05-17
Here's the output:

```
spike-x@spike-x-desktop:~$ dbx_preference.py
Traceback (most recent call last):
  File "/usr/bin/dbx_preference.py", line 1264, in <module>
    PrefDialog()
  File "/usr/bin/dbx_preference.py", line 793, in __init__
    self.update()
  File "/usr/bin/dbx_preference.py", line 975, in update
    alpha = colors[a] * 256
KeyError: 'color1_alpha'
spike-x@spike-x-desktop:~$ ^C
spike-x@spike-x-desktop:~$ 


```

---

### Post by M7S on 2010-05-17
Same old bug. There is a fix that will be released in next version (which I've been holding back way too long). I still don't understand how you could loose your theme just like that. Perhaps you should run

dockbarx.py run-in-window

to see if you get any errors there as well. After that you could try to change your theme via gconf-editor (that goes for any other option you need from preference window as well. (/apps/dockbarx/theme)

---

### Post by Spike-X on 2010-05-18
> **M7S said:**
> Same old bug. There is a fix that will be released in next version (which I've been holding back way too long). I still don't understand how you could loose your theme just like that. Perhaps you should run

dockbarx.py run-in-window

Here's what happens:

```
spike-x@spike-x-desktop:~$ dockbarx.py run-in-window


** (dockbarx.py:1221): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (dockbarx.py:1221): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (dockbarx.py:1221): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Dockbarx init
Dockbarx reload
Opened window matched with gio app on id: guayadeque
Opened window matched with gio app on id: transmission
Opened window matched with gio app on id: firefox
Opened window matched with gio app on id: gnome-terminal

```

Then when I click Preferences:

```
Traceback (most recent call last):
  File "/usr/bin/dbx_preference.py", line 1264, in <module>
    PrefDialog()
  File "/usr/bin/dbx_preference.py", line 793, in __init__
    self.update()
  File "/usr/bin/dbx_preference.py", line 975, in update
    alpha = colors[a] * 256
KeyError: 'color1_alpha'

```

> **M7S said:**
> After that you could try to change your theme via gconf-editor (that goes for any other option you need from preference window as well. (/apps/dockbarx/theme)

That doesn't work either, even after I killall gnome-panel.

---

### Post by Tamanegi on 2010-05-19
Hi!
I had the same problem. I edited /usr/bin/dbx_preference.py and deleted color1_alpha and color5_alpha lines.
Now I can enter the properties without a problem.

---

### Post by Spike-X on 2010-05-19
> **Tamanegi said:**
> Hi!
I had the same problem. I edited /usr/bin/dbx_preference.py and deleted color1_alpha and color5_alpha lines.
Now I can enter the properties without a problem.
That seems to have done the trick. Thank you very much, Tamanegi!

---

