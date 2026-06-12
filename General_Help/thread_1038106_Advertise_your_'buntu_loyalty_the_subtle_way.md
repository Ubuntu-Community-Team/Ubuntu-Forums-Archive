---
title: "Advertise your 'buntu loyalty the subtle way"
date: 2009-01-12
forum: General Help
---

### Post by Krydahl on 2009-01-12
It's daft, but I just had to share this mouse theme...

[http://www.gnome-look.org/content/show.php/Ubuntu+Crystal+Cursors?content=66327&PHPSESSID=145f2f576eb050176f3d01debcf39f38](http://www.gnome-look.org/content/show.php/Ubuntu+Crystal+Cursors?content=66327&PHPSESSID=145f2f576eb050176f3d01debcf39f38)

---

### Post by Jameshardy88 on 2009-01-12
Looks really kool though i can't install it for some reason it says it is not a valid theme name, any ideas?

---

### Post by DustinCasler on 2009-01-13
That's AMAZING!

---

### Post by Krydahl on 2009-01-14
> **Jameshardy88 said:**
> Looks really kool though i can't install it for some reason it says it is not a valid theme name, any ideas?

Sorry not to reply earlier, I've been having touble access the forums.

Install for me was: download file, extract, go to directory and follow the instructions in the README (make, then make install, basically). I then copied the 2 directories created (crystalwhite and crystalwhite_nonanim) into /usr/share/icons (but ~/.icons will do just as well if you don't want the theme available to all users).

---

### Post by Jameshardy88 on 2009-01-14
> **Krydahl said:**
> Sorry not to reply earlier, I've been having touble access the forums.

Install for me was: download file, extract, go to directory and follow the instructions in the README (make, then make install, basically). I then copied the 2 directories created (crystalwhite and crystalwhite_nonanim) into /usr/share/icons (but ~/.icons will do just as well if you don't want the theme available to all users).

i sorry im still a bit new to ubuntu but what does this bit actually mean and how exactly do i do it?

"go to directory and follow the instructions in the README (make, then make install, basically)"

sorry to be a pain, i know how to do the rest though

---

### Post by Krydahl on 2009-01-14
No problem.

If you've downloaded the file and extracted it, you must have told the system where to extract it to. You've probably found that using Nautilus. If you click on the extracted folder (it will be called Crystalcursors unless you changed it), you'll see a file called README. Double click on that and it should open, allowing you to read the instructions.

The instructions aren't very complicated, but they do involved using the terminal. To open a terminal, go to applications -> accessories -> terminal.

Once you've got the terminal open, you need to change it into the Crystalcursors folder. You do this by typing

cd /path/to/Crystalcursors

where /path/to should be replaced by the path to wherever you've extracted the folder. So, if you put the folder on your desktop, you'd want "cd /home/yourusername/desktop/Crystalcursors". (If you've put Crystalcursors somewhere below your home directory, you  don't actually need the full path after the cd command, it assumes you're starting from your home unless you tell it otherwise, so actually "cd desktop/Crystalcursors" would do in this example.)

Once in Crystalcursors, type "make" then return. Follow that with "make install" return. 

You should now see the 2 new folders crystalwhite and crystalwhite_nonanim in the same folder as Crystalwhite.

Move them to /home/yourusername/.icons using Nautilus.

---

### Post by Maheriano on 2009-01-14
cool

---

### Post by Jameshardy88 on 2009-01-14
> **Krydahl said:**
> No problem.

If you've downloaded the file and extracted it, you must have told the system where to extract it to. You've probably found that using Nautilus. If you click on the extracted folder (it will be called Crystalcursors unless you changed it), you'll see a file called README. Double click on that and it should open, allowing you to read the instructions.

The instructions aren't very complicated, but they do involved using the terminal. To open a terminal, go to applications -> accessories -> terminal.

Once you've got the terminal open, you need to change it into the Crystalcursors folder. You do this by typing

cd /path/to/Crystalcursors

where /path/to should be replaced by the path to wherever you've extracted the folder. So, if you put the folder on your desktop, you'd want "cd /home/yourusername/desktop/Crystalcursors". (If you've put Crystalcursors somewhere below your home directory, you  don't actually need the full path after the cd command, it assumes you're starting from your home unless you tell it otherwise, so actually "cd desktop/Crystalcursors" would do in this example.)

Once in Crystalcursors, type "make" then return. Follow that with "make install" return. 

You should now see the 2 new folders crystalwhite and crystalwhite_nonanim in the same folder as Crystalwhite.

Move them to /home/yourusername/.icons using Nautilus.

tyvm, got them all installed and up and running now =)

---

### Post by albinootje on 2009-01-14
> **Krydahl said:**
> It's daft, but I just had to share this mouse theme...

[http://www.gnome-look.org/content/show.php/Ubuntu+Crystal+Cursors?content=66327&PHPSESSID=145f2f576eb050176f3d01debcf39f38](http://www.gnome-look.org/content/show.php/Ubuntu+Crystal+Cursors?content=66327&PHPSESSID=145f2f576eb050176f3d01debcf39f38)

Cool and funny! Thanks for sharing! :)

---

