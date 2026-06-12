---
title: "change system clock colour"
date: 2009-05-04
forum: Desktop Environments
---

### Post by timroberts on 2009-05-04
Anybody know how to change the colour of the system clock? I'm in the gconf editor, and i found something for 8.04, but for whatever reason it isn't working in 9.04. I'm trying to make the clock red. Could somebody give me some suggestions?

This link doesn't work for jaunty:
[http://www.linuxine.com/2008/07/trick-customize-clocks-font-colour-on-gnome.html](http://www.linuxine.com/2008/07/trick-customize-clocks-font-colour-on-gnome.html)

I tried to modify what the above link says for what i want, and this is what my gconf-editor has right now: <span colour="FF0000> %H:%M </span>

---

### Post by BUSHYBOB on 2009-05-04
You seem to be missing  a '#' and an end quote.

<span colour="FF0000> %H:%M </span>
should be
<span colour="#FF0000"> %H:%M </span>

---

### Post by timroberts on 2009-05-04
put that in, still a no-go though.

---

### Post by BUSHYBOB on 2009-05-04
Did you  change the format key to  custom?

---

### Post by timroberts on 2009-05-04
I did. For some reason it doesn't seem to recognize it as a script. It just gives me the straight text.

---

### Post by BUSHYBOB on 2009-05-04
I got that until I discovered I'd left out the end quote.

---

### Post by timroberts on 2009-05-04
I just tried copying and pasting your code. No success.

---

### Post by BUSHYBOB on 2009-05-04
I've just noticed that colour should be spelled color.
Change that and you should be sorted.

---

### Post by timroberts on 2009-05-04
HEY! that did it! thanks a lot.

---

