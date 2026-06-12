---
title: "Right click context menus"
date: 2009-12-26
forum: Desktop Environments
---

### Post by TheCat on 2009-12-26
I'm a bit confused about the right click context menus.  I am running a fresh install of Karmic.  I did some searching and found "Nautilus Actions Configuration" but couldn't get it to work, so I disabled it.  Here is what I am seeing:

file.prop -> right click offers
[LIST]
[*]Open
[*]---------
[*]Open with notepad
[*]Open with OpenOffice.org Word Processor
[*]Open with Other Application
[/LIST]

file.txt -> right click offers
[LIST]
[*]Open with gedit
[*]---------
[*]Open with notepad
[*]Open with OpenOffice.org Word Processor
[*]Open with Other Application
[/LIST]

file.sh -> right click offers
[LIST]
[*]Open
[*]---------
[*]Open with >
[LIST]
[*]gedit
[*]notepad
[*]OpenOffice.org Word Processor
[*]---------
[*]Other Application
[/LIST]
[/LIST]

Why are these different?  It seems to say that both .prop and .txt are recognized as plain text files.  What can I do to get "open with gedit" associated with *.prop files?

---

### Post by hariks0 on 2009-12-26
Open one .prop file once with 'Other application'. Select gedit from the populated applications list. Next time you right click a .prop file, open with text gedit will be there.:)

---

### Post by TheCat on 2009-12-26
I tried that, but it doesn't change anything.  gedit is still not offered in the list.

---

### Post by hariks0 on 2009-12-27
> **TheCat said:**
> I tried that, but it doesn't change anything.  gedit is still not offered in the list.

To the contrary, the dummy.prop file is opened by gedit by default. BTW, what are .prop files?

---

### Post by TheCat on 2009-12-27
Well, sorry to say, your "to the contrary" is apparently only working that way on your workstation and not on mine.  On my new install of Karmic, when I click on file.prop, it offers me "run in terminal | display | cancel | run" and never offers gedit as an option.  This despite several times right clicking > open with other application > gedit which works but doesn't change any of the future behaviours of Nautilus.

The prop file is a settings file for BrettspielWelt.

Thanks for the suggestions, but unfortunately they didn't work.

---

### Post by TheCat on 2009-12-27
Ah, I figured it out.  You were right, when I created a new file named dummy.prop, it opened in gedit.  My original file was set to +x for some reason, and that explains the odd behavior.

---

