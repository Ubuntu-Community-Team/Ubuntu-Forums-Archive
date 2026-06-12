---
title: "can't get cube with Compiz"
date: 2008-02-23
forum: Desktop Effects &amp; Customization
---

### Post by Beowulf.1000 on 2008-02-23
I can't get the cube with Compiz like I used to have with Beryl using 7.04. I have 7.10 running on a new laptop and installed compiz with synaptic manager -- no beryl listed like i was able to do with 7.04.  Ok so I go to the Advanced Desktop Effects Settings in the System menu and I can find and checkbox the cube. But when I flip what should be a cube it is like a two sided cube, or rather like flipping to the backside of a wall, no cube. What am I doing wrong? I would like to have a 4 sided cube.

---

### Post by PurposeOfReason on 2008-02-23
Go to the general section and make sure you have four horizontal desktops.

---

### Post by Beowulf.1000 on 2008-02-23
Thank you, that worked,. Actually i just right clicked on my multiple desktops section on the task bar, I had it set for 2x2, changed it to 1 row 4 columns and then I got the cube. Thanks!

> **PurposeOfReason said:**
> Go to the general section and make sure you have four horizontal desktops.

---

### Post by Chipter on 2008-02-23
Ya i had that for a while too.
It depends on how many workspaces you have running.

If you have 2 it'll be a wall, if you have 3 it'll be a triangle, 4 square, 5 pentagon, etc.

---

### Post by bellwells on 2008-02-23
I can't for the life of me figure out how to display the cube.  I've been wrestling with this for 2 days now; done all the searches that can be done; enabled Desktop Effects; checked the appropriate box; have a great openGL nVidia card.  I do have the Wobbly Windows effect, which is pretty cool but no love with the cube.

As a side note here, Open Office is so much better than MS products, especially with regard to manipulating jpegs in a word document.

Ron

Edit: I think my problem stems from the fact I can't access CompizConfig Settings Manager.  It shows up in Preferences, but when I click on it nothing happens. Typing "ccsm" into a terminal returns: 

ronwells@ubuntu:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 43, in <module>
    mainWin = ccm.MainWin(context)
  File "/usr/lib/python2.5/site-packages/ccm/Window.py", line 77, in __init__
    for category in sorted(self.Context.Categories, self.CatSortCompare):
  File "/usr/lib/python2.5/site-packages/ccm/Window.py", line 361, in CatSortCompare
    if self.Context.Plugins['core'].Category == v1:
KeyError: 'core'
ronwells@ubuntu:~$ 

I'm not proficient enough to understand this gobbledy-gook.  Any help would be greatly appreciated.  If I do figure it out, I'll post back.

Ron

---

