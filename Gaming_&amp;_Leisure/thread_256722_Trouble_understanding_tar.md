---
title: "Trouble understanding tar"
date: 2006-09-13
forum: Gaming &amp; Leisure
---

### Post by jbumgar on 2006-09-13
I'm a noobie and I'm going crazy trying to figuring out how to use tar and tar bz2. Most of time the install docs haven't told me a thing about how to go about setting up my files. I even had one with a text file that said I would find an install info in the directory. I looked in all the directories and never did find anything relating to install.

Then what are the mysterios and .sh and .ini for? How are you supposed to use them in terminal mode?

---

### Post by joeljkp on 2006-09-13
Maybe if you gave an example we'd be able to help you better.

Files with .tar and .tar.bz2 are just compressed files, like .zip files. You should be able to double-click on them to open them.

Files with .sh are script files; you have to right-click them, go to properties, go to permission tab, and enable execution, then double-click on them.

---

### Post by Timothy Butwinick on 2006-09-13
You can also use the terminal: 
"tar xf yourTarFile.tar" (x means eXtract, F Files)
For bz2 files:
"tar xjf yourTarFile.bz2" (j means "bz2", with a little imagination)
There is a third format as well: .gz:
"tar xgf yourTarFile.gz"
or
"tar xjgf yourTarFile.gz.bz2"

"./yourShFile.sh" starts .sh files (shell scripts) Note that it begins with a dot.

I think, though I am not sure, that .ini files are for configuration.

---

