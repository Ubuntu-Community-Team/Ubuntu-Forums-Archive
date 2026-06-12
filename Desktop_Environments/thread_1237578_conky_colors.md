---
title: "conky colors"
date: 2009-08-11
forum: Desktop Environments
---

### Post by blur xc on 2009-08-11
Is it possible to assign colors to variables, and use them to define certain colors in your conky script?  I find it annoying to have to search and replace so many instances of a color in a script, whenever I try out a different wallpaper.

Thanks,
BM

---

### Post by VCoolio on 2009-08-11
Yes, like this:
```

color1 white
color2 000000

TEXT

${color1}This is white
${color2}This is black ${color}This is your default_color
```

You can use the strings (white, dark-grey etc) or #blah codes without the # above text, then refer to them without spaces.

---

### Post by blur xc on 2009-08-11
Dude that's awesome.... thanks!

BM

---

