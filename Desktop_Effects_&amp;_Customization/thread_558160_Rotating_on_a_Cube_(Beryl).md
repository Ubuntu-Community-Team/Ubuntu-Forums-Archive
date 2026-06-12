---
title: "Rotating on a Cube (Beryl)"
date: 2007-09-23
forum: Desktop Effects &amp; Customization
---

### Post by tsumiro on 2007-09-23
Hey, i got beryl running great on my system. i honestly love the features, but i have a problem. i was trying to enable the rain feature using the shortcut, shift, f9, and it didnt work, i tried shift f8, and stuff, and eventually i think i pressed cntrl, alt, f9 and my comp screen went black so i restarted.

now, instead of getting a cube that i can move around my workspaces in, it fades to the next screen instead, and i cant drag windows from workspace to workspace anymore...



help much appreciated.

---

### Post by yuku-aki on 2007-09-23
All I can tell you for sure is that ctrl+alt+F9 is just taking you to another terminal... control, alt, and any F button up to F8, typically, will do that.  You can go back to the default terminal (the one you had open) by hitting ctrl+alt+F7.  

This is a good trick to know when your GUI crashes, or you can't start top for some reason to see what's dragging your system down.  I use htop, the graphical version of top, after re-logging in on terminal 1, (ctrl+alt+F1)  Then sort by R (running) or S (stopped) status, use F3 to search for, then F9 to kill any stopped programs that should be running (Firefox used to do this to me alot) and then ctrl+alt+F7 back to my original terminal, and all is back to normal.

I haven't had any such issues in Beryl yet, but will look into this rain feature, I don't believe I've even tried it yet.  

Btw... what machine/release/kernel etc are you on?  I ask because I'm on a Toshiba laptop, which are notorious for having hardware issues in Linux, but Beryl works great for me.  Maybe the developers had Toshibas, too.  :)

---

### Post by yuku-aki on 2007-09-24
You also may have to restart Beryl by F2->beryl-manager each time you log in until you set it as the default window manager.  That may be why your effects aren't working since you restarted.

If you're lucky, there's a red jewel icon somewhere on your top menu bar, which you can right click, and select Beryl as your active wm.  Otherwise, the F2 command above should suffice.

---

