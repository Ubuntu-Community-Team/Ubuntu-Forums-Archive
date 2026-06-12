---
title: "Ubuntu no longer remembers changes"
date: 2013-03-14
forum: Desktop Environments
---

### Post by cojacfar on 2013-03-14
I installed pyGObject last night and the newest install of GLIB. Ubuntu no longer remembers changes to my profile. It erased all of my launcher icons and changed my background. When I set new ones, it simply gets rid of them and changes to defualt when I reset my computer.

All of the programs that were on my computer are still there, but the Unity environment seems permanently screwed up. If I try to change my background now, nothing happens. It stays as the default Ubuntu one, same with the theme.

(It appears I can create bookmarks in Firefox still that persist)

---

### Post by Frogs Hair on 2013-03-14
The guest account will behave this way , but have not seen this in a user account.

---

### Post by cojacfar on 2013-03-14
It is in my user account. It is indeed behaving just like a guest account. I've been using it for a few months now, logged into it like normal, and cannot seem to do anything permanent.

---

### Post by Frogs Hair on 2013-03-14
Open Home, right click a folder > properties > permission and see if read/write permissions have changed . It reads like all permissions have changed. I am not familiar with  what you installed or if it would be the cause.

---

### Post by cojacfar on 2013-03-14
Says the owner (my user name) can create and delete folders. Same for the group, which is also just my login. 

I think it all seems normal. I'm able to apt-get and things like that with sudo just fine still. I followed this guide : [http://gtk3lab.blogspot.com/2011/05/installing-gtk3-and-pygobject.html](http://gtk3lab.blogspot.com/2011/05/installing-gtk3-and-pygobject.html) to install GTK3 to use. I'm assuming something in there screwed me.

---

### Post by Frogs Hair on 2013-03-14
The warning was pretty stern so you may have to wait for someone using the application.
 
[FONT=Georgia, Utopia, Palatino Linotype, Palatino, serif][COLOR=#cccccc]****[/COLOR][/FONT]Warning: Some of the packages of Gtk+3 or its dependencies may be experimental. After I installed Gtk+3  and PyGI, I had major issues with Gnome and had to reinstall Ubuntu altogether. I am not sure about the relation between installing Gtk+3, PyGI and the problem I had, but you are warned and should do that at your own risk.

---

### Post by cojacfar on 2013-03-14
Thank you for your help. I actually fixed it... somehow. I went through and uninstalled all of the things on that list, and reinstalled appropriate versions. That didn't fix it, but this latest restore from my backup did. Somehow. Any ways, thank you for your time!!

---

