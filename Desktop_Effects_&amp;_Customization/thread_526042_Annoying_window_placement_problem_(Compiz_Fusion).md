---
title: "Annoying window placement problem (Compiz Fusion)"
date: 2007-08-15
forum: Desktop Effects &amp; Customization
---

### Post by GFree678 on 2007-08-15
I've noticed an unusual problem with my setup. For some reason, if I have a program running that when it closes, also saves its window position, when it loads up again it doesn't actually place the window exactly where it closed, but a tiny bit down and to the right, almost like a cascade. This happens ONLY with programs which explicitly tell the window manager where to place the window, and not with programs that just dump the window where it likes.

It also affects certain programs which can maximise to full screen and return to desktop, like SMplayer and VMware fullscreen mode. I'm thinking this has to be a specific issue with the window placement rules in Fusion and/or emerald, but I have no idea what to do to fix this. The problem doesn't occur when just using Metacity.

I've run fusion in the past and never had this issue. Maybe it was a change in a recent build, I dunno.

...

UPDATE: Woah, just found out the fix. CompizConfig Settings Manager -> Place Windows -> uncheck Workarounds. Very nice now, but does anyone know what workarounds specifically this refers to?

UPDATE: Nope, spoke too soon. Unchecking workarounds simply fixed Nautilus by not remembering its location, but things like SMPlayer are still affected. This is hugely frustrating if you suffer from it.

---

### Post by rvm4000 on 2007-08-15
Recents versions of smplayer have an option to not remember the position on the screen, so it won't tell the window manager where it should be placed.

---

### Post by GFree678 on 2007-08-15
I know, but I'm just using SMPlayer as an example. Several other programs have the same issue, and simply resolving SMPlayer isn't gonna fix things when I know the problem is with the window manager itself.

Besides, even with SMPlayer I'd like it to remember my position, specifically an above-left center location. With metacity running it works perfectly, but fusion likes to move it around, and that's no fault of SMPlayer itself.

---

### Post by Bunchofmails on 2007-08-28
I am irritated by the same bug. All my applications, terminal, firefox all seem to start at some corner under the top panel. I have to bring them to the usable real estate everytime I start them. They dont remember their positions anymore. Happens only with Compiz fusion on my Thinkpad T41 with ATI Radeon 7500 and not with beryl.

---

### Post by sicofante on 2007-10-20
Very irritating indeed. I'm very surprised CF has actually destroyed a very important usability issue.

---

### Post by Faud on 2007-10-20
> **Bunchofmails said:**
> I am irritated by the same bug. All my applications, terminal, firefox all seem to start at some corner under the top panel. I have to bring them to the usable real estate everytime I start them. They dont remember their positions anymore. Happens only with Compiz fusion on my Thinkpad T41 with ATI Radeon 7500 and not with beryl.


Did you try going to the ccsm manager and then going to the place window plugin and changing it from smart to centered ?

---

### Post by evets on 2007-10-29
The setting that did it for me was Advanced desktop Effects Settings>Place Windows>Fixed Window Placement. I set mine to All, and 30 X and 30 Y. 

Now they are centered just fine for me.


Thanks for the thread.

---

### Post by sicofante on 2007-10-29
After using the centered settings in CCSM's Place Windows for some days, this is my feeling on the subject:

- Applications that take care of placement will remember positions fine.

- Applications that don't care about its placement will start centered.

Since system developers can't prevent every bad practice from application developers, I guess this is all we can expect. I wish Gnome had stricter rules for application developers (much like OSX does), but I guess that's as good as it gets for now.

---

### Post by Githlar on 2007-11-22
I find myself having to use the Place Windows plugin also. If I don't, windows open with the title bar under the top panel as mentioned above. However, with it enabled, I get very strange results in some places. For example: vncviewer. When I hit the F8 button, it is supposed to pop up a menu under the cursor (with Compiz Fusion off), but with the Place Windows plugin enabled, it throws it off into a corner and I have to drag my mouse all the way over to where it's thrown. If only there was a way to use the default GNOME positioning. In the default, you don't have it throwing windows wildly and Put Windows would keep that same "Constrain Y" feature that shows up in the "Move Windows" plugin. But, I have to have it installed if I don't want to have to move a window every time I open it.

---

