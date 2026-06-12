---
title: "nautilus and the .dat format"
date: 2008-03-21
forum: Desktop Environments
---

### Post by petrosk on 2008-03-21
Every time I try to open a file with the extension .dat (plain text files, which I read in gedit) in Nautilus I get this Warning message:

> The filename "conv.dat" indicates that this file is of type "dat document". The contents of the file indicate that the file is of type "plain text document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "plain text document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file.

How can I stop Nautilus showing this message and open .dat files just by double-click?

---

### Post by ioluas on 2008-03-22
in nautilus, right click on the .dat file. from the pop-up menu, choose the last option "properties"; a new dialogue opens with few tabs. click on the tab "open with", there will be a list of software capable of viewing this type of file, if your favorite software not listed click on the "Add" button on the bottom to add it and when finished click close and thats it.  next time you click on .dat file it would open without asking stuff.
hope this helped

---

### Post by petrosk on 2008-03-22
Nope, I've already tried that before as well as playing with other options in Properties, but nothing seems to help.

---

### Post by tvtech on 2008-03-22
run gconf-editor  most of the irritating pop up messages and config info is in there and can be disabled from there. up to and including turning off the beep when you try to backspace one too many times in terminal

---

### Post by petrosk on 2008-03-22
OK, problem solved,just in case someone wants to know - I deleted (but backuped) the ~/.local/share/mime directory, which stored the information about overriding the .dat extension, everything's working OK now.

---

