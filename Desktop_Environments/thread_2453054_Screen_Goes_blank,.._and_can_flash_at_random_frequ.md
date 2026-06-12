---
title: "Screen Goes blank,.. and can flash at random frequency and interval"
date: 2020-11-02
forum: Desktop Environments
---

### Post by diyhouse on 2020-11-02
I have to confess to not really knowing what is going here, other than to say the screen can start blanking, ( going completely black ), then coming back,.. and this can then continue every few seconds,.. and get very annoying if trying to do something useful.

when it finishes flashing,. my Vbox windows can be left in a weird state,.. usually much smaller and with their environments all screwed up.... ( but content is still intact,.. I then just have to sort things out,.. until the next time)

My system was doing this with 18.04,.. so I opted to do a clean install of 20.04,.. and its still present....

When I rebuild,.. I trash the root filesystem,.. but keep the /home intact,.. are there any dot files keeping some graphics setting that I should maybe delete?

looking in syslog,.. I have lots of the following:- ( note this is a partial output of syslog,.. )

I have checked the web/forums for ideas but nothing jumps out with the same issues/characteristics... and anything close does not offer a solution.

Any help gratefully received..

// -----------------------------

> Nov  2 20:19:01 mhnuc gnome-shell[1911]: Window manager warning: Overwriting existing binding of keysym 39 with keysym 39 (keycode 12).Nov  2 20:19:01 mhnuc gnome-shell[1911]: Window manager warning: Overwriting existing binding of keysym 73 with keysym 73 (keycode 27).
Nov  2 20:19:01 mhnuc gnome-shell[1911]: Window manager warning: Overwriting existing binding of keysym 31 with keysym 31 (keycode a).
Nov  2 20:19:01 mhnuc gnome-shell[1911]: Window manager warning: Overwriting existing binding of keysym 32 with keysym 32 (keycode b).
Nov  2 20:19:01 mhnuc gnome-shell[1911]: Window manager warning: Overwriting existing binding of keysym 34 with keysym 34 (keycode d).
Nov  2 20:19:01 mhnuc gnome-shell[1911]: Window manager warning: Overwriting existing binding of keysym 33 with keysym 33 (keycode c).
Nov  2 20:19:01 mhnuc gnome-shell[1911]: Window manager warning: Overwriting existing binding of keysym 35 with keysym 35 (keycode e).
Nov  2 20:19:01 mhnuc gnome-shell[1911]: Window manager warning: Overwriting existing binding of keysym 39 with keysym 39 (keycode 12).
Nov  2 20:19:01 mhnuc gnome-shell[1911]: Window manager warning: Overwriting existing binding of keysym 73 with keysym 73 (keycode 27).
Nov  2 20:19:01 mhnuc gnome-shell[1911]: Window manager warning: Overwriting existing binding of keysym 31 with keysym 31 (keycode a).
Nov  2 20:19:01 mhnuc gnome-shell[1911]: Window manager warning: Overwriting existing binding of keysym 32 with keysym 32 (keycode b).
Nov  2 20:19:01 mhnuc gnome-shell[1911]: Window manager warning: Overwriting existing binding of keysym 34 with keysym 34 (keycode d).
Nov  2 20:19:01 mhnuc gnome-shell[1911]: Window manager warning: Overwriting existing binding of keysym 33 with keysym 33 (keycode c).
Nov  2 20:19:01 mhnuc gnome-shell[1911]: Window manager warning: Overwriting existing binding of keysym 35 with keysym 35 (keycode e).
Nov  2 20:19:01 mhnuc gnome-shell[1911]: Window manager warning: Overwriting existing binding of keysym 36 with keysym 36 (keycode f).
Nov  2 20:19:01 mhnuc gnome-shell[1911]: Window manager warning: Overwriting existing binding of keysym 38 with keysym 38 (keycode 11).
.
.
.
Nov  2 20:19:01 mhnuc gnome-shell[1911]: Window manager warning: Overwriting existing binding of keysym 36 with keysym 36 (keycode f).
Nov  2 20:19:01 mhnuc gnome-shell[1911]: Window manager warning: Overwriting existing binding of keysym 38 with keysym 38 (keycode 11).






---

### Post by diyhouse on 2020-11-27
Well I think I got to the bottom of this annoying issue...

The monitor hardware was beginning to fail (12yr old 28" LED screen),... and as it kept resetting itself (on-off),.. it would send random info to the host PC,.. so it in turn would re-config its screen settings.
and make a complete mess of the screen and running windows,.. so not surprising.

Case closed Ma-Lord....:p

---

