---
title: "Double-click quit working in KDE applications"
date: 2006-08-13
forum: Desktop Environments
---

### Post by _axiom_ on 2006-08-13
I am *not* refering to single vs. double clicking to launch files in Konqueror.

What has quit is:

Being able to double click a titlebar and having it maximize (Yes, it is still set to do this.  It always did this before, and inexplicably quit working.  I changed the setting back and forth, hitting "apply", but to no effect)

Double clicking messages in kmail to bring them up in a new window.  (As far as I know, there is no other way to do this)

Double clicking in google maps to zoom in in Konqueror.  (This still works in firefox, although konq, when it did work, was the only browser to show that cool zooming in animation before loading the higher-res imagery)

Double clicking still works in gtk apps.  The double click speed looks sane in kcontrol.  Any ideas?

---

### Post by aysiu on 2006-08-13
Any time I've lost functionality in KDE, it's because I installed a new (broken) theme or icon set. Did you?

---

### Post by _axiom_ on 2006-08-13
I haven't installed any new themes or iconsets, but I did have a weird problem with the ktorrent mimetype icon conflicting with some KDE thing, (which seems fine now).

The question is, how did you get the functionality back?  I recently upgraded to KDE 3.5.4, but I still have the same problem.  Is there some settings folder that can be restored to defaults?  

What strikes me as really strange is that I can go into kcontrol, and see the setting for double-click to maximize window, and turn it off and on, yet having no effect.  This seems like a deep KDE bug...

---

### Post by aysiu on 2006-08-13
This may be a bit extreme, but you can reset all your KDE settings with this command: ```
mv ~/.kde ~/.kde.old
``` You may have to log out and log back in again for the changes to take effect.

---

### Post by _axiom_ on 2006-08-21
I ran the command you suggested, and it did fix double-click, but I lost more setting than I reall wanted to, so I tried to run it in reverse:
```
mv ~/.kde.old  ~/.kde
```

Some settings came back, but I still don't have any mail or to-dos in kmail.

Is there another way I should route this command?

There seems to be no 'undo' button in Konsole...

---

### Post by aysiu on 2006-08-21
It's possible that ```
mv ~/.kde.old ~/.kde
``` might not have worked because the ~/.kde directory already existed. I would have done something like ```
rm -rf ~/.kde
mv ~/.kde.old ~/.kde
``` but it's a bit late for that.

When you go into Konqueror and press Alt-V, then H to see hidden directories, is there still a ~/.kde.old folder in there somewhere...? If so, your old KMail stuff should be in there.

---

### Post by _axiom_ on 2006-08-27
Hey, thanks I did get my kmail back, but now I have *The KDE Setup Wizard* coming up every time I start kde.  I went through it once, but it still comes up. I have been just clicking cancel.

I am guessing that something is terribly wrong with my .kde forlders permisions.

I tried this command:
```

axiom@axiom:~$ sudo chown -R axiom axiom
```

But it didn't really have any effect.

P.S.  The double-clicking didn't work becuase the speed got set to 2 msec.  I don't know how that happened, but I set that back and it works now

---

### Post by aysiu on 2006-08-27
What you should do is ```
sudo chown -R axiom:axiom /home/axiom/.kde
```

---

### Post by _axiom_ on 2006-08-27
I did this, but the The *KDE Setup Wizard *is still coming up everytime KDE starts. I have been seaching for others who have had this problem, but don't seem to find them.

---

### Post by aysiu on 2006-08-27
> **_axiom_ said:**
> I did this, but the The *KDE Setup Wizard *is still coming up everytime KDE starts. I have been seaching for others who have had this problem, but don't seem to find them.
Actually [you're not the only one experiencing that](http://ubuntuforums.org/showthread.php?t=242467).

---

