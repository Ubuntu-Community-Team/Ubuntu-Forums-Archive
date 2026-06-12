---
title: "Conky and Beryl problem"
date: 2007-10-14
forum: Desktop Effects &amp; Customization
---

### Post by RockoTDF on 2007-10-14
So I have a small issue...selection boxes on my desktop (when you are trying to highlight things for selection) erase conky.  The program is still running but whatever area is covered by the box will disappear.  Any suggestions?

---

### Post by Faud on 2007-10-14
You can intergrate Conky into your desktop itself, then move stuff over it and move it off of it and it's still there.

---

### Post by Rupertronco on 2007-10-15
> **Faud said:**
> You can intergrate Conky into your desktop itself, then move stuff over it and move it off of it and it's still there.

Huh? Thanks for the specifics. 


Original poster: Post your conkyrc file and we'll go from there.

---

### Post by Faud on 2007-10-15
> **Rupertronco said:**
> Huh? Thanks for the specifics. 




He asked for suggestions, that was my suggestion.

But how you would accomplish that is by adding

```
# set to yes if you want Conky to be forked in the background
background yes
```
to the top of your .conkyrc file and deleting
```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background no
```
If its there.
Conky is a lot of fun to play with an an amazing app IMO once you get used to it :)

---

