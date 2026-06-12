---
title: "Using Theme Colors Everywhere?"
date: 2009-02-01
forum: General Help
---

### Post by PoopLoops on 2009-02-01
I installed a dark theme (SlicknessBlack) that uses dark backgrounds and light text/foregrounds.  I love it.  Easy on the eyes.  Except when some apps don't *get* with the program and change the background (say in an input box) to gray, but keep their black font.

Two in particular are Firefox and Mathematica.  In Firefox it's not so bad, but like the search box up top?  It's real dark, almost black, and of course black text = I can't read it.

In Mathematica it's even worse because when I go to the preferences menu, any black text stays black, but the entire background is a dark gray.  Ugh!

Is there any way I can have my way with these apps and force them into submission?  Or perhaps just some file I can play with to change this?

EDIT:  Oh, or maybe just some way I could tell these select few programs to just run their default colors and ignore my themes?

---

### Post by IceReaver75 on 2009-02-02
im using a personal modified version of slickness on my computer.  for the firefox issue you can try adding this file to your /home/.mozilla(hidden)/firefox/a bunch of numbers and letters.default/chrome folder and see if it helps any.  On mine I still have the dark address bar but the text is white so you can read it.

---

### Post by johnl on 2009-02-02
The problem is that your theme only affects Gnome/GTK applications.  Firefox has it's own UI toolkit (XUL?) which won't pick up all of the settings.  You might be able to find a firefox theme that matches your GTK theme closely and use that.

Mathmatica probably uses some other UI toolkit as well, but I couldn't tell you which one.

---

### Post by PoopLoops on 2009-02-02
Ahh, I didn't know Firefox had themes too.  I'll look into those.

Yeah, Mathematica has its own thing for the most part, but it lets me control backgrounds of menu popups and backgrounds of search bars.  Since it still keeps black text, it is totally unusable though.  Weird thing is I found some options to change some of the text features, such as crossing it out, or underlining it, which seemed to work, but when I tried to change the text color, it just lol'ed at me and didn't do anything.  Insolence!

---

