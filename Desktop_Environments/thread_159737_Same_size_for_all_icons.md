---
title: "Same size for all icons?"
date: 2006-04-13
forum: Desktop Environments
---

### Post by sha_man on 2006-04-13
How to have (all) the *desktop* icons at a the same, custom size, for ex. 64x64 Pixel. (Not having to resize them maually with the stretch tool). In KDE this is easily possible, what about Gnome?

---

### Post by sha_man on 2006-04-14
nobody?

---

### Post by twigboy on 2006-04-15
You can try modifying your theme's gtkrc file.
add the line 
gtk-icon-sizes = "gtk-desktop xx,yy"
where xx and yy is the size of the icon you want.
But if you are using an additional icon theme I dont thik it will work.  You will probably have to modify that files icon theme.  I dont know how to do that.

---

