---
title: "zsnes"
date: 2008-05-01
forum: Gaming &amp; Leisure
---

### Post by d20diceroller on 2008-05-01
For some reason I can't get zsnes to save game states. I have everything else working great, but it always says it was unable to save. I went into the path options and set the path up to the /.znes folder. Before that it pointed to a folder in my home directory, but it too was unable to save. I am at a loss. Does anyone have any idea?

---

### Post by Belak on 2008-05-01
> **d20diceroller said:**
> For some reason I can't get zsnes to save game states. I have everything else working great, but it always says it was unable to save. I went into the path options and set the path up to the /.znes folder. Before that it pointed to a folder in my home directory, but it too was unable to save. I am at a loss. Does anyone have any idea?

What output do you get when you run zsnes from a terminal and try to save it?

---

### Post by acoustibop on 2008-05-02
ZSES was originally coded as a Windows (or DOS) application, d20diceroller.  It doesn't handle paths well in Linux because it fails to differentiate between upper and lower case in paths - notice that when you type paths in the GUI configuration, they come out as all upper case, regardless of what you type?

One solution is to edit your configuration (~/.zsnes/zsnesl.cfg) so that the paths read with the appropriate upper and lower case characters.  Additionally, if there are any spaces in the the paths, either put a backslash before each space or enclose the paths in inverted commas ("").

To avoid these problems, I always make sure my zsnes saves, save states, ROMs etc are in locations (I keep them on a separate partition so I can access them from other OS installations as well) that don't have upper case characters or spaces in their paths.

---

### Post by travlemon on 2010-06-25
> **acoustibop said:**
> ZSES was originally coded as a Windows (or DOS) application, d20diceroller.  It doesn't handle paths well in Linux because it fails to differentiate between upper and lower case in paths - notice that when you type paths in the GUI configuration, they come out as all upper case, regardless of what you type?

One solution is to edit your configuration (~/.zsnes/zsnesl.cfg) so that the paths read with the appropriate upper and lower case characters.  Additionally, if there are any spaces in the the paths, either put a backslash before each space or enclose the paths in inverted commas ("").

To avoid these problems, I always make sure my zsnes saves, save states, ROMs etc are in locations (I keep them on a separate partition so I can access them from other OS installations as well) that don't have upper case characters or spaces in their paths.

Just wanted to confirm that this worked for me!  In Windows, upper and lower case letters do not make a difference in filenames like in Linux.  I made the change in the config file and it worked perfectly. Thanks!

---

