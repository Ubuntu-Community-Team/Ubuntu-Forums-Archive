---
title: "Close application with a gesture"
date: 2005-11-15
forum: Desktop Environments
---

### Post by grizzly on 2005-11-15
Hi i installed Kubuntu today earlier i was ubuntu, and i must say even though it runs slowly on my system, i was still totally blown away by it :).  

In khotkeys i am unable to specify a gesture to close a window( or dialog).
what i want to do is specify /(down) gesture to send Alt+f4 or Ctrl+q. But it doesn't works! I can see ^Q being typed in konsole, but i don't get how to modify it to close apps.

I did mange to assign gestures to copy, paste etc so i know how it works.
Is there any list of keys or any documentation regarding this excllent feature?

Also 'Alt+Tab' too wasn't working . 

Thanks

---

### Post by Takis on 2005-11-16
Howdy. I've got some pretty good experience with Khotkeys, and I've started writing up some how-tos, but I have an exam tomorrow so I've been studying up for that. Wait about a day and a bit, and I should have put up more information.

In the meantime, for the Konsole problem, open up Konsole and hit Settings->Configure Shortcuts. Set 'Quit' to Ctrl+Alt+Q, and adjust Khotkeys to match. Konsole normally won't pay attention to basic control sequences (CTRL+Q, CTRL+C, etc) because they often have useful meanings in the terminal.

---

### Post by grizzly on 2005-11-17
Thank god you exist! Up till now I had a feeling i was the only person on the planet interested in khotkeys gestures.
Best of luck for your exams. 
Waiting for your hoto's i think i came across part I of yours.
And do share if can figure out a way to Alt+F4 with a gesture

c ya

---

### Post by grizzly on 2005-11-19
Anybody? I really need this to work, so... 
Is it possible to write some sort of script or something that closes a application?

@takis i tried ctrl+alt+Q - Doesn't works for closing application, though i could close tabs with it in Krusader.

---

### Post by Takis on 2005-11-24
Sorry I've been down at the coast after exams finished. :) Wait *one* more day and I'll put up a how-to that'll show you exactly how to do it. If you wanna know what the basic problem is, it's that most programs will use ALT+F4 by default or maybe CTRL+Q. You can change this in KDE's settings (can't remember what it's called, will post it tomorrow) and then you'll need two KHotKeys entries - one specifically for Konsole, which will need to be a 'generic' type one because you'll need to set a condition that the active window is Konsole, which sends CTRL+ALT+Q (which presumably you've set in Konsole via the shortcuts settings), and the other entry will send ALT+F4 or CTRL+Q (whatever you've set) to all other windows.

Sorry if this is a bit hard to follow, wait a bit and I'll clarify.

---

