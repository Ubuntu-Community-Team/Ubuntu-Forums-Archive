---
title: "How To Clear GNOME Games Score?"
date: 2006-07-09
forum: Gaming &amp; Leisure
---

### Post by sooqing on 2006-07-09
I was playing Mines and I wished to clear my high scores. How do I do that?

---

### Post by sooqing on 2006-07-09
anyone?

---

### Post by sooqing on 2006-07-09
anyone?

---

### Post by Schalken on 2006-07-09
After going to 'Places' -> 'Search for Files...' and searching for 'gnomine' on the whole hard drive I found the scores are stored in the files '/var/games/gnomine.Large.scores', '/var/games/gnomine.Medium.scores', '/var/games/gnomine.Small.scores' and '/var/games/gnomine.Custom.scores'.

(BTW I found out it was called 'gnomine' by going into Alacarte and seeing where the menu entry pointed to)

Since it's not in your home directory you will need to use 'sudo' to edit the files. Just enter 'sudo gedit /var/games/gnomine.Small.scores' in the terminal, delete it's contents and save. Repeat for the other three files and whala your high scores have been erased.

That's something they should have included, though. In the spirit of open-source goodness, maybe you can find the Gnomines project (would you call it a project?) page and request there to be a 'Clear High Scores' button. :D Then again, maybe like an old arcade machine, your not supposed to be able to clear the High Scores.

---

### Post by EGadZooks on 2008-09-04
Ok, tried that, and it still says Great Work, but unfortunately your score did not make the top ten.  Even if I delete said files, it still tells me that I didnt make the top ten, and doesn't generate new ones.  Are there any other places where top scores are recorded and kept?  Using Gutsy here.

---

### Post by m.owen on 2009-01-17
Only just found this thread whilst trying to sort the same issue out for my son! :-)

After deleting the contents of the files, type

sudo chown root.games /var/games/gnomine*

and then

sudo chmod 664 /var/games/gnomine*

The ownership & permissions of the edited files were different to the others in the directory and after changing them the new scores were saved again.

---

### Post by ds3 on 2009-02-24
If you use the Syanaptic Package Manager and mark Gnome Games for COMPLETE removal, when you reinstall the games the scores will have been cleared.

---

