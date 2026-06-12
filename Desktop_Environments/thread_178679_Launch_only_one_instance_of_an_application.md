---
title: "Launch only one instance of an application"
date: 2006-05-18
forum: Desktop Environments
---

### Post by matthis on 2006-05-18
Dear Ubuntu users,
 I tend to minimize the windows of the apps I use, forget that I have already launched them, and thus launch them again. As a result, I get for example two instances of evolution mail, openoffice writer, etc... which I don't want to happen.
Is there a way to check if the application is running, and if it is only un-minimize it rather than launching a new instance? I would like this to happen when launching apps from the gnome-panel, either as application launchers or from the main menu.

Thanks for any help!

---

### Post by bswilson on 2006-05-18
Are you not using the Window List?](*,)

---

### Post by matthis on 2006-05-18
Well yes I do use it. But say I don't look at it ;) 
The reason I ask for this is because having only once instance of an application is the way it works in the mac system.
I don't think its particularly better or worse than in gnome, but I'm kind of used to it...

---

### Post by H.E. Pennypacker on 2006-09-12
This is not a problem with a program like Totem, but its definitely true for VLC.  Clicking on a VLC more than once will launch multiple instances of VLC.  Totem doesn't create new windows.

---

### Post by sonoma on 2006-11-29
I too would love to have this built into Gnome, where I can only launch one instance of ANY particular application, especially picture viewers;) Gphoto is a great example, I only want 1 window and I want it to be reused if I double click another image from Nautilus. Now that gThumb is the default viewer for Edgy, does anyone know how to set it to single instance only?

VLC finally has the option to run only one instance built into it's preferences, but I can't find it in the Ubuntu binary version 0.8.6, I know I found and set it on the windows version (0.8.5 specially compiled by Moyekj for ReplayTV optimizations), it's under Settings->Preferences->Advanced (click "advanced" checkbox)->Allow Only 1 Running Instance. It's NOT there on the Linux ported binary for Ubuntu 0.8.6?

---

### Post by ecoxmit on 2006-12-06
I am having the same problem. I would like only one instance of evolution. 

Does anyone have a solution?

---

### Post by mannheim on 2006-12-06
It's not a great solution, but you can deal with this problem one app at a time by creating a script that first checks whether the app is already open: if it is open, the script brings the app's window to the front, and if the app is not open, the script just launches the app. Then you can create a launcher on your panel or desktop which just runs that script: you can give the launcher an appropriate icon, and you are all set. I explained how to create a script of this sort in an [earlier  post.]("http://www.ubuntuforums.org/showpost.php?p=1142703&postcount=10")

---

### Post by ecoxmit on 2006-12-07
Fantastic! this works. thanks

> **mannheim said:**
> It's not a great solution, but you can deal with this problem one app at a time by creating a script that first checks whether the app is already open: if it is open, the script brings the app's window to the front, and if the app is not open, the script just launches the app. Then you can create a launcher on your panel or desktop which just runs that script: you can give the launcher an appropriate icon, and you are all set. I explained how to create a script of this sort in an [earlier  post.]("http://www.ubuntuforums.org/showpost.php?p=1142703&postcount=10")

---

### Post by newsun on 2007-12-17
this mostly works for me as well, only with skype, the app can be open but no windows for wmctrl to act on so it still opens a new one...if only they did it better, I mean they have focus skype key command in windows versions, why not linux? Amarok works well like this by default

---

