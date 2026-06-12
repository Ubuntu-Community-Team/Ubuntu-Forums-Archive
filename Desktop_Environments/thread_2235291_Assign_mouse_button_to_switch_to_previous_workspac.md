---
title: "Assign mouse button to switch to previous workspace"
date: 2014-07-20
forum: Desktop Environments
---

### Post by Matthew_Bird on 2014-07-20
Hey all!

I have a mouse with buttons on the side. For various reasons, **I'd find it really useful if I could use one of the buttons to switch to the previous workspace** (that way, when working on workspace 1 and 2 I could just click the mouse button to rapidly move - I tend to use the mouse more than the keyboard so the current need to switch to the keyboard and use three fingers to switch is less efficient).

I think I've found a way to map my mouse button to a key-input using xdotool.

**Problem.** I can't find a command to switch to the previous workspace. Does one exist, or is it simple to make one?

Thanks so much in advance!
Matt


For anyone who's interested, I'm following Krytarik's advice for the Mouse-button key binding ([http://ubuntuforums.org/showthread.php?t=1694352](http://ubuntuforums.org/showthread.php?t=1694352))

[COLOR=#000000]1.) install "xdotool" through Synaptic[/COLOR]

[COLOR=#000000]2.) go to "System -> Preferences -> CompizConfig Settings Manager -> Commands"[/COLOR]

[COLOR=#000000]- at the first tab, "Commands", enter the respective xdotool command:[/COLOR][COLOR=#000000]
```
xdotool key shift+a
```
[/COLOR][COLOR=#000000] at the tab "Button Bindings" assign the desired mouse button to the newly created command[/COLOR]

---

### Post by deadflowr on 2014-07-20
Why not use the built in settings in ccsm/
Go to Desktop Wall > bindings.
Move within wall will move you around the workspaces.
Move window within wall will move the windows around, if you want.

How many buttons does the mouse have?
And are those extra buttons used by anything?
If they aren't then simple select the mouse option for the manuever you want and set it.
(It will complain and warn about not setting a modifier; that's settings an area of the side you would click on, if you have unused buttons that aren't assigned to anything you can leave those side click-on areas blank)
If that makes sense.

---

### Post by Matthew_Bird on 2014-07-20
Ah, I'll use ccsm. Much easier. Thanks for the tip! I have two mouse buttons, but one is harder to reach than the other.

Unfortunately I just realised that my mouse buttons are bound to back/forward in Chrome. Any idea what's made that binding? Is it default?

Now I just need to find a way to use CCSM to bind a **previous workspace**&#8203; keybinding.

---

### Post by grumblebum2 on 2014-07-20
In the desktop wall plugin enable **Allow Wrap-around**
and select your mouse button for move next.

I actually use the cube with 2 workspaces because I prefer the cube flip effect.

For me the ccsm button bind overrides the chrome shortcut.

---

### Post by Matthew_Bird on 2014-07-21
Works an absolute charm. Thanks so much! This is really useful! :-)

---

