---
title: "Disabling F1 (don't want Help)"
date: 2005-01-29
forum: Desktop Environments
---

### Post by grubble on 2005-01-29
Hi, this must be really simple, but I can't figure it out.

I have a tiny keyboard, and I keep hitting F1 instead of Esc, and that brings up Help. I'd like to disable F1. I have looked in the Keyboard Shortcuts and a number of other applets but I can't find it.

If someone could clue me in I'd be most grateful.

Thanks,
G.

---

### Post by dare2dreamer on 2005-01-29
xmodmap is your friend:

A few relevant links:

[http://www.princessleia.com/Windowsbind.html](http://www.princessleia.com/Windowsbind.html)
[http://web.mit.edu/answers/xwindows/xwindows_xmodmap.html](http://web.mit.edu/answers/xwindows/xwindows_xmodmap.html)
[http://www-h.eng.cam.ac.uk/help/tpl/unix/xkeys.html](http://www-h.eng.cam.ac.uk/help/tpl/unix/xkeys.html)

and of course the ubiquitous RTFM: :-)

```
man xmodmap
```

The above should give you the basic idea. Oddly enough, ran into this question not two nights ago. Good timing for both of us I guess.

---

### Post by Jad on 2005-01-29
**Tips:** 
- Get real keyboard
- Get a tiny fingers?
- Remove the F1 button from your keyboard?
- Stop hitting ESC!

---

### Post by grubble on 2005-01-29
[QUOTE=Jad]
- Get real keyboard
[/QUOTE]

It's a laptop. Atttaching a full keyboard to it is possible, but defeats the purpose, and damned impossible on the bus.

[QUOTE=Jad]
- Get a tiny fingers?
[/QUOTE]

Extreme body modification isn't my thing

[QUOTE=Jad]
- Remove the F1 button from your keyboard?
[/QUOTE]

No, I might need it sometime

[QUOTE=Jad]
- Stop hitting ESC!
[/QUOTE]

Yeah right. It's kinda crucial in vi...

---

### Post by Jad on 2005-01-29
Hmm 
How about quiting using computers :-)

---

### Post by grubble on 2005-01-29
[QUOTE=dare2dreamer]xmodmap is your friend:

A few relevant links:

[http://www.princessleia.com/Windowsbind.html](http://www.princessleia.com/Windowsbind.html)
[http://web.mit.edu/answers/xwindows/xwindows_xmodmap.html](http://web.mit.edu/answers/xwindows/xwindows_xmodmap.html)
[http://www-h.eng.cam.ac.uk/help/tpl/unix/xkeys.html](http://www-h.eng.cam.ac.uk/help/tpl/unix/xkeys.html)

and of course the ubiquitous RTFM: :-)

```
man xmodmap
```

The above should give you the basic idea. Oddly enough, ran into this question not two nights ago. Good timing for both of us I guess.[/QUOTE]

Well, xmodmap didn't even want to start, and I'm not sure it even has anything to do with it, it's more of a Gnome Keyboard Shortcuts issue in this case. I did R TFM but drew a blank.

Anyway, I side-stepped the issue. First I mapped F1 to Screen Capture in the Shortcuts applet. That stopped Help from popping up. Then I mapped Screen Capture to disabled, and now F1 neither captures nor helps.

The end :)

---

### Post by HeWhoE on 2007-04-15
I'm using gnome-terminal 2.16.1, which allows us to disable keyboard shortcuts.

1.  Click on "Edit" in the menu toolbar.

2.  Click on "Keyboard Shortcuts..."

3.  In the "Keyboard Shortcuts" window, scroll down to the bottom to the "Help" section and change the keybinding for "Contents" to something else, or disable it.

---

### Post by Jinx-Wolf on 2008-02-18
> **HeWhoE said:**
> I'm using gnome-terminal 2.16.1, which allows us to disable keyboard shortcuts.

1.  Click on "Edit" in the menu toolbar.

2.  Click on "Keyboard Shortcuts..."

3.  In the "Keyboard Shortcuts" window, scroll down to the bottom to the "Help" section and change the keybinding for "Contents" to something else, or disable it.

This only disables it for the Terminal.

I'm trying to use xmodmap, and I've gotten pretty far, but I lack complete understanding on how to use it.

I read the man page, but I'm still having difficulty

On my system F1 is assigned the number 67.

So you'd thinkg :xmodmap -e 67=whatever" would change the function, instead, it says it's an "unknown command line"

[I need to figure this out, because my cat likes sleeping on my desk, and he lays his head on the F1 key, causing a ton of help windows to fill the screen]

---

### Post by xlinuks on 2008-07-04
From February:
> 
[I need to figure this out, because my cat likes sleeping on my desk, and he lays his head on the F1 key, causing a ton of help windows to fill the screen]
I'm also looking for how to disable F1 for I got my issues with it, but your reason for disabling it is the funniest in the world.

PS: this thread helped me:
[http://ge.ubuntuforums.com/showthread.php?t=734430](http://ge.ubuntuforums.com/showthread.php?t=734430)

---

