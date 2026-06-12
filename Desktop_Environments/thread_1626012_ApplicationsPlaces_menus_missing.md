---
title: "Applications/Places menus missing"
date: 2010-11-19
forum: Desktop Environments
---

### Post by purple-spear on 2010-11-19
I finished updating, and had to reboot, so I did. Upon logging in, my Applications and Places menus were gone. Rebooted, switched to a different kernel, still gone. Rebooted again, started the kernel that usually works the best, and they're gone there, too. Opening up the "Add to Panel" menu doesn't work, there's not an option to add the menus back. Ran xfce4-panel, that didn't work either. Any ideas?

---

### Post by Purplerob on 2010-11-19
:\ 
edit: oops didnt see it was xubuntu sorry

---

### Post by purple-spear on 2010-11-19
> **purple-spear said:**
>  Opening up the "Add to Panel" menu doesn't work, there's not an option to add the menus back.

I already tried that.

---

### Post by azertyh on 2010-11-20
hello,
to be sure : right-click the panel, select "add new items ...", and you don't have the items "places" and "xfce menu"???

---

### Post by purple-spear on 2010-11-20
Nope. On the panel I'm missing "Appilcations" and "Places," and in "Add New Items" there is no "places," "applications," "menu bar," or "xfce menu."

---

### Post by NoNameWill on 2010-11-20
I just had the same thing happen to my sons computer. This is lame as this is the second time in two days that after updating on two different computers that some type of issue has come up. 

I installed xfce desktop on top of a gnome so that still works.

---

### Post by NoNameWill on 2010-11-21
Ok I have had some time to research this problem. Seems to be some what common. I did a google search and found some archived threads from this forum about this issue. 

From terminal type:
```
xfce4-panel start
``` 

After that they should appear. Then restart your computer with sessions saves. It's usually already marked if not tick it and the panels should be there when you restart.

---

### Post by purple-spear on 2010-11-21
> **purple-spear said:**
>  Ran xfce4-panel, that didn't work either. 

I've tried that, too...

---

### Post by NoNameWill on 2010-11-21
> **purple-spear said:**
> I've tried that, too...


Sorry I forgot to mention I also reinstalled anything that had to do with xfce panel in synaptic before I started through terminal. 
I also through terminal purged xubuntu-desktop. Which wasn't the whole package but a 41k file. Then reinstalled it through terminal. And then restarted xfce4-panel.

I also got 4 errors while it started that had to do with plugins.

---

### Post by purple-spear on 2010-11-22
It's still not working. I don't think that simply purging/reinstalling is going to help with this one.

---

