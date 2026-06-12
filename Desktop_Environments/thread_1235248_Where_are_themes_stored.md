---
title: "Where are themes stored?"
date: 2009-08-08
forum: Desktop Environments
---

### Post by Dullstar on 2009-08-08
I'd like to know where the themes, such as your icons and window visual settings, are stored so I can transfer themes between two computers (I have a good theme from 9.04 not available on my 8.04 and a good theme from 8.04 not available on 9.04).

Thanks in advance.

---

### Post by hansdown on 2009-08-08
Hi Dullstar.

You can download themes.

[http://www.techiesouls.com/2008/11/27/collection-of-50-best-looking-linux-gnomeubuntu-themes-to-download/](http://www.techiesouls.com/2008/11/27/collection-of-50-best-looking-linux-gnomeubuntu-themes-to-download/)

[http://www.google.ca/search?q=download+themes+for+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=download+themes+for+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by j.bell730 on 2009-08-08
I believe themes are stored in...
```
/usr/share/themes
```

EDIT- Oops, I didn't read your full post, icons are in:
```
/usr/share/icons
```

---

### Post by 67GTA on 2009-08-08
Also, depending on how they were installed, they could also hide in /home/<username>/.themes or /home/<username>/.icons

---

### Post by Johanano on 2009-08-09
Also for fonts:

/usr/share/fonts

or, if installed in home directory:

/home/<USER>/.fonts (you can just create the .fonts folder if it doesn't exist already)

---

### Post by Dullstar on 2009-08-09
I'll check these.

---

### Post by Dullstar on 2009-08-09
Hmmm, that was interesting.  The files I was looking for were already there, only buried in a strange way.  So the theme I was looking for was there the entire time, just buried very oddly.:mrgreen:

I produced the theme by customising themes.  That was very strange...

---

### Post by gjoellee on 2009-08-09
It can be:

/usr/share/themes
/usr/share/icons

or

/home/$user/.themes
/home/$user/.icon


Names with a dot in front of them are hidden in Linux. In Ubunut you can show hidden files by pressing Ctrl + H to show them, and the same hotkey to hide them again. (It is Alt + . with Dolphin)

---

