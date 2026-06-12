---
title: "Themeing Main Panel Question"
date: 2006-04-12
forum: Desktop Environments
---

### Post by sclough on 2006-04-12
Forgive me if this is the wrong place to post it, I'll happily move the thread. I had originally posted this in the dapper forum since I'm running dapper, but this is more of a generic Gnome question.

I'm using the standard ClearLooks theme on Dapper and there are two things I'm interested in changing and I can't figure out how to do it. The first is the color of the Window Manager. Clear Looks uses a blue that's a little towards the aqua or turquoise side and that makes it incompatible with a lot of other colors in my little opinion. How do I tweak that color? I looked at the theme and apparently themes are just xml files which give GTK instructions? Anyway, I see it using variable names like SELECTED which I assume are used to load colors, but I don't see how to specify those colors. (Or course, I haven't read all 817 or so lines of the file either).

Also, the window bars in ClearLooks have a little bit of a rounded look to them that is pleasing, but when comparing it against the standard panel it makes the panel look just flat and like it doesn't belong. Is there a way to give that slight "rounded" look to the panel as well? I suppose I could create some sort of image and use that as a background, but I didn't know if there was a way to add this to the theme so that it would be generated the same way as the window bar's and would look cohesive. Thanks for any help.

---

### Post by mannheim on 2006-04-12
The colors are defined in 

/usr/share/themes/Clearlooks/gtk-2.0/gtkrc

If you don't want to edit this file, make your own personal "MyClearLooks" or whatever: copy the Clearlooks directory into ~/.themes/ and rename that directory "MyClearLooks". Similarly, change the name wherever it appears in the files below this directory. Then edit ~/.themes/MyClearLooks/gtk-2.0/gtkrc.

---

### Post by sclough on 2006-04-12
Ok, I'll try that to change the colors.  Thanks.

---

