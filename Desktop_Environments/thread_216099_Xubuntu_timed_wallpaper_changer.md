---
title: "Xubuntu timed wallpaper changer"
date: 2006-07-14
forum: Desktop Environments
---

### Post by mcpish on 2006-07-14
The Wallpaper dialogs for Xubuntu (XFCE) let you select a number of background wallpapers that rotate each time you login, is there anyway to make this a timed rotation of say, 30 minutes?

---

### Post by jvdowney on 2006-07-14
Yeah, I did this on my setup. Open the terminal, and type crontab -e to edit the crontab, the first line is a commented sample, delete or ignore and go to the second line. Copy and past this command for a thirty minute changeover:

0,30 * * * * export DISPLAY=:0; /usr/bin/xfdesktop -reload

I think you have to hit the carriage return first, then save the changes. The background should change on the hour and half hour.

I found this somewhere after a google search, but can't remember now who worked it out.

---

### Post by mcpish on 2006-07-15
Thank you for this info.  Now XFCE is perfect for me.

---

### Post by jvdowney on 2006-07-15
My favorite too. Tried gnome, but my old Pavilion was too slow. The learning curve was a little steep but manageable, after only about three weeks I have everything customized just the way I like it.

---

### Post by mcpish on 2006-07-15
Yup.  
My system isn't too old, (1GB RAM, AMD Sempron 2500+) but I love the blazing performance of XFCE and I find it looks just as good as Gnome.  I like the fact that most of the included apps open instantly (i.e. mousepad), without even a second delay unlike gedit.  To me, it's like a GUI that's as fast as the shell. :)

---

### Post by gtr225 on 2007-12-14
Thanks, this helped me out.

---

