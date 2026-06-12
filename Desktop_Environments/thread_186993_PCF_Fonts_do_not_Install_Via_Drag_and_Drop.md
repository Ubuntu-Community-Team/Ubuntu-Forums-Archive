---
title: "PCF Fonts do not Install Via Drag and Drop"
date: 2006-06-02
forum: Desktop Environments
---

### Post by v8YKxgHe on 2006-06-02
Hey,

I am trying to install this PCF Font: [http://www.netalive.org/tinkering/triskweline/]("http://www.netalive.org/tinkering/triskweline/") But when I go to fonts:// and try to drag and drop it in there to install it, it does not install/copy/move there. 

I got some help on the IRC channel, and they had the same problem with it. So, how do I install PCF Fonts in 6.06?

Thanks, ;)


EDIT: The file does get moved into .fonts/ but I can't use it at all.

---

### Post by panurge77 on 2006-06-02
I copied some truetype manually into ~./fonts and that did not work here either.

---

### Post by panurge77 on 2006-06-02
I tried moving them directly into ~/.fonts and using some xft commands and they did appear on gnome fonts config, but are unusable... they only appear as squares...

---

### Post by nbv4 on 2007-06-14
> **panurge77 said:**
> I tried moving them directly into ~/.fonts and using some xft commands and they did appear on gnome fonts config, but are unusable... they only appear as squares...

bump because I'm having the same problem. I have a pcf font that I can't install...

---

### Post by joolz on 2007-07-09
Same here, copied the fonts to /usr/share/fonts/type1/gsfonts/artwiz

run:

fc-cache -f -v

output:

/usr/share/fonts/type1/gsfonts/artwiz: caching, 0 fonts, 0 dirs

fc-list | grep snap
nothing

what is wrong?

---

