---
title: "Konqueror opens blank folder on startup"
date: 2007-06-10
forum: Desktop Environments
---

### Post by beartard on 2007-06-10
I have an unusual problem that I haven't been able to solve.  When I click on a folder to open in Konqueror, it not only opens the folder I selected, but also opens a blank folder in another tab.  It's an annoyance since I have to go through the "are you sure" dialog to close the window later.  Has anybody else had a similar problem?

---

### Post by qpieus on 2007-06-10
Well, I don't know about the blank tab you're getting, but you can get rid of the "are you sure" dialog by going to:
Settings, Configure Konqueror, web behavior, Advanced options, then uncheck  "confirm when closing windows with multiple tabs"

I tried to duplicate the extra blank tab problem you are seeing and could not. Could you describe again exactly what you are doing when you get this behavior, and I'll try to duplicate it.

---

### Post by bailout on 2007-06-10
What is the address of the blank folder?

---

### Post by MartinJ on 2007-06-10
This has been caused by the View Profile being re-saved at some point in the past, with that blank tab open.

First, open Konqueror at your home directory.  You'll then need to close all extra tabs and click on Settings>Save View Profile...  Check both boxes at the bottom and push Save.  After that, exit and restart Konqueror.  Hopefully it should be fixed but profiles are a bit confusing.

---

### Post by beartard on 2007-06-10
That did the trick!  Seriously, I would never have figured that one out on my own.  There's a checkbox in the "save profile" screen called "save URLs."  Unchecking it did the trick.

Yes, I'm a relatively (re)new(ed) KDE user and the behavior baffled me.  I didn't want to disable the "are you sure?" box, in case I got mouse-happy with useful tabs open.  This solved the problem nicely.  Thanks!

---

### Post by MartinJ on 2007-06-11
Glad to help!

---

