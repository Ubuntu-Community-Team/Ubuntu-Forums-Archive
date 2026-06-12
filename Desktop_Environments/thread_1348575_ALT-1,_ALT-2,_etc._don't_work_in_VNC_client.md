---
title: "ALT-1, ALT-2, etc. don't work in VNC client"
date: 2009-12-07
forum: Desktop Environments
---

### Post by robertbub on 2009-12-07
When I run my VNC viewer (xtightvncviewer), ALT-1, ALT-2, etc. do not get passed to the VNC server.  This is annoying when using Emacs and switching between tabs in various apps (Firefox, gnome-terminal, and mrxvt).

Is there a configuration or switch which can fix this?

Thanks!

---

### Post by akashiraffee on 2009-12-07
Go to Preferences->Keyboard Shortcuts, find what is set to use those alt combos, and set them disabled (use backspace).

Compiz sets some hotkeys too.

---

### Post by robertbub on 2009-12-08
I don't see any shortcuts which specifically capture ALT-1, etc.

But!  When connecting to the VNC server from Windows, I discovered that it too didn't work.  Which makes me thing it's a server-side thing.

I think my xrdp uses xtightvncserver.  Are there any tweaks to allow these sequences to be passed through?

---

### Post by robertbub on 2009-12-25
I made some new (or a couple of weeks ago :)) discoveries:[LIST]
[*]Fluxbox was capturing some ALT-1, etc.  I commented out the relevant lines in ~/.fluxbox/keys .
[*]X Windows wasn't dealing with the ALT key properly; I did the xmodmap trick (on the xmodmap man page) to map ALT to META.
[*]starting TightVNC Viewer on Windows with the Scroll Lock (ScrlLk) key seems to make things (all ALT key operations) work perfectly.
[/LIST]However, I still am unable to make xtightvncviewer pass the ALT key for (ALT-1) through.

ALT-1, ALT-2, etc. works perfectly outside of xtightvncviewer (e.g., works in mrxvt with multiple tabs).  **xev** correctly shows Alt_L and "1" when pressing ALT-1.  Because it works with Windows but not Linux, this makes me think this is a bug with xtightvncviewer.

---

### Post by robertbub on 2009-12-29
I made one more discovery.

If I run **xev** locally (the client machine running the VNC viewer), the ALT key emits ALT_L.  If I run **xev** on the host machine (running the VNC server), the ALT key emits Meta_L.  I.e.,[LIST]
[*]local -> *Alt_L*
[*]remote -> *Meta_L*
[/LIST]So, it seems that xtightvncviewer remaps the ALT key somehow.  I cannot find out how to suppress this remapping.  (The ScrollLk trick doesn't seem to work with xtightvncviewer unlike the Windows VNCViewer.)

---

### Post by robertbub on 2009-12-29
It appears that through the proper manipulation of xmodmap (**xmodmap -e 'add mod4 = Alt_L'**), the ScrollLk key trick seems unnecessary.

And, in fact, everything works, including both Windows VNCViewer and xtightvncviewer.  Everything, that is, except Firefox.  I just could not get ALT-Left to go back a page.  There seems to be a strange bug where if both mod1 and mod4 include an Alt key, it rejects both.  As a workaround, I only add Alt_L to mod4 (so it appears in both mod1 and mod4) and leave Alt_R only in mod1.  So, I can do Alt_R-Left to go back a page.  (I could not figure out a way to manipulate Firefox to accept the Alt key in the way I want it.)

---

