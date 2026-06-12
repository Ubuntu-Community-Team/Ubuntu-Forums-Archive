---
title: "Window Placement and Cursors"
date: 2008-02-07
forum: Desktop Effects &amp; Customization
---

### Post by Spoken on 2008-02-07
I have 2 problems here

[SOLVED] 1)When i open anything, be it a document or a application or program, it appears it the far far top left every time it opens, and i have to alt + click it to drag it down, because its so far up that the window borders are hidden.  It only started doing this recently, and i do not recall configureing anything that had to do with my windows.

2)My cursor selector is messed up, when i click "install" or "theme folder" , it doesnt do anything, and even when i change from my current cursor back to default, it doesnt even change.  I have tried this after turning off compiz fusion and it still doesnt help.

---

### Post by Therion on 2008-02-07
> **Spoken said:**
> 

1)  When i open anything, be it a document or a application or program, it appears it the far far top left every time it opens, and i have to alt + click it to drag it down, because its so far up that the window borders are hidden.  
Try configuring the [Place Windows]("http://wiki.opencompositing.org/Plugins/Place") plugin and see if that solves the problem.

---

### Post by Spoken on 2008-02-07
Thank you very much, that fixed # 1

But my cursor selector is still messed up , idk if its because of compiz or because or something else. any help?

---

### Post by Therion on 2008-02-07
> **Spoken said:**
> 
Thank you very much, that fixed # 1

No problem.  Glad it worked out.

> **Spoken said:**
> 
But my cursor selector is still messed up...
This problem persists through a restart of **X** via Ctrl+Alt+Backspace and/or after rebooting your system?

---

### Post by Spoken on 2008-02-07
Yes, none of the buttons work , i cant even change my cursor size.  but i have the downloads for a new curso i want to use, only if the app to change them worked lol.

---

### Post by Therion on 2008-02-07
So, if you navigate to System/Preferences/Appearance and try to use the Themes Manager, nothing there is working.  Is that correct?  Not just your cursor selections but you can't change *anything* there?  You can't select any of the pre-installed themes, like "Clearlooks" or "Glider"?  Sorry to ask so many questions but I'm trying to pin down the nature of the problem.

Try using Synaptic, search for “Gnome Art” and install "Art Manager".  See if using that will maybe "jump start" you so you can modify your themes, cursors, etc.  Admittedly I'm grasping at straws.

---

### Post by Spoken on 2008-02-07
oh no lol, i can change my themes to stuff like "glider" and "clearlooks" , and this is when i have compiz fusion enabled, i cant change window borders however, but thats just because i have emerald working in conjunction with fusion.  But neither of those should have anything to do with my cursors right?

---

### Post by slugicide on 2008-02-07
I have the exact same cursor problem as you.

---

### Post by Spoken on 2008-02-07
Only if someone came acrossed it that knew how to help.

---

### Post by Xgen on 2008-02-07
Let me get this right...you have tried adding your custom cursor to your [COLOR="DarkRed"]*[profile]*[/COLOR] .icons folder and changed cursors through System-->Preferences-->Appearance-->Theme-->Customize-->Pointer and logged out and nothing has changed? (Gcursor doesn't work with Gutsy and Heron)

---

### Post by Spoken on 2008-02-07
ok that lets me change my cursors , that i ALREADY have installed, but when i try to install new ones, via system > preferences > cursor selection, neither the install nor theme buttons work.  How am i supposed to install new cursors.

---

### Post by Xgen on 2008-02-08
The Cursor Selection startup command is 'gcursor' which, as stated, doesn't work properly in Gutsy or Hardy. Adding extra cursor folders to your *[profile]* .icons folder should show up under the 'Pointer' tab...don't know if you have to log out. I have added my preferred ones there.

---

