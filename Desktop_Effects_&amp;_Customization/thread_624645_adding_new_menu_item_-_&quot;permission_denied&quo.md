---
title: "adding new menu item - &quot;permission denied&quot; when clicked"
date: 2007-11-27
forum: Desktop Effects &amp; Customization
---

### Post by chamstar on 2007-11-27
Ive added a new menu item for a java app I downloaded (Eclipse). But when I click the menu item I get a permission denied error. If I double click the executable directly it loads fine. The executable is set to be executable and its owner is me.

What else do I need to do to get it to work from the menu?

Many thanks, Cham.

---

### Post by Nano Geek on 2007-11-27
I'm not sure, but try giving it 777 permissions. It could be that GNOME runs as a different user then you do.

---

### Post by chamstar on 2007-11-27
Thanks for the reply, I tried:

chmod 777 Aptana 

But it didn't work, I tried looking at other menu items and the files they 'link' to, and they are also owned by me.

Now then, the error does say that Aptana fails to run a child process... so I guess the target file is okay to execute but something else is not. I don't see how this is different from double clicking on the icon directly...

---

### Post by Nano Geek on 2007-11-27
> **chamstar said:**
> Thanks for the reply, I tried:

chmod 777 Aptana 

But it didn't work, I tried looking at other menu items and the files they 'link' to, and they are also owned by me.

Now then, the error does say that Aptana fails to run a child process... so I guess the target file is okay to execute but something else is not. I don't see how this is different from double clicking on the icon directly...Try doing this, I know it's not smart to keep it like this, but try putting **gksudo** in front of the path to the file in the menu item. It might be that it needs sudo privileges to run.

---

### Post by chamstar on 2007-11-27
The screen popped up to ask for password, but the app did not run, and I did not get an error message... Strange!! 

I might try the Aptana forum and report back my findings :)

---

