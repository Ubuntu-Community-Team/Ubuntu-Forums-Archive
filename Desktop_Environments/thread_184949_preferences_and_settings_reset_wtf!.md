---
title: "preferences and settings reset? wtf!?"
date: 2006-05-30
forum: Desktop Environments
---

### Post by veratyr on 2006-05-30
Very strange. Just updated last night and restarted after getting home from work today. Now my dapper is all messed up. The icons in the menus don't load. If i want to delete something I'm typing I can't just hold backspace. I have to hit backspace each time i want to delete a character. My system monitor on the panel has all the colors set to black now. My mouse is much more sensitive. The trash icon is now visible on my desktop even though I had set it to be hidden. The values in gconf/apps/nautilus/desktop were also changed from boolean to integer. I'm assuming a lot of other values got changed cause my nautilus display behavior is all changed as well. I also see file sizes displayed for files on my desktop now...? So much crap has changed on me its going to take forever to track it all down and fix. Things were going so well too, and now it's 2 days till final.

---

### Post by veratyr on 2006-05-30
Just tried fixing my mouse sensitivity and now the acceleration slider bar seems borked. It just goes back to slow each time i try and move it. now my mouse is stuck on slug mode. :evil:

---

### Post by joepotter on 2006-05-30
I have no clue what happened to you.

If it were me I would try "sudo rm -rf .*" and wipe out all settings and then log back in and see if it at least goes back to default and can be set.

Or, you could try making a new user and logging in as that user to see what that is like.

Good luck.

---

### Post by slimsam1 on 2006-05-30
Woah there! How about a 
```
cd
mkdir oldconfigs
sudo mv .* oldconfigs/
```

instead of the rm -rf?

---

### Post by towsonu2003 on 2006-05-31
[QUOTE=slimsam1]Woah there! How about a 
```
cd
mkdir oldconfigs
sudo mv .* oldconfigs/
```

instead of the rm -rf?[/QUOTE]
I strongly agree... plus if you miss the point (.) by accident, your screwed...

---

### Post by henriquemaia on 2006-05-31
[quote=towsonu2003]I strongly agree... plus if you miss the point (.) by accident, your screwed...[/quote]

One more to agree. Just to highlight that there is no undelete in ext3.

---

