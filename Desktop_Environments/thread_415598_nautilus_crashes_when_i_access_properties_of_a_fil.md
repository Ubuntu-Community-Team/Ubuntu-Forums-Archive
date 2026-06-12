---
title: "nautilus crashes when i access properties of a file"
date: 2007-04-20
forum: Desktop Environments
---

### Post by modaniel on 2007-04-20
Can someone please help with this..
i have a problem with nautilus. When i try to access properties of a file or copy files/paste files between windows, nautilus crashes.
If i have run nautilus from the command line i get the following error:

"nautilus: symbol lookup error: nautilus: undefined symbol: eel_ellipsizing_label_new"

I am using ubuntu 7.04 and Nautilus and Gnome 2.18 (i upgraded from 6.10)

I have resolved the problem, it was due to a modification i made a long time ago that i had forgotten about, sorry for the inconvenience.

---

### Post by earobinson on 2007-04-20
can you give us more info about the file, what file system is it on?

---

### Post by earobinson on 2007-04-20
can you post the output of an ls -la in the directory that the file is in and tell us the file name

---

### Post by modaniel on 2007-04-20
actually it doesn't matter which file type i choose or which directory it is in. 
it also happens when i try to interact with the desktop.
I have also discovered that the crash also happens when i try to delete the file with the delete key.

---

### Post by JT673 on 2007-04-20
Hmms...It's probably a GNOME error.  Check for GNOME packages that Feisty might have broke.

---

### Post by modaniel on 2007-04-21
I used the synaptic fix broken packages option and it said that dependencies were successfully resolve d but this hasn't corrected the problem. 
  a google search tells me that eel_ellipsizing_label_new, is a part of the Eazel Extensions Library but reinstalling eel and nautilus hasn't worked.

perhaps this is relevant ... I get the following warnings when i access folders...
Eel-WARNING **: Trying to add a callback for preferences/background_set that already exists.

(nautilus:30462): Eel-WARNING **: Trying to add a callback for preferences/background_color that already exists.

(nautilus:30462): Eel-WARNING **: Trying to add a callback for preferences/background_filename that already exists.

---

### Post by galileon on 2007-05-09
same problem here, but it occurs also whenever i try to copy-paste, cut-paste, drag-drop, move-to-trash, basically any move operation... i'm getting by using the console, but any help to fix this would be appreciated, thanks...

---

