---
title: "Trash can icon on desktop"
date: 2012-03-18
forum: Desktop Environments
---

### Post by Deafia on 2012-03-18
Hello everyone. I am trying to find where I can put trash can icon on desktop in Lubuntu with LXDE.

Does anybody know how to add trash can icon to desktop in Lubuntu?

Thanks! :)

---

### Post by seppalta on 2012-03-18
[http://douwil7.100webspace.net/linux/Tuning.html#11]("http://douwil7.100webspace.net/linux/Tuning.html#11")

---

### Post by Rex Bouwense on 2012-03-18
Try reading this:
[http://forum.lxde.org/viewtopic.php?f=8&t=2018](http://forum.lxde.org/viewtopic.php?f=8&t=2018)
I have not tried it because I operate with a clean desktop but it apparently worked for the OP.

---

### Post by patriki on 2012-03-21
Hello,
I have created a Trash icon on my desktop.
Just create a file using leafpad and paste this code:
```


[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=Trash
Name[fr_FR]=Trash
Icon=/usr/share/icons/gnome/256x256/places/user-trash.png
Exec=pcmanfm trash:///
Comment[fr_FR]=Trash
StartupNotify=true


```
perhaps, change [fr_FR] with your system language (I'm french)
then save it to your desktop using "trash" for name and you're done. :p

I'm using Lubuntu 11.10 oneiric.

---

### Post by ctxanadu on 2012-04-27
Thanks!!


> **patriki said:**
> Hello,
I have created a Trash icon on my desktop.
Just create a file using leafpad and paste this code:
```


[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=Trash
Name[fr_FR]=Trash
Icon=/usr/share/icons/gnome/256x256/places/user-trash.png
Exec=pcmanfm trash:///
Comment[fr_FR]=Trash
StartupNotify=true


```perhaps, change [fr_FR] with your system language (I'm french)
then save it to your desktop using "trash" for name and you're done. :p

I'm using Lubuntu 11.10 oneiric.

---

### Post by N4RPS on 2012-06-12
> **patriki said:**
> Hello,
I have created a Trash icon on my desktop.
Just create a file using leafpad and paste this code:
```


[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=Trash
Name[fr_FR]=Trash
Icon=/usr/share/icons/gnome/256x256/places/user-trash.png
Exec=pcmanfm trash:///
Comment[fr_FR]=Trash
StartupNotify=true


```
perhaps, change [fr_FR] with your system language (I'm french)
then save it to your desktop using "trash" for name and you're done. :p

I'm using Lubuntu 11.10 oneiric.

Hello!

Is there a way to write a 'script icon' that will perform an 'mv' command on whatever's dragged into it from the desktop and move it into the 'trash:///' directory? THAT would implement the effect most ex-Windozers are used to... :confused:

73 DE N4RPS
Rob

---

### Post by markbl on 2012-06-12
Two simple questions for you guys.

1. Why are you visiting your trash so often that you need 1 click to access it rather than 2?

2. Do you also put icons on your desktop for all the other "special" folders such as Home, Documents, Downloads, Music, Pictures, Videos, etc (i.e. all those other ones in the left pane in your file/nautilus app)?

---

### Post by Gaygerbil on 2012-06-18
I see no point in putting a trash on your desktop since you still need to open up the file manager to empty out the trash, because currently there is no way to have an ACTUAL trash icon on the desktop through LXDE. 

If anyone knows the terminal command to emptying the trash in pcmanfm then we could probably do something though...

---

