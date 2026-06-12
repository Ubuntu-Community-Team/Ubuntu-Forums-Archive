---
title: "Icons, folders and files not showing on Unity desktop"
date: 2014-10-18
forum: Desktop Environments
---

### Post by chaaderf on 2014-10-18
Hello dear Ubuntu users! I have a question and I hope you could help me.

I have a problem with my Unity desktop. I would like to see the content of my ~/Desktop folder on my desktop. But it seems to be quite hard. In more detailed:

I have Ubuntu 14.04.1 and I've created files and folders in ~/Desktop folder and I can see them either in terminal (ls ~/Desktop) or in nautilus (nautilus ~/Desktop). What I expect, is that they also show on the desktop screen as icons (so that I could simply click one of them to open it (without launching e.g. nautilus)), but this is not the case at the moment. I've tried to install Ubuntu Tweak and force the icons (such as Trash) to show, but I've seen nothing but a wallpaper since I've installed this version of Ubuntu operating system. No matter do I log out or restart the computer. 

So my question: Is there any hints what should I do? Have I missed a setting or two? Should I reinstall Unity or what?

Thank you for any help!

---

### Post by deadflowr on 2014-10-18
What happens when you right-click on the desktop.
Do you get a menu with option to create documents, and folders, among other listings?

Edit: By only see the wallpaper, do you mean you do not have a panel on top and a launcher dock running down the left side?

---

### Post by chaaderf on 2014-10-18
> **deadflowr said:**
> What happens when you right-click on the desktop.
Do you get a menu with option to create documents, and folders, among other listings?

Yes, I get that menu.

---

### Post by deadflowr on 2014-10-18
If you right click and add a new document, does it show up on the desktop. And does it get added to ~/Desktop?

---

### Post by chaaderf on 2014-10-18
> **deadflowr said:**
> If you right click and add a new document, does it show up on the desktop. And does it get added to ~/Desktop?

Right after clicking the 'New Document' I can see another menu (right click again and there is something like cut and paste), but nothing is actually seen on desktop. That's why I found that second menu as I tried to add a new document again, but the menu has changed. It does add the file to the ~/Desktop:

```
-rw-rw-r-- 1 <name> <name>    0 Oct 18 20:54 Untitled Document
```

But no, I can't see anything on screen...

EDIT: > **deadflowr said:**
> Edit: By only see the wallpaper, do you mean  you do not have a panel on top and a launcher dock running down the left  side?

Ah, no. The panel on top and the launcher are visible and they are working fine.

---

### Post by CantankRus on 2014-10-18
Are you using the wallpaper plugin for compiz or installed another file manager like nemo?
Is nautilus in startup applications...Listed as "Files"?

---

### Post by chaaderf on 2014-10-18
> **CantankRus said:**
> Are you using the wallpaper plugin for compiz or installed another file manager like nemo?
Is nautilus in startup applications...Listed as "Files"?

Yes, I use wallpaper plugin. I'm not sure, but if I remember right, the problem was present even before I enabled the wallpaper in ccsm. But can't be absolutely sure as it was so long ago...
No, I have only the nautilus. (But I hardly ever use it, actually. :D )
Yes, "Files" is listed in startup applications.

---

### Post by CantankRus on 2014-10-18
You won't see icons on the desktop when using the wallpaper plugin to draw the desktops.
Right click still shows a menu though.

---

### Post by chaaderf on 2014-10-18
> **CantankRus said:**
> You won't see icons on the desktop when using the wallpaper plugin to draw the desktops.
Right click still shows a menu though.

Ahh, thank you! ^^ I guess, I need to think about these things a little bit now...

---

