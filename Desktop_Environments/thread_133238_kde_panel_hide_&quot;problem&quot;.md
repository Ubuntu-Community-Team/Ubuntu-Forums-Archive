---
title: "kde panel hide &quot;problem&quot;"
date: 2006-02-19
forum: Desktop Environments
---

### Post by mistamcgoo on 2006-02-19
Hi, 

i'm having a little problem with my kde panel since upgrading from 3.4 to 3.5

i have set on "hide" , so it is out of the way when i don't need it, and comes
back up when i "touch"" the bottom of the screen with my mouse pointer

but since the upgrade, when i go to the screen bottom with my mouse pointer, it doesn't pop up anymore, only when i move it to the complete bottom left, where the k menu with the little black arrow or triangle is, it does come up. 

this has happened both on my desktop and laptop since the upgrade.
i tried making the panel size a little bigger, but doesn't help.
(also tried changing the screen vertically with the "hardware buttons", but doesn't help)

i know this is something pretty small as a problem, but it kinda annoys
since it's not what i'm used to, but does anyone know how to solve this? 
i tried the forum help function, but couldn't find anything relevant.

---

### Post by GoldBuggie on 2006-02-20
change the property of **right-click kicker->configure panel->Hiding->Raise When pointer touches the screen** to **Bottom Edge** or whatever place you want

---

### Post by mistamcgoo on 2006-02-20
Thank you very much for the help. So this isn't a "problem", it's a feature i didn't even know about. \\:D/  sweet . I love KDE

i do find it a bit strange my default kde 3.4 setting changed by upgrading to 3.5, though, 
but it works now

---

### Post by zi99y on 2006-02-20
If only I had found this thread sooner, I recreated my entire panel because of this problem!! (worra plonker)

At least it's good to find out what was the problem :rolleyes:

---

### Post by Randomskk on 2006-02-20
I had a slightly different problem, for people searching...
My panel would only hide after I moved the mouse to the left or top edge of the screen (panel was at the bottom), even though it should have hidden after my mouse moved off it.
Go to /home/username/.kde/kickerrc and find where it says "unhidelocation" and then a number (mine was 7) and just delete the line, save, then in a terminal:
killall kicker
kicker

will reload it, problem fixed for me. I couldn't find anywhere on the GUI interface to fix it...
If you have multiple panels, they have really funny rc names, so look in your kickerrc for their names and then the fix is the same.

This is a pretty weird problem, I got it after upgrading to 3.5.

---

### Post by snaga on 2006-06-06
[QUOTE=Randomskk]
My panel would only hide after I moved the mouse to the left or top edge of the screen (panel was at the bottom), even though it should have hidden after my mouse moved off it.
Go to /home/username/.kde/kickerrc and find where it says "unhidelocation" and then a number (mine was 7) and just delete the line, save, then in a terminal:
killall kicker
kicker
[/QUOTE]

I have this same problem after upgrading to Dapper. Unfortunately this doesn't seem to do the trick for me. I cannot find any reference to 'unhidelocation' in any kde rc file.

---

### Post by thedanyes on 2008-03-23
I had this same problem and it annoyed the heck out of me for a month or so (until I googled to find the solution).  The above advice helped me, but wasn't exact.  Here's what fixed the problem for me:

open the file /home/(yourusername)/.kde/share/config/kickerrc in your editor of choice

search for the text 'UnHideLocation' or something similar (many search functions are case sensitive so if you don't find it at first, just do a search for 'ocation' or something until you find it).

Delete that line.

Save the file and restart kicker.

---

### Post by fuzzybyte on 2008-05-02
[https://bugs.kde.org/show_bug.cgi?id=127466](https://bugs.kde.org/show_bug.cgi?id=127466)

seems like they aren't going to fix this bug ever, because kde4 has a new panel (which at the moment doesn't even have the ability to auto-hide).

---

