---
title: "Stalled login - caused by deskbar applet?"
date: 2006-10-29
forum: Desktop Environments
---

### Post by frostie on 2006-10-29
When I login the desktop loads up everything fom the left edge of the screen as far as the applet and then stops when it reaches where the deskbar applet is sited. (the centre of the panel).

This doesn't load and neither does anything on the panel beyond, the login sequence just hangs there.(neither can I click anything already loaded on the panel or Alt-F2).

At the moment what I do is:
create a gnome-terminal shortcut on the desktop and open it.
$ ps -e
$ kill [deskbar -applet id]

The missing part of the panel (to the right of the deskbar-applet) then instantly loads and (if I choose reload from the popup) so does the deskbar.

Everything is then normal.

Does anyone have any idea how I might go about stopping it from stalling in the first place (apart from remove the deskbar from the panel - I like it).

---

### Post by mitchmao on 2006-10-29
I have the same problem..
had it in dapper and now in edgy too...
well... it stalls just "sometimes"...
but everytime is very very slow in loading at login.. cpu usage grows to 99-100 and after 10secs deskbar is loaded

---

### Post by frostie on 2006-11-08
I've since found that if I set the Deskbar to 'Use all available space' (Preferences > View) rather than a fixed width, as I had it, then I don't have any problem.

(If it stretches out a little too far for your liking you can lock a couple of separators either side to rein it in a bit).

---

