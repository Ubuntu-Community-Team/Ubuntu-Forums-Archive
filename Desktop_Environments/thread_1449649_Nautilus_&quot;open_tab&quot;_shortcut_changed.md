---
title: "Nautilus: &quot;open tab&quot; shortcut changed"
date: 2010-04-08
forum: Desktop Environments
---

### Post by alex.kirchen on 2010-04-08
Hello =)!

I am having trouble with Nautilus since yesterday:
The "New Tab" shortcut changed from "Ctrl-T" to "D" so now each time I press the D key there is a new tab that appears and it's quite annoying...

Did anyone already have this kind of problem ?

---

### Post by micio on 2010-04-08
No I don't, however you should be able to fix through gconf2-editor
Browse until nautilus and change the key!

Micio

---

### Post by alex.kirchen on 2010-04-08
No, I already looked all the keys related to Nautilus in the GCONF Editor and there is no option that defines a shortcut or a hotkey =/...

---

### Post by alex.kirchen on 2010-04-08
Okay I found where the problem came from:

A while ago I had checked the option "Editable menu shortcut keys" in the System>Preferences menu, "Interface" tab, and I hadn't unchecked it.
This option allows you to modify the shortcuts of a Gnome application by just hovering the menu command and pressing a shortcut.
 
And so I must have entered a new shortcut by mistake, but now it's fixed =) !

---

### Post by leona on 2012-01-19
HI I am having the same problem.
New tab is assigned to 'P' I don't know why or how it happened.
I can not find how to remove / change this.
I do not have an 'Interfaces' Menu in Preferences.
Please how can I solve this, its really getting annoying!

---

### Post by leona on 2012-01-19
Ok Answering my own question, but after a bit of digging around I fixed this.
Firstly for some bizzare reason an option was enabled that allows you to over over a menu item with your mouse and if you click while you press a key it changes the short cut key, really annoying, I don't remember EVER enabling that stupid feature, this is how you get your sanity back!
Hover over the menu option giving you the trouble, in my case 'New Tab' and press Ctrl and T (or the key you wish to be assigned to it), it will then return to Ctrl T).
Really helpfully, once this stupid feature was enabled, Gnome decided to remove the ability to turn it off, so to disable it you need to do the following.
Run gconf-editor from the terminal (I've got it in my Applications menu) and go to desktop > gnome > interface > can_change_accels remove the 'tick', exit, all done!

Aww now you can breathe easy again, relax all is well........

---

### Post by TuxProbe on 2012-04-21
thumbs up to the heads up in regards to accel option  :D

---

