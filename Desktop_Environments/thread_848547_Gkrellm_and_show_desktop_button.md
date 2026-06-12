---
title: "Gkrellm and show desktop button"
date: 2008-07-03
forum: Desktop Environments
---

### Post by kerryhall on 2008-07-03
Hey all!

I would like to configure the "show desktop" button somehow so that it doesn't minimize gkrellm (or possibly some other apps)

Is this possible? I was thinking that i could find the script for show desktop, and have it grep for certain process names, and not minimize those.

Thanks!

---

### Post by kerryhall on 2008-07-17
bump

---

### Post by pauper on 2008-07-19
The starting point is apparently here:

```
gedit $HOME/.gconf/apps/panel/applets/show_desktop_button_screen0/%gconf.xml
```

---

### Post by kerryhall on 2008-08-15
bump

---

### Post by kerryhall on 2008-10-22
Bump.

---

### Post by kerryhall on 2008-11-04
Bump.

---

### Post by gtr225 on 2008-11-22
I was thinking that would be great if Gkrellm would stay on the desktop no matter what.

---

### Post by kerryhall on 2008-12-02
Agreed. Now how do we do that? Bump.

---

### Post by Mark76 on 2008-12-27
Set it to be a dock or panel in Configuration/General/Properties

---

### Post by gtr225 on 2008-12-28
I've tried that and it does nothing

---

### Post by Mark76 on 2008-12-28
Worked for me.

---

### Post by kerryhall on 2009-01-02
Awesome, that worked! I think the problem I was having is that gkrellm has to be restarted for that setting to take effect! I was expecting the changes to take place immediately. Thank you for the help! :)

Edit: Now the problem is that when another window is maximized, gkrellm takes up permanent space on the right side of the screen. It would be nice if that didn't happen, but that would be a gkrellm feature request I would imagine.

---

### Post by gtr225 on 2009-01-02
Yes that's my problem now, I want it stuck to the desktop but not on top of other windows or reserving it's own space on the side.

---

### Post by Mark76 on 2009-01-03
What DE are you using?  Maybe there's an option in configuration that'll allow you to override this behaviour.

---

### Post by gtr225 on 2009-01-03
Gnome

---

### Post by Mark76 on 2009-01-03
I got nothing.

I use ROX Desktop and Openbox and I don't know what I did, but I'm having no problem with GKrellm taking up space at the side.

---

### Post by kerryhall on 2009-01-14
Looks like I should bump this then.

---

