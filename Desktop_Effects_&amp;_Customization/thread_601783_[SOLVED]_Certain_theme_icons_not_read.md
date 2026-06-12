---
title: "[SOLVED] Certain theme icons not read"
date: 2007-11-03
forum: Desktop Effects &amp; Customization
---

### Post by rahulthewall3000 on 2007-11-03
Ok, so I just installed Linista icon theme, but I find that the icons for the home folder, desktop and the trash used are not the ones provided in the icon oackage, in stead it is using the default gnome icons for these. I would like to use the same icon theme all over, and this is Linista, and I would be grateful if anyone could tell me how to fix this.

---

### Post by rahulthewall3000 on 2007-11-03
Any answers?

---

### Post by CatKiller on 2007-11-04
The names for which icons control which element have changed in the past. I remember a number of people complained that their trash icons didn't work anymore with the release of Feisty, because the name of the trash icon had changed to user-trash and the themes they were using didn't have a file called that.

If you go into the theme folder for the icon theme you want to use (~/.icons/linista, probably) and make a symbolic link to the icon that you want to use, called whatever the new name is, then your theme will work with the right icons. I can remember what they're all called, but you can use the Human theme (/usr/share/icons/Human) as a guide.

---

### Post by rahulthewall3000 on 2007-11-04
Yeah, that is what I did. Have edited some and they are working. Will move on to the others when I have more free time.
Thanks for your reply, though!

---

