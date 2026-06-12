---
title: "Window Start Positions"
date: 2007-10-29
forum: Desktop Environments
---

### Post by cuscus1986 on 2007-10-29
Hi,

I have just recently started using Ubuntu as my main Linux environment. I have had some exposure to using Linux at university but I do not know much about desktop managers. This is where I have a problem. As you can see from the screen shot below I have installed a nice shiny new color scheme for Gnome and got the latest version of AWN going from the repositories.

My problem comes in where my new windows start. Slightly annoyingly new windows all appear with the title bar tucked underneath the top Gnome panel. This means that I have to go through the business of right clicking the application icon and selecting move. This is especially an issue with dialogs which do not appear in the dock,

Once I maximize the window it sits in the correct spot.

Any info on where I might start looking for a problem would be greatly appreciated.

UPDATE
Found the solution to the problem further down on this thread. If anyone has any idea of why this happened then please let me know.

---

### Post by Jhongy on 2007-10-29
It's a problem with compiz. If you look in the advanced settings for desktop effects, there should be an option for "plac3" windows (perhaps "put", not at home right now). In that menu, you have the optiuon to "enable workarounds". That fixes the problem for me.

Sorry I can't be more specific, but yo uget the idea.

---

### Post by thisbeadam on 2007-10-30
I have the same problem as him, but enabling "workarounds" does nothing. When any of my windows are maximized, they are perfectly fine, but when restored the title bar is stuck underneath the panel bar.


MAXIMIZED

[IMG]http://i209.photobucket.com/albums/bb40/thisbeadam/Screenshot.png[/IMG]


MINIMIZED

[IMG]http://i209.photobucket.com/albums/bb40/thisbeadam/Screenshot-1.png[/IMG]


I have gusty with compiz fusion on a dell inspiron 6000. This just came up...

---

### Post by L815 on 2007-10-30
What worked for me was turning on max effects, then turning them back to whatever setting you want & the opposite if you are already in max.

---

### Post by treris on 2007-11-01
The problem seems to be in the window border theme used by Ubuntu, changing that through 'Appearance'  may solve your problem

---

### Post by cuscus1986 on 2007-11-14
Thank you L815 that seems to have fixed the problem. I went to the Visual Effects tab of the System > Preferences > Appearance window and found that none of the radio buttons were selected for some bizarre reason. Selected max again as it should be and that appears to have fixed the problem.

---

