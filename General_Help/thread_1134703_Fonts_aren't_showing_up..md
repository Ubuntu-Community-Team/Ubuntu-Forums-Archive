---
title: "Fonts aren't showing up."
date: 2009-04-23
forum: General Help
---

### Post by powerpleb on 2009-04-23
I have a bunch of fonts that on my Desktop with Ubuntu 8.10 I could place inside subdirectories in /usr/share/fonts, run sudo fc-cache -fv and tada! they work.

But I have put Jaunty on my laptop and when I try to do the same thing fc-cache seems to see them but they don't show up in any programs (like Open Office or Appearances).

The fonts are in subdirectories like this: /usr/share/fonts/other_fonts/fontname/font.ttf

Why would they work on Intrepid but not on Jaunty? :confused:

---

### Post by aaronp on 2009-04-23
Not sure about the specific answer to your problem but I find the best way to isntall fonts is to just drop them into ~/.fonts folder. Once you do that, they become instantly available to apps.

EDIT: Note, I am running Hardy so my advice may be out of date depending on any changes I'm unaware of in Intrepid or Jaunty.

---

### Post by powerpleb on 2009-04-24
Yea but I want them to be available to all users.

---

### Post by powerpleb on 2009-04-26
It was a permissions error. I fixed it with:
```
sudo chmod 755 -R /usr/share/fonts
```

---

