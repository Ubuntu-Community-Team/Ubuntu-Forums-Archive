---
title: "Gnome panel acting weird..."
date: 2007-06-08
forum: Desktop Effects &amp; Customization
---

### Post by 5407 on 2007-06-08
When I go into a gnome session my panel (I only have one, with a drawer,that has a usual location of the upper right corner of my screen) is now floating in the middle of the right side of my screen, and trying to send it to any edge just makes it rotate in place.  This happened after I changed the resolution back up after accidently reducing it.  Prior to that I had noticed occasionally that upon loading a gnome session my panel would be a little bit over to the left from the corner it should have been in, but upon hiding it it would move over.

This isn't anything that is really important to me to fix, as I prefer KDE anyway, but was just curious if anyone had seen this before or knew how to fix it.

---

### Post by Mozork on 2008-02-22
Same thing here, does anyone know a solution?

---

### Post by RottenBananas on 2008-02-26
Hey,
A similar thing happened to me
Heres how i fixed it

First open up the config editor
I think alt+f2 and typin gconf-editor is the command

then (this may be different based on how many panels you have...just play with the different ones, log out and back in to see the results) go into apps/panel/toplevel/top_panel_screen0 and changed the y value to what you need

My resolution is 1280 by 800 and having a y value of 800 puts my panel at the bottom. So im assuming a y value of 0 will stick it at the top

And then you can  change to x value for its position from left to right

Hope this helps
-Bananas

---

