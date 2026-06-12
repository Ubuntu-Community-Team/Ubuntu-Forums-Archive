---
title: "How can i install a tar.gz file?"
date: 2005-10-27
forum: Desktop Environments
---

### Post by Dark Damo on 2005-10-27
Hello I am unable to figure out how to install a tar.gz file? Im trying to set up a program called Roaring penguin PPPoE.

---

### Post by Emerzen on 2005-10-27
Right click on the file, then select "extract here."  What kind of file is it?  Is it source code?

---

### Post by XDevHald on 2005-10-27
it's best to **tar xzvf filename.tar.gz **so it is done correctly with no errors.

---

### Post by Emerzen on 2005-10-27
What errors would you run across using the GUI archiving tool?  Do you know of any good intro's to tar?

---

### Post by psychicdragon on 2005-10-27
**tar --help** or **man tar** will tell you about all the command-line options.

I've never had any kind of error using file-roller though.

---

### Post by aysiu on 2005-10-28
Any reason the PPPoe tools available through Synaptic (see attached screenshot) don't do it for you?

---

### Post by Moonbuzz on 2005-10-28
[QUOTE=Emerzen]What errors would you run across using the GUI archiving tool?[/QUOTE]

the GUI tools are created as a frontend to the actual program. If tar works 100% bug free, it doesn't mean the GUI frontend will do the same. Moreso, it's safe to assume both sides used tar, but you don't know which GUI frontend did the compressor use, if any. There's a big difference between a program that was created with the GUI, and one that is created as a frontend.
This been said, I've been using both tar and the Ubuntu/Gnome gui, and haven't had any errors.

---

