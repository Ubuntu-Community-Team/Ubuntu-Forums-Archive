---
title: "Wierd problem: window headers have gone, is in disappeared"
date: 2007-04-26
forum: Desktop Environments
---

### Post by bbrand on 2007-04-26
After booting today something weird, never seen it before:

- After starting any app the top border (what I am calling the header) of the window is not constructed properly, in fact it is completely gone and the menu of the app is the top of the frame now. That means I cannot move or minimize the window. They open "stuck" to the top of my screen and the window covers the gnome menu bar.

- I have now only 1 desktop session available.

This started "out of the blue" this AM. 

Any ideas on how to reset this in gnome? It is as if the gnome session is not completely built correctly.
Where do the gnome setup file reside?

HELP PLEASE...

---

### Post by Rinzwind on 2007-04-26
Goto a terminal session and type
metacity

If al goes well you should have them back.

Have you got Beryl or Compiz installed? I think I read somewehere that this happens when you do NOT have 3d rendering on.

---

### Post by bbrand on 2007-04-26
Excellent!! thanks!!

Yup, that did the trick. 

Now why does metacity bomb and start automatically ...

No Beryl or Compiz installed,I did install "DVR" yesterday, but that is unrelated.

OK, got a workaround, thanks. When I figure what what really is happening then I will post the answer.

Thanks Rinzwind, you saved the day!!

---

### Post by bbrand on 2007-04-26
Got is back to being stable. Not really sure why but this worked:

Open terminal session, enter: metacity, the headers and sessions reappear fixing my earlier problem.

To make this stick:

System -> Preferences -> Sessions

Session Options TAB -> Save the current session

What I think happened is that the last time the session was saved (automatically) it saved it without a "metacity" entry. 

Needless to say in that same TAB I have cleared the "Automatically saves changes to session" check box. I want full control now.

Thanks again!!

Ben

---

### Post by kc0eks on 2007-04-26
I have had this happen numerous times in both edgy and now feisty. I havent used the metacity trick yet, but now I know ;)

---

