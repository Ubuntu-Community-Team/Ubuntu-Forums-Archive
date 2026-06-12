---
title: "Where are gnome 'file types' stored?"
date: 2010-04-03
forum: Desktop Environments
---

### Post by gregsmith_to on 2010-04-03
I have a problem in my desktop (8.04 on amd64), where there is a new file type called 'python file (no console)', which applies  to all files that used to be 'text file'. This occured as an unwanted side effect of installing Python 2.2 for windows under Wine (and yes, I had a reason to do that). The new file type's icon is a happy green python 2.2 snake. In addition to all the happy green snake icons, gedit no longer gives me python formatting by default for *.py files.

I'm sure there's a way to fix this by removing the new file type, but the location of the file type database in gnome 2 has eluded google searches, menu walks, and random wandering through the file system, I've found no applet for this or documentation about it.

Can anybody point me to where this information is stored, or to docs?

---

### Post by asmoore82 on 2010-04-03
I've always wanted to know this myself but I still don't yet.

But for your specific situation, wine should have created some *.desktop files in
"$HOME/.local/share/applications/" that you can edit or delete to help.

---

### Post by gregsmith_to on 2010-04-04
Yes, indeed! thank you, there are also the following


```
~/.local/share/mime/packages/x-wine-extension-pyw
~/.local/share/icons/text-plain.xpm

```

The first one maps 'text/plain' to 'python file (no console)', and the second one gives it the happy snake; neither of which makes sense, but there you are. I should be able to straighten this out now, thanks.

---

