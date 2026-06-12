---
title: "Screenlets 'Notes' Properties Not Saving"
date: 2008-01-27
forum: Desktop Effects &amp; Customization
---

### Post by alsamman on 2008-01-27
How come when I make new notes from screenlets, the settings dont save when I create a second one.
ie. I create a note with font X and adjust it however i want, when I make a second note, the settings are all default and I have to re adjust the new note all over again.
So is there a way where I can set my settings for my notes to a default so that every single note I put on the desktop, I don't have to change font, position, etc.

---

### Post by santiagoward2000 on 2008-01-27
> **alsamman said:**
> How come when I make new notes from screenlets, the settings dont save when I create a second one.
ie. I create a note with font X and adjust it however i want, when I make a second note, the settings are all default and I have to re adjust the new note all over again.
So is there a way where I can set my settings for my notes to a default so that every single note I put on the desktop, I don't have to change font, position, etc.

Hi!
Have you tried deleting that screenlet? I had a similat problem with another screenlet. Try right click on it and choose **Delete Screenlet...**. Then go to **/home/username/.config/Screenlets** and delete the **Notes** folder. This would delete the settings.
Then open it again and see if the new settings are saved.
Cheers!

---

### Post by alsamman on 2008-01-27
unfortunately that didnt work:(
It gets annoying whenever you make a new note it doesnt take the settings of the previous notes I have on the desktop because it gets frustrating having to change to my desired settings everytime I make a new note](*,)

---

### Post by santiagoward2000 on 2008-01-27
> **alsamman said:**
> unfortunately that didnt work:(
It gets annoying whenever you make a new note it doesnt take the settings of the previous notes I have on the desktop because it gets frustrating having to change to my desired settings everytime I make a new note](*,)

:( Sorry to hear that! Try opening a terminal, and type:
```
screenlets-manager
```
You should see the screenlets window. Then, enable Notes and see if you get any error on the terminal.

---

### Post by alsamman on 2008-01-28
i did that and i did not get any errors when i launched a new note all it said was "Note" and nothing else. Your help is very much appreciated.

---

### Post by alsamman on 2008-01-28
bump

---

### Post by alsamman on 2008-01-29
bump

---

