---
title: "Wrong startup arguments for gedit!"
date: 2005-08-03
forum: Desktop Environments
---

### Post by Zanathel on 2005-08-03
Hi fellow Linux users,
I've very recently installed Ubuntu Linux, and have never ever been using Linux before. This is a totally new experience, which unfortionatly has turned into an annoying nightmare because of one simple misconfiguration.

I made some PHP files, which I wanted to open. I right clicked on them, and found the option "Open with another application". I wanted to compare the dialog with Windows, so instead of just clicking on "open", I chosed "Open with another application". In teh commandargument I wrote something like this (the name of the document was ftp.info):
gedit ./ftp.info

What I DIDN'T know was that Linux ADDS the arguments automaticly. I Didn't have to type the arguments. Just gedit.

And this is where everything began.

Each time I open a document through X-server (outside the terminal) gedit also opens this "./ftp.info" file, which doesn't exist. It creates two tabs, one with ftp.info (not saved since it doesn't exist) and one with the document I wanted to open. It's so irrating when you're just going through the source.

Is it possible to reset the old gedit startup? Where is the configurationfile located that takes care of the file-extension startups?

I appreciate a quick reply,
// Zanathel

---

### Post by Hairy_Palms on 2005-08-03
if u right click on any php file that has the problem then go to the "Open with" tab it should let u remove the gedit u added and then add a new one and select "Text Editor" (this is gedit) from the list of programs, this will change it for all Files.

---

### Post by Zanathel on 2005-08-03
Eventhouigh I select another application, the default "gedit" is never replaced.

---

### Post by Zanathel on 2005-08-03
Aren't there like "Directory Preferences", like there are in Windows XP?

---

### Post by Zanathel on 2005-08-04
Please, please help. I really need  to fix this as soon as possible.

I've tried five times now - and got five options "gedit" options in "Open With" tab. The old application still remains.

Aren't it possible to reset everything?! Or set global properties?!

---

### Post by Zanathel on 2005-08-04
**Fixed!**
Thanks to the Unofficial Ubuntu starter guide!

---

