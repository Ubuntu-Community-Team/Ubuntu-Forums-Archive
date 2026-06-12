---
title: "smeg / Applications Menu Editor not working"
date: 2005-11-10
forum: Desktop Environments
---

### Post by maxwellcom on 2005-11-10
(Using Ubuntu Breezy)

My Applications Menu Editor does not seem to work.  For instance, I added Amarok, which installed fine.  But with the editor I tried to change the name from "amarok" to "Amarok."  I've tried everything a newbie would think of: running smeg as root, renaming from "amarok" to "temp" and then to "Amarok," etc.  Nothing seems to work- it always just shows a "amarok" and a different icon. 

I know I'm missing something simple.  Any suggestions?

Thanks!
Nathan

---

### Post by 23meg on 2005-11-10
Try restarting your gnome panel with "killall gnome-panel".

---

### Post by maxwellcom on 2005-11-10
[QUOTE=23meg]Try restarting your gnome panel with "killall gnome-panel".[/QUOTE]

I forgot to mention that I have tried that as well.  For some reason, smeg doesn't seem to have any impact on renaming any items in my applications menu.  In what folder/file is the applications menu content stored?

Thanks,
Nathan

---

### Post by aysiu on 2005-11-10
Have you tried adding it as a new entry instead of editing the entry that was already there?

---

### Post by Juzz on 2005-11-10
I had to make it start from terminal to get it working.

---

### Post by maxwellcom on 2005-11-10
[QUOTE=aysiu]Have you tried adding it as a new entry instead of editing the entry that was already there?[/QUOTE]

I didn't think of that... did the trick.  I think it's kinda wierd, however, that this approach is the only way to get it to work!

Anyway, thanks for your help!

Nathan

---

### Post by DrBair on 2005-11-10
I've noticed that as well.  I can move and change various things about a menu item and everything will work fine EXCEPT changing the name which never catches up... 

Odd problem.

---

### Post by maxwellcom on 2005-11-10
[QUOTE=Juzz]I had to make it start from terminal to get it working.[/QUOTE]

Strange- I tried that option as well, but it didn't seem to have any impact.

Nathan

---

### Post by nike984 on 2005-11-10
[QUOTE=maxwellcom](Using Ubuntu Breezy)

My Applications Menu Editor does not seem to work.  For instance, I added Amarok, which installed fine.  But with the editor I tried to change the name from "amarok" to "Amarok."  I've tried everything a newbie would think of: running smeg as root, renaming from "amarok" to "temp" and then to "Amarok," etc.  Nothing seems to work- it always just shows a "amarok" and a different icon. 

I know I'm missing something simple.  Any suggestions?

Thanks!
Nathan[/QUOTE]

try in terminal 
sudo smeg

then after when smeg is started, edit the smeg command in the menu to 
"sudo smeg"

---

### Post by Sutekh on 2005-11-10
[QUOTE=maxwellcom]In what folder/file is the applications menu content stored?[/QUOTE]

Amarok for example would probably be in /usr/share/applications/kde/ and the file would be amarok.desktop or similar.

---

