---
title: "minor annoyence with firestarter"
date: 2006-02-22
forum: Desktop Environments
---

### Post by alfonz on 2006-02-22
Well, I have managed to detach the toolbar off firestarters main window. See screenshot [[IMG]http://ubuntuforums.org/gallery/files/7/0/6/1/0/Screenshot_879054.png[/IMG]]("http://ubuntuforums.org/gallery/displayimage.php?imageid=2039&original=1") 


 and I can't dock it back in for some reason, it won't let me. Its really anoying to have it floating around. I've tried to look for user preferences somewhere but I can't seem to find them or maybe I just don't know where to look. 

If anyone has any advice please let me know

Thanks in advance

Cheers!

---

### Post by roostishaw on 2006-02-22
Did you try to just restart it?
It took me about 20 minutes of pokin' around, then I just closed and re-opened the app.

---

### Post by alfonz on 2006-02-22
yeah tried that, many times and it wont budge, even reinstalled it noting works. There must be a user config file that I need to edit somewhere but I just can't find it at all. Not sure where to look for it to be honest.

---

### Post by alfonz on 2006-02-22
Success!!!! :D 

The nosie person that I am, went on a field trip into the / directory and under /root/.gnome2 I found a text file named firestarter. Inside there was a tag [placement] and another line with co-ordinates for menu bar and tool bar. I basicaly deleted the contents of the file and left it empty (backed it up first ofcourse ;) ), restarter firestarter and presto back to normal. Heh! I guess I found the solution for my anoyance. 

Oh well, hope this helps someone that has same problem.

---

