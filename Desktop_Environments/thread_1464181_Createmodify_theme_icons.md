---
title: "Create/modify theme icons?"
date: 2010-04-27
forum: Desktop Environments
---

### Post by trooster89 on 2010-04-27
I got sick of horrible orange color of the folders in the humanity theme, so I edited the icons located at /usr/share/icons/Humanity/places/  saved the .svg's with nicer blue colors. (don't worry I didn't save over the originals) However I only did this for the 48x48 sizes.

Is there any way I can export all of them in each of the sizes 16x16 22x22 ....64x64 without having to do each one manually multiple times? 
or maybe an easier way to create an new icon set?

---

### Post by SnickerSnack on 2010-04-27
I assume that you used inkscape.

You can shrink the large (bluish) ones down to the right size (and save as a new icon).

Whatever your software is, if it can modify color, it can probably modify size.

---

### Post by trooster89 on 2010-04-27
there's about 82 icons per each size. So I'd really rather not do each one by one 6  times.

However what I did discover was that if I edited the index.theme  file as below I could avoid the resizing altogether. For each size I just changed the "Type=" from "Fixed" to "Scalable"

[places/16]
Size=16
Context=Places
Type=Scalable

---

