---
title: "XGL/Beryl Working, but one question"
date: 2006-11-18
forum: Desktop Environments
---

### Post by Smith2688 on 2006-11-18
Hello all, I finally got XGL/Beryl working with my ATI system (I have it running off of a USB hard drive and there is only a slightly noticeable lag when saving a file).

Everything's finally running smoothly, however, I have one question, well two, actually.

As you can see from the following screenshots, I have emerald themes working, however, the actual properties of the windows themselves, as in the all the actual menus (File, Edit, Applications, Places, etc. etc.) have reverted to some less than sleek look.  All the actual windows do not look as nice as they do in metacity.  Any idea what's going on?

[[IMG]http://img371.imageshack.us/img371/5403/screenshotnz7.th.jpg[/IMG]](http://img371.imageshack.us/my.php?image=screenshotnz7.jpg)
[[IMG]http://img371.imageshack.us/img371/4965/screenshot1tn0.th.jpg[/IMG]](http://img371.imageshack.us/my.php?image=screenshot1tn0.jpg)
[[IMG]http://img398.imageshack.us/img398/7996/screenshot3ko3.th.jpg[/IMG]](http://img398.imageshack.us/my.php?image=screenshot3ko3.jpg)

My other question, which I believe is related to the first, is, does anyone know why I do not have a Shutdown or Restart button anymore?  Instead I have to log out and shutdown from the login menu.

Thank you for any help you can provide.

---

### Post by xabbott on 2006-11-18
I'm having the same problem. Any help would be appreciated.

---

### Post by sancheztavo on 2006-11-18
I can answer your first question:
go to System -> Preferences -> Sessions and add gnome-settings-daemon in startup programs.
That's all.

---

### Post by xabbott on 2006-11-18
That worked. Thanks.

---

### Post by Smith2688 on 2006-11-18
Oh thanks, that made everything look better.  

Unfortunately, I'm still missing my Shutdown and Restart buttons.

---

### Post by Shatrat on 2006-11-19
> **Smith2688 said:**
> Oh thanks, that made everything look better.  

Unfortunately, I'm still missing my Shutdown and Restart buttons.

Just right-click whichever panel you want your shut down button on and choose +Add to Panel. 
The Shut Down button is the very last item when you scroll down.

---

### Post by CowzRule on 2006-11-19
Have a look at this page
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL")
It'll give you some options on how to start Beryl and what you can do about the "gnome-settings-daemon".
As far as adding the "Shut Down" and "Restart" buttons, I remember reading something about that here in the forums. I'm gonna search for it again and if I find it I'll post it here.

EDIT:
Found some info about the buttons
[http://www.ubuntuforums.org/showpost.php?p=1350989&postcount=3]("http://www.ubuntuforums.org/showpost.php?p=1350989&postcount=3")
Seems it's not possible to fix it yet, just some work-arounds

---

### Post by Smith2688 on 2006-11-19
Hey, thanks guys, I'll have to test both of your suggestions out!

---

### Post by Mr Fat Bat on 2006-11-20
I've had the same problem and found a great fix on the wiki:

[http://forum.beryl-project.org/topic-6119-beryl-gnome-settings-daemon-startup-scripts](http://forum.beryl-project.org/topic-6119-beryl-gnome-settings-daemon-startup-scripts)

Let me know how you go!

---

