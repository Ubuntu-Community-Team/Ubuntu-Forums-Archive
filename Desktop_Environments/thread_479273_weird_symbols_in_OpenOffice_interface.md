---
title: "weird symbols in OpenOffice interface"
date: 2007-06-20
forum: Desktop Environments
---

### Post by necr0man6er on 2007-06-20
Hello, 

I've this problem that OpenOffice displays weird symbols in the interface. I don't know what to do about it.
Check the screenshot, to fully understand my problem.
I'm using Kubuntu 7.04 and openoffice 2.2

I already reinstalled Oo, but that didn't help (as i suspected)

If someone can help me out.

---

### Post by bapoumba on 2007-06-20
May be a font problem? Which one did you choose ?

---

### Post by necr0man6er on 2007-06-20
this is a default install, i didn't change any font. 
btw, i can't see wich font is installed.

Any other suggestions

---

### Post by Hagar Delest on 2007-06-20
Hi bapoumba ;)

This is the combination of 2 problems :
- First, install all the OOo icon themes (in Synaptic, install all openoffice.org2-style... packages) ; Feisty packages have been separated concerning themes :evil:
- Second, there is often an issue between OOo and the fonts set in Gnome control center for applications. There are several fixes, one is to use the replacement table in the OOo options, the other is to change the font used by all the applications.

---

### Post by bapoumba on 2007-06-20
Hey Hagar, thanks for stopping by :)

---

### Post by Hagar Delest on 2007-06-20
Always a pleasure to be of some help !

I hope the next Ubuntu release will have a better integration for OOo because Feisty is really bad.

---

### Post by necr0man6er on 2007-06-21
well, i found a solution to my problem, but i don't know what is causing it. 
I had to disable "use system font for user interface" in the view section.
But i don't use such kind of fonts on my system interface. strange

---

### Post by Hagar Delest on 2007-06-21
Yes, it seems that too many fonts installed confuses OOo when it updates the cache. This is why simply resetting the applications fonts usually fix it. Perhaps that even selecting a different one, runnning OOo, closing and selecting the initial one again could do the trick. But not sure, I've never faced this problem.

---

### Post by necr0man6er on 2007-06-21
well, for what i do with office tools, Koffice might be just what i need.

---

