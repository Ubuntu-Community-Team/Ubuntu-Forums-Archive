---
title: "Opening terminal profile through terminal?"
date: 2009-12-15
forum: Desktop Environments
---

### Post by mmmmf on 2009-12-15
Hi, I have 2 profiles in my terminal, 1 in which I use for IRC. Is there anyway I can open that profile without having to use the terminal menubar? I prefer it disabled if possible.

---

### Post by spiderbatdad on 2009-12-15
Not sure I understand, but lets say you have 2 launchers...in the launcher properties you can pass the profile as argument in the command. Like: ```
gnome-terminal --profile=myprofile1
#The other launcher would be
gnome-terminal --profile=myprofile2
```

---

### Post by mmmmf on 2009-12-15
Thank you spiderbatdad, this is exactly what I needed.

---

