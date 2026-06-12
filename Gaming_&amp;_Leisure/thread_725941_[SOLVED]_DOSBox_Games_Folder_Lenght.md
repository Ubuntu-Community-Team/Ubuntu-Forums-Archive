---
title: "[SOLVED] DOSBox Games Folder Lenght"
date: 2008-03-16
forum: Gaming &amp; Leisure
---

### Post by Rytron on 2008-03-16
Hi,
I notice that when I put my Dos games into my dosgames folder and then start DosBox and navigate to that folder - if the folder title and even the .exe is too long, the name in dos goes something like this **dosgamenam~** (this is just an example).

Is there a limit on the number of characters that a name in Dos must be and if you have a name that is very long and shows up with a (~) at the end can you still select somehow?

---

### Post by acoustibop on 2008-03-16
This is DOS' 8.3 file naming system, Rytron.  Extensions are limited to 3 characters and filenames to 8: if you get a file (or folder) name longer than that, you have to modify it like this:

Use the first 6 characters of the filename/foldername, then add ~1.  Omit spaces.  This will work fine if it's the only file/folder that meets this description, but if more  files/folders have the same first 6 characters, they'l be recognised as ######~1, ######~2 etc - unfortunately, DOS numbers them somewhat arbitrarily; you'll have to use trial & error to find out which is correct.

Later versions of DOS (is it 7.x and up?  Can't recall...) can recognise longer filenames.

You may be able to use long filenames by enclosing the path in inverted commas (").  I haven't used DOSBox, so I don't know what versions of DOS it emulates, or what it allows.

---

