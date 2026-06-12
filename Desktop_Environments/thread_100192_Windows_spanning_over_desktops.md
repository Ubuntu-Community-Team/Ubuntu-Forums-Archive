---
title: "Windows spanning over desktops"
date: 2005-12-07
forum: Desktop Environments
---

### Post by Ruskie on 2005-12-07
Hi all,

Years ago, when I was working on an old Unix machine (I believe it was a DEC box), I had a windows manager that "spanned" windows over multiple desktops. I don't know if I used the right english word: what I mean is that, if you put a window near the border of the active desktop, so that a portion of it is "cut out" of view, it was displayed in the adiacent desktop, so that changing desktop you could see the other part of the window.
This is not only an oddity I believe, because in lower resolutions many linux windows can overflow the desktop, cutting out important part of them. I had this problem, for example, with the System Settings, where I could not press the "Administrator Mode" windows because it was offscreen.

Is there a way to obtain this with Kde 3.4 (or 3.5 at least)? I've looked extensively through windows settings yesterday, but couldn't find any way to obtain that. Anyone can help?

Thank you very much
Marco

---

### Post by curuxz on 2005-12-07
If you have 2 monitors setup and you want one giant desktop, then simply add the Xinerama on option in your xconfig, This is from my /etc/X11/xorg.conf file at the very end...

```


Section "ServerLayout"

	Identifier	"Default Layout"

	Screen		"Default Screen 0"
	Screen		"Default Screen 1" RightOf "Default Screen 0"

	InputDevice	"Generic Keyboard"

	InputDevice	"Configured Mouse"

	Option	"Xinerama" "On"

EndSection


```

That gives me one big desktop and if i move windows between the gap they 'Span' personaly annoying but if thats your buzz then go right ahead, if its to solve the buttons of screen thing then you may want the 2nd screen to be BottomOf not LeftOf the first :)

Hope that helps

---

### Post by shakin on 2005-12-07
Naw, curuxz, I think he wants windows to span workspaces, not monitors. I've seen it before, but never paid much attention to it. It's probably a function of the pager rather than window manager. I think I remember that functionality in Red Hat 5.2 :)

---

### Post by Ruskie on 2005-12-07
[QUOTE=shakin]Naw, curuxz, I think he wants windows to span workspaces, not monitors. I've seen it before, but never paid much attention to it. It's probably a function of the pager rather than window manager. I think I remember that functionality in Red Hat 5.2 :)[/QUOTE]

Uhm... I think you are right but perhaps I've been imprecise...
I do want windows to span workspaces not monitor, but better clarify:

Monitor = piece of hardware measured in inches, with a plug and a vga-cable to attach it to the main pc-box.

Workspace = logical screen that is visible in the monitor when you boot your OS. Kde, Gnome and most windows managers have 4 workspaces, for example.

This said, I believe I should have more precisely specify I want the windows to be able to span workspaces...
I wouldn't use it on a stable basis, however, it would be very nice if it was possible to enable it (best of all if it was a "live" configuration issue and not an .rc or .conf modification) just for those cases when application windows are "malformed" (too big for the resolution they're into) and thus unusable...
I had it on a Unix windowmanager, and I'm talking of many years ago... Can it be done on Kde?

---

### Post by shakin on 2005-12-07
Ruskie, hold Alt while you click the mouse button on a window... it will let you drag the window even if you aren't on the title bar. I think that may be an easier way to view hidden parts of a window on occasion.

---

### Post by shakin on 2005-12-07
** double post. Not sure how I managed to double post 13 minutes apart :)

---

### Post by Ptero-4 on 2005-12-07
Ruskie. What you're probably looking for is fvwm. It's built-in pager span windows across workspaces if you move them against an edge of a workspace. To use fvwm on gnome just kill metacity, start fvwm and logout. The session manager will make fvwm the default wm for gnome. For kde you'll need to set the KDEWM variable to the fvwm path in your shell startup file. KDE will take it instead of kwin.

---

### Post by Ruskie on 2005-12-07
First of all, thank you all.
Ptero, you're probably right, it should have been fvwm; now you mentioned it probably was.
However, I didn't know I can move windows with the Alt key. Since Kde can't do what I want, and I would be obliged to restart X with the new wm, I think shakin suggestion is my choice. :)

Thank you again everybody for your help!
Marco

---

