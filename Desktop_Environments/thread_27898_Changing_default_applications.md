---
title: "Changing default applications"
date: 2005-04-18
forum: Desktop Environments
---

### Post by poyner on 2005-04-18
Hi all,

I want to change the default application for opening picture files to GIMP. How do I do this? 
Thanks,

---

### Post by TravisNewman on 2005-04-18
right click on a jpg, for example, click Properties, click "open with" select the gimp, click ok
repeat for the other image formats :)

not as quick as I'd like, but it gets the job done! ;)

---

### Post by poyner on 2005-04-18
[QUOTE=panickedthumb]right click on a jpg, for example, click Properties, click "open with" select the gimp, click ok
repeat for the other image formats :)

not as quick as I'd like, but it gets the job done! ;)[/QUOTE]
unfortunately that's not working..... yes it opens the file in GIMP.... but if i then close the file and just click on it again (to open it) it opens up in eye of GNOME again.... is there somewhere else where i can change this permanently?

---

### Post by Cool_dude_Prav on 2005-04-18
[QUOTE=poyner]unfortunately that's not working..... yes it opens the file in GIMP.... but if i then close the file and just click on it again (to open it) it opens up in eye of GNOME again.... is there somewhere else where i can change this permanently?[/QUOTE]
 Well.. what I am saying is related to KUbuntu Hoary...

Goto Menu-> Control Center-> KDE Components-> File Associations-> Images(You wil find a set of all possible image types, change here!!!

May also apply to GDM... dunno :wink:

---

### Post by Alexander Kirillov on 2005-04-18
[QUOTE=poyner]unfortunately that's not working..... yes it opens the file in GIMP.... but if i then close the file and just click on it again (to open it) it opens up in eye of GNOME again.... is there somewhere else where i can change this permanently?[/QUOTE]
 This must be a bug - I had similar experiences. However, after doing it the second time, or maybe restaring Nautilus, the setting was remembered. I couldn't figure out what went wrong...


If you right-click on the same file again and select "Properties->Open with", what does it show? EOG or GIMP? And is it a local file, or on a remote filesystem(samba/NFS)? I had a suspicion that it may be related

---

### Post by poyner on 2005-04-19
[QUOTE=Alexander Kirillov]This must be a bug - I had similar experiences. However, after doing it the second time, or maybe restaring Nautilus, the setting was remembered. I couldn't figure out what went wrong...


If you right-click on the same file again and select "Properties->Open with", what does it show? EOG or GIMP? And is it a local file, or on a remote filesystem(samba/NFS)? I had a suspicion that it may be related[/QUOTE]

Thanks heaps for the tip about "Properties->Open with" Alexander.... this showed EOG. Once I selected GIMP it seemed to fix the problem. 

Obviously either:
a) There is a BUG with Hoary/Gnome that is not changing the default application when an application is chosen from the Right Click -> Open with menu, or
b) This feature has been changed and to change a default application you now have to go into the Propertieis->Open with menu. ie. there was a deliberate change.... either way... I'm happy.

BTW.... the files are in my home directory

---

### Post by Alexander Kirillov on 2005-04-19
[QUOTE=poyner]Thanks heaps for the tip about "Properties->Open with" Alexander.... this showed EOG. Once I selected GIMP it seemed to fix the problem. 

Obviously either:
a) There is a BUG with Hoary/Gnome that is not changing the default application when an application is chosen from the Right Click -> Open with menu, or
b) This feature has been changed and to change a default application you now have to go into the Propertieis->Open with menu. ie. there was a deliberate change.... either way... I'm happy.

BTW.... the files are in my home directory[/QUOTE]
 b) is correct. 

"Right-click-->Open with" is for those cases when you intentiaonlly want to open a file in something other than the default app. For example, I normally open html files with web browser, but occasionally I might open one with Bluefish editor. In such cases, I do not want to change the default app. This is why GNOME provides a different mechanism for changing the default app.

---

