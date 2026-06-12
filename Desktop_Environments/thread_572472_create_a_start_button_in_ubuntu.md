---
title: "create a start button in ubuntu"
date: 2007-10-10
forum: Desktop Environments
---

### Post by Balvinder25 on 2007-10-10
hi all,
         i use 7.04 and its working fine..could any one advice how to setup a start button in gnome inplace of  the three menus tht we normally have ..as of now i only have one menu with the ubuntu logo on it.but would like to replace this with a start button..so t be more specific..if we could just replace the logo with a start button..tht would be just great..possible?

---

### Post by vanadium on 2007-10-10
Look in the panel applets. There is one applet that behaves like the Windows Start button.

---

### Post by Balvinder25 on 2007-10-11
hi ,
        thanxz alot for the concern ..i already have a button that behaves like a start button but would like to change tht to look like a start button as in windows ..?

---

### Post by Forlong on 2007-10-11
Run this:
```
gksu nautilus /usr/share/icons/Human/22x22/places
```

And replace **start-here.png** with whatever you like. You should make a backup first.

Then all you need to do is choose another icon theme and go back to Human.

You can do this with any other icon theme too, of course.

---

### Post by Balvinder25 on 2007-10-11
hi buddy,
                   thanxs for that ..tht worked like a dream...thanks alot again,,:)

---

