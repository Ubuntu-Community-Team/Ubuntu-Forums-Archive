---
title: "Font Type: PostScript Type 1 Outline &quot;empty&quot;"
date: 2012-08-23
forum: Desktop Environments
---

### Post by nowashburn on 2012-08-23
I am trying to install a font called "AacheBol" that is apparently a PostScript font with no success. Font Viewer does not open the font and the file also has the size of 0 bytes. I obviously thought there was something wrong with the file but here's the weird thing... Other mac users who are on the same network as me are able to install the font from the same exact network location and their systems return the file as being 41 kb in size. The mac system also says the file type is "PostScript Type 1 Outline". Any ideas what is going on here?

Ubuntu 12.04

Thanks!

---

### Post by nowashburn on 2012-08-23
So I kind of came up with a solution here by using t1unmac:

[http://manpages.ubuntu.com/manpages/hardy/man1/t1unmac.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/t1unmac.1.html)

First, I had a mac user zip up the PostScript file and send me the zip file. 

Then, I extracted the zip file and went into the __MACOSX directory and used t1unmac to convert the hidden font file in there. $ t1unmac ._hiddenFontFile newConvertedfile

Although this did work, it isn't a great solution as it did require the mac user to help out by zipping and sending me the archive. Its there a more efficient way of doing this?

---

