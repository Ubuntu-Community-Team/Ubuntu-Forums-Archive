---
title: "Move to workspace on open"
date: 2011-03-23
forum: Desktop Environments
---

### Post by Giraffro on 2011-03-23
I've got a few programs that open up in specific workspaces, but when they're opened they don't automatically move to that workspace, unlike Mac OS X. Is there a way to set this up in Compiz?

Thanks in advance!

---

### Post by Krytarik on 2011-03-23
I'm not sure if I got you right, because your post somehow contradicts itself.

But if you want that specific apps always open in specified workspaces, you can use Compiz' "Place Windows" plugin for that:
"System ->  Preferences -> CompizConfig Settings Manager -> Window Management  -> Place Windows".

In the "Fixed Window Placement" tab add a rule to "Windows with fixed  viewport", grab the "class" of the respective apps in the "New" dialog.
[http://wiki.compiz.org/WindowMatching](http://wiki.compiz.org/WindowMatching)

Greetings.

---

### Post by Giraffro on 2011-03-23
> **Krytarik said:**
> I'm not sure if I got you right, because your post somehow contradicts itself.

But if you want that specific apps always open in specified workspaces, you can use Compiz' "Place Windows" plugin for that:
"System ->  Preferences -> CompizConfig Settings Manager -> Window Management  -> Place Windows".

In the "Fixed Window Placement" tab add a rule to "Windows with fixed  viewport", grab the "class" of the respective apps in the "New" dialog.
[http://wiki.compiz.org/WindowMatching](http://wiki.compiz.org/WindowMatching)

Greetings.

That's what I have setup, but it doesn't move to that workspace when opened. For example, I've setup Evolution to open in workspace 1. If I'm in workspace 2 and I open Evolution, it appears in the window list but I'm still in workspace 2; I have to manually move to workspace 1 to get to Evolution. I hope I've clarified my problem.

---

### Post by Krytarik on 2011-03-23
Ah, you want that YOU get moved to the workspace of the just launched app. I don't believe that this is possible via Compiz' settings. But you could include a command for that into the launchers of the respective apps.

---

### Post by Giraffro on 2011-03-24
I've managed to find a solution using xdotool (allows you to simulate key presses) together with the keybinding settings in Compiz. Also tried wmctrl but it doesn't seem to work with Compiz, at least when switching desktops.

---

### Post by Krytarik on 2011-03-24
I was actually meaning wmctrl. Sorry for not elaborating further before, but I wasn't sure if you are fine with the launcher thing.

See my earlier post regarding it: [http://ubuntuforums.org/showthread.php?p=10404646](http://ubuntuforums.org/showthread.php?p=10404646)

For example, the launcher command for Evolution would need to be like this:
```
sh -c "evolution; wmctrl -o 1152,0"
```

---

### Post by Giraffro on 2011-03-24
> **Krytarik said:**
> I was actually meaning wmctrl. Sorry for not elaborating further before, but I wasn't sure if you are fine with the launcher thing.

See my earlier post regarding it: [http://ubuntuforums.org/showthread.php?p=10404646](http://ubuntuforums.org/showthread.php?p=10404646)

For example, the launcher command for Evolution would need to be like this:
```
sh -c "evolution; wmctrl -o 1152,0"
```

That's much neater, thanks! On a sidenote, do you know if it's possible to move workspaces when I open a link in, say, Evolution? If not, I'll open a new thread.

---

### Post by Krytarik on 2011-03-24
> **Giraffro said:**
> On a sidenote, do you know if it's possible to move workspaces when I open a link in, say, Evolution? If not, I'll open a new thread.
To achieve that you need to enter a "Custom" command for the web browser in "Preferred Applications", like this:
```
sh -c "firefox %s; wmctrl -o 0,0"
```

---

### Post by Giraffro on 2011-03-24
Thanks, that's perfect!

---

