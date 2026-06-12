---
title: "problem with xfe"
date: 2005-06-21
forum: Desktop Environments
---

### Post by mstreibe on 2005-06-21
I'm using the xfe file browser and have a problem with the displaying of german umlauts in the menus and filenames. Filenames etc are UTF8 encoded, but in xfe I see them displayed in ISO encoding, e.g. instead of an "Ü" I see "Ã&#339;". This is the same if I type, e.g. when renaming files. I type an umlaut, but what I see is something like the above.

My locale is de_DE.UTF-8. No other application has this problem. I tried the xfe and libfox packages offered with ubuntu, and also built their latest versions from source, but it is always the same. I also contacted the author of xfe and he didn't know that problem, he said everything is fine on his debian system.

Does anyone see the same problem or know the solution?

---

### Post by mstreibe on 2005-06-21
[QUOTE=mstreibe]I'm using the xfe file browser and have a problem with the displaying of german umlauts in the menus and filenames. Filenames etc are UTF8 encoded, but in xfe I see them displayed in ISO encoding, e.g. instead of an "Ü" I see "Ã&#339;". This is the same if I type, e.g. when renaming files. I type an umlaut, but what I see is something like the above.

My locale is de_DE.UTF-8. No other application has this problem. I tried the xfe and libfox packages offered with ubuntu, and also built their latest versions from source, but it is always the same. I also contacted the author of xfe and he didn't know that problem, he said everything is fine on his debian system.

Does anyone see the same problem or know the solution?[/QUOTE]
 One addition: Currently I am using the debian packages provided at

  [http://roland65.free.fr/xfe/fox-deb.html](http://roland65.free.fr/xfe/fox-deb.html)

---

### Post by mstreibe on 2005-06-28
I have learned that the problem lies within the FOX toolkit. It doesn't support UTF8 yet, only single byte charsets like ISO. Since on my system I found only UTF8 locales, I had to create an ISO locale, which can be done as described in /usr/share/doc/locales/README:

localedef -i de_DE -f ISO-8859-1 de_DE.ISO8859-1

I can then run xfe as

LANG=de_DE.ISO88591 xfe

without needing to change the system's locale.

---

