---
title: "[SOLVED] login window theme not showing up in list"
date: 2007-12-22
forum: Desktop Effects &amp; Customization
---

### Post by spiderbatdad on 2007-12-22
I have installed several themes by simply moving the necessary files into /usr/share/gdm/themes/newfolder. Recently i tried to build my own using my own .jpg and copying some .xml and .desktop programs. everything is executable and should work. But when I go to Login Window Preferences-->Local my theme is not there. I can't understand, as other themes with similar files do appear after being manually added to /usr/share/gdm/themes/newfolder.  Could anyone help please?

---

### Post by Nano Geek on 2007-12-23
Are you sure you copied every file that the others have?

---

### Post by spiderbatdad on 2007-12-23
they all seem to be in order and with correct permissions as compared to other directories i have in /themes.

---

### Post by Nano Geek on 2007-12-23
Besides trying to manually adding them from the Login Window settings, I'm not sure what the problem is.

---

### Post by spiderbatdad on 2007-12-23
no luck. what a head scratcher.

---

### Post by Nano Geek on 2007-12-23
Strange.

If you want to, you could put it in a tar file, upload it here, and I'll try to take a look at it.

---

### Post by spiderbatdad on 2007-12-23
hrm? 976KB file size limit here.

---

### Post by spiderbatdad on 2007-12-23
Finally got it. The GdmGreeterTheme.desktop needed to be named just that. And for some reason, as I had copied it, it was adding info into the file including Desktop Location and Version 1.0. xml did not like that.

---

### Post by Nano Geek on 2007-12-23
Ahh.

Glad you found the solution.

Merry Christmas.

---

