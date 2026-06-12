---
title: "unable to restore toolbar trash icon"
date: 2008-04-29
forum: Desktop Environments
---

### Post by BrandeX on 2008-04-29
Checked the other "trash" threads and was unable to come up with an answer to my problem.  Today I noticed that the trash icon in my bottom taskbar is missing from the lower right corner. (8.04/gnome) Simply right clicking the taskbar and attempting to "+add" trash has zero effect/response (anywhere, not just this taskbar, the other one also)  I can add any of the other icons in the list just fine.

Any ideas how to restore my trash icon back to the taskbar?

Thanks.

---

### Post by scragar on 2008-04-29
it's called "Deleted Items" now, no idea behind the name change, or it's sudden change in location for the trash.

---

### Post by BrandeX on 2008-04-30
There is no "Deleted Items" in the "Add to Panel" menu, just "Trash", and clicking on "add" does not add the trash to the taskbar. the other choices work fine.

---

### Post by scragar on 2008-04-30
what distro are you using?

have you tried going to a terminal and manualy launching it:```
/usr/lib/gnome-applets/trashapplet
```see if it throws any errors(if it does copy them back here please :P).

---

### Post by BrandeX on 2008-04-30
```
bash: trashapplet: command not found
```
I have been able to successfully add a functional trash can to the desktop via config, but I don't particularly want it there, I'd like it back on the task bar.

---

### Post by pPrdrm on 2008-05-03
It happened to me too while I was trying to make my wacom volito 2 work with Hardy. Following some thread, not only it wrecked my display (wrong resolution, x not starting and other problems) but it made the trash icon in the taskbar to disappear. At first I thought it was gone or deleted. But when I tried to add a new one nothing was showing up. By accident I right click on the taskbar and the trash menu opened up!!! The trash bin is there. It just not show any icon. How can I fix that? I can't see if there are any trash in the trash bin.
By the way, this wacom setup messing up my system every 6 months is starting to get on my nerves. Why is it so hard to make an easy tool to setup all wacom tablets? They all use the same driver, or so I think. Please find a way soon.

---

### Post by pPrdrm on 2008-05-03
I just tried something I read somewhere and it worked. In the ".nautilus" folder I deleted everything except the "metafiles" folder, logged out - logged in and there it was. After I checked the ".nautilus" folder only one file reappeared. It's called "saved-session-XXXXXX" where XXXXXX some random letters. Maybe this is the only file that needs to be deleted. I don't know. I am a bit worried about the other files that didn't show up again but for now all seems to be O.K.

---

### Post by jeffimperial on 2008-05-15
> **pPrdrm said:**
> I just tried something I read somewhere and it worked. In the ".nautilus" folder I deleted everything except the "metafiles" folder, logged out - logged in and there it was. After I checked the ".nautilus" folder only one file reappeared. It's called "saved-session-XXXXXX" where XXXXXX some random letters. Maybe this is the only file that needs to be deleted. I don't know. I am a bit worried about the other files that didn't show up again but for now all seems to be O.K.
You could have just "moved" [Cut - Paste to another place] those files. That's what I'll do anyways. Thanks for the tip and hope this helps me.

---

### Post by b3n5p34km4n on 2008-06-03
i have this same problem and i'm trying to fix it.  how do i access the .nautilus folder?  i went to the computer folder and searched for it but i got nothing.

---

### Post by XneoX on 2008-06-03
> **b3n5p34km4n said:**
> i have this same problem and i'm trying to fix it.  how do i access the .nautilus folder?  i went to the computer folder and searched for it but i got nothing.
Tthe .nautilus folder is a hidden folder in your home directory. you can see it by going to your home directoy and pressing Ctrl+H to enable hidden files view.

I have this same problem too.. I tried adding it to the toolbar using the default method and it din't work. I used the configuration editor in the system tools or gconf-edtor to place it on the desktop and then tried dragging it to the toolbar, it still would not work. Then i did notice that when i added it to the toolbar from the conventional method by dragging it to a certain point on the toolbar, if i right clicked at the same spot even though there was nothing there, it would show me the menu for the trash applet. It seems like the applet crashes there for some reason. If i run the command, "/usr/lib/gnome-applets/trashapplet" it doesnot give any errors but it does absolutely nothing. 

A lil
!!!!! ***  HELP  **** !!!!!!!

---

### Post by bettylafk7 on 2011-01-11
> **BrandeX said:**
> Checked the other "trash" threads and was unable to come up with an answer to my problem. Today I noticed that the trash icon in my bottom taskbar is missing from the lower right corner. (8.04/gnome) Simply [[COLOR=#000000]right[/COLOR]](http://www.softcov.com/zh-cn/manufacturers-news/ibm-to-help-build-shanghai-rural-credit.html) clicking the taskbar and attempting to "+add" trash has zero effect/response (anywhere, not just this taskbar, the other one also) I can add any of the other icons in the list just fine.Any ideas how to restore my trash icon back to the taskbar?Thanks.Thanks for your analysis! This is what I'm looking for.

---

