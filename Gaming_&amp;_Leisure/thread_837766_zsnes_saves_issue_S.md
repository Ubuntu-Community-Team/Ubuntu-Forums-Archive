---
title: "zsnes saves issue :S"
date: 2008-06-22
forum: Gaming &amp; Leisure
---

### Post by zero777zero on 2008-06-22
i'm trying to load saves from an external drive (NTFS). the game loads fines off the external drive but i cant seem to set the path correctly

here is what my path is set to: "/media/931NTFS/3 games/0 software and saves/SNES/saves"
i've tried this: a) case sensitive without parenthesis, b) case sensitive with parenthesis

i tried the advice [here]("http://ubuntuforums.org/archive/index.php/t-664618.html") and put parenthesis around the path but to no avail. after playing a game and saving data (to see where it would save to) i cannot find the saved data! i searched in my external harddrive, my username folder, my file system and my media folder and the .srm is no where to be found. if i restart the game in zsnes the old save is there, even though its not in the path specified. the old save was not overwritten and replaced because the "date modified" is still a day old (when i last played it).

-hardy heron

---

### Post by FranMichaels on 2008-06-22
The default save location is ~/.zsnes/
aka your home folder, .zsnes (press ctrl + h in nautilus as all folders with . are hidden)

Also, is the folder on the ntfs drive read only? I think maybe the spaces in the filename could be messing something up... Are you running zsnes 1.51?

Lastly, when you say parenthesis do you mean quotation marks?
"this folder/games here"
Quotation will help with spaces in the filenames etc.

---

### Post by zero777zero on 2008-06-22
> **FranMichaels said:**
> The default save location is ~/.zsnes/
aka your home folder, .zsnes (press ctrl + h in nautilus as all folders with . are hidden)

Also, is the folder on the ntfs drive read only? I think maybe the spaces in the filename could be messing something up... Are you running zsnes 1.51?

Lastly, when you say parenthesis do you mean quotation marks?
"this folder/games here"
Quotation will help with spaces in the filenames etc.

save found.

ntfs is not read only, i dont think the NTFS is the issue, but i wanted to provide the info in case

yes i'm running 1.51

yes i did mean quotation marks

---

### Post by acoustibop on 2008-06-23
No, NTFS is not the issue (I used to use images, saves etc from an NTFS drive quite successfully), ZSNES is.  It's originally a Windows (or DOS) application and doesn't write paths properly from the GUI.  Notice that, as shown in the GUI, paths are always shown as all upper case, regardless of what you type?

You'll need to edit your #/.zsnes/zsnesl.cfg configuration file appropriately.  Don't forget that if your path has spaces or illegal symbols in it, you'll need to put a backslash before them or enclose the path in inverted commas (""), and that Linux paths are case sensitive.  I always found the best option was always to ensure that any paths I needed to access from Linux were without spaces or illegal characters, and preferably all lower case.

---

### Post by zero777zero on 2008-06-23
well that did it

thanks for helping me track down this config file. the line i changed ended up being this one:

SRAMPath="/media/931NTFS/3 games/0 software and saves/SNES/saves"
which autochanged to this
SRAMPath="/media/931NTFS/3 games/0 software and saves/SNES/saves**/**"

the program needs to be shut down or it will try to revert the path.

thanks for the help on this one!

---

### Post by Bensy on 2008-09-09
OK. My problem was that there was no path assigned to the save folder. I didn't think of it at first because so far every time I installed zsnes, both in Windows and Ubuntu, it used the proper paths by default. Must have been the latest release or something like that.

For the record, none of my keys could use the "/" symbol, so I had to edit the config file manually. It's pretty easy to find where changes must be made.

---

