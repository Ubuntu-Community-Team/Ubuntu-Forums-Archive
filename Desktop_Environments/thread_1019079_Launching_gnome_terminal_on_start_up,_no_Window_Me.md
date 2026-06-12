---
title: "Launching gnome terminal on start up, no Window Menu"
date: 2008-12-22
forum: Desktop Environments
---

### Post by Vpc on 2008-12-22
I have set gnome-terminal to launch on start-up via Sessions Preferences in the System menu. However, when gnome desktop is loaded, the character terminal appears in the top-right corner of the desktop without a Window Menu so I can't minimize or move the character terminal. 

Why is this? Is there any way I can launch the gnome-terminal on startup such that it appears inside a standard window with a Window Menu?

Thanks.

---

### Post by Vpc on 2011-09-09
To clarify, the Window menu appears hidden under the top menu bar. Using alt-f7 I am able to move the terminal window down so the Window menu becomes accessible but it would be nice to be able to make it so that the top of the terminal window doesn't appear hidden on start up.

---

### Post by stinkeye on 2011-09-09
Have you been trying to figure this out for 3 years? :confused:

Try using this as your startup command.
```
bash -c "sleep 10 && gnome-terminal"
```

and/or if your using compiz
you could set the placement mode for new windows as **centred**.
ccsm  > window management > place windows

---

### Post by Vpc on 2011-11-09
> **stinkeye said:**
> Have you been trying to figure this out for 3 years? :confused:

Try using this as your startup command.
```
bash -c "sleep 10 && gnome-terminal"
```

and/or if your using compiz
you could set the placement mode for new windows as **centred**.
ccsm  > window management > place windows

I think the problem stopped after I recently upgraded to Lucid 10.04 and turned off Desktop Effects via System > Preferences > Appearance > Visual Effects

It's one of those problems that's easy to forget, just got use to moving the terminal window using alt-F7. I may have tried using 'sleep' as you suggested a few years ago but may not have worked. Both are valid suggestions.

---

