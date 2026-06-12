---
title: "odd xbindkeys problem"
date: 2012-07-21
forum: Desktop Environments
---

### Post by ddeleon4 on 2012-07-21
hey guys, I have searched for this with no luck (may just not be using the right keywords), but I am Having a problem with xbindkeys where I assign expo (super+s) and window picker (super+w) to the left and right scroll wheel movements of my mouse (b:7 and b:6 respectively). The problem is that it works the first time but not the second, meaning that if I go into expo or window picker the press the respective button again, it won't leave expo or window picker. In order to leave I am force to double click, press Enter, or use the keyboard shortcuts. I just don't understand why the keyboard shortcuts work both times but not the shortcut made by xbindkeys. Is there anyway to make this work?

---

### Post by ddeleon4 on 2012-07-25
here is some extra detail about this problem, the code is written like so:

```

#Expo
"xte 'keydown Super_L' 'key z' 'keyup Super_L'"
   b:7

#Mission Control/Window picker
"xte 'keydown Super_L' 'key w' 'keyup Super_L'"
   b:6

```
Also, some times they system holds down the z or w keys after I have exited the respective action.

Any help is greatly appreciated

---

### Post by brainwash on 2012-07-25
Install **xdotool** and edit your xbindkeys configuration file. Maybe one of these changes (or both) will solve your problem:

1)
```
xdotool key super+z
```
2)
```
b:7 + Release
```

---

### Post by ddeleon4 on 2012-07-25
> **brainwash said:**
> Install **xdotool** and edit your xbindkeys configuration file. Maybe one of these changes (or both) will solve your problem:

1)
```
xdotool key super+z
```2)
```
b:7 + Release
```

thank you so much for the help. This fixed the sticking key problem but problem of the shortcut not working once in expo or window picker still exists, is this something that I’m gonna have to live with or is there something I can do to fix it?

---

### Post by brainwash on 2012-07-26
> **ddeleon4 said:**
> This fixed the sticking key problem but problem of the shortcut not working once in expo or window picker still exists, is this something that I&#8217;m gonna have to live with or is there something I can do to fix it?
That's really an odd issue. Guess I'll get a copy of Ubuntu somewhat later to see how the Unity stuff works. Maybe there is a way to fix your custom keybindings.

_edit:_
I was able to reproduce the issue. The culprit is of course compiz. So I went ahead and installed **CompizConfig Settings Manager** to change following things:

*Desktop > Expo > Bindings*
- Assign **Button7** to "Expo Button"

*Window Management > Scale > Bindings*
- **Check** "Button Bindings Toggle Scale Mode"
- Assign **Button6** to "Initiate Window Picker For All Windows" (mouse icon)

Don't forget edit your xbindkeys configuration file and remove the two entries, which are no longer needed.

---

### Post by ddeleon4 on 2012-07-27
Thank you, that worked perfectly

---

