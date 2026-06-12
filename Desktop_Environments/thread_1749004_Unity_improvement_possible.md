---
title: "Unity improvement possible?"
date: 2011-05-04
forum: Desktop Environments
---

### Post by kornelix on 2011-05-04
I use a large monitor and often have 2-3 apps open. My biggest complaint about Unity is the loss of menus on each window. Switching apps and choosing menus causes lots of extra motion and requires more concentration. This is not exactly a killer but is a nuisance.

Is there an option to keep the menus with the windows? I notice that if an app is started with sudo (e.g. $ sudo nautilus) then the menus stay with the window. Is there a way to make all apps behave this way? If not, why not add this?

---

### Post by Brian R. on 2011-05-04
I noticed the same thing, nautilus lost it's menus when open by clicking the home folder icon, which is most annoying also i lost the menus in clamtk unable to update that, so got fed up and reverted to the classic desktop. Think Unity needs more work and programs to personalise it, so you can use it the way you want to.
Hope you find an answer.

---

### Post by kornelix on 2011-05-04
I googled this issue and found a way. 

I removed the following 3 packages and rebooted:
indicator-applet-appmenu
indicator-appmenu
indicator-application

I am not sure which one did the trick but the menus are now back on the windows.

---

### Post by DavePlummer on 2011-05-04
sudo apt-get remove indicator-applet-appmenu

---

### Post by truck87bp on 2011-05-04
Turn of the disappearing bar then all seems fine   [http://ubuntuguide.net/how-to-change...n-ubuntu-11-04](http://ubuntuguide.net/how-to-change...n-ubuntu-11-04)

---

### Post by hyperspacex on 2011-05-25
I find it very frustrating in switching between multiple windows of the same application. Would it be possible to add a feature something like that in the picture below?

[[IMG]http://img84.imageshack.us/img84/1505/ideap.jpg[/IMG]]("http://imageshack.us/photo/my-images/84/ideap.jpg/")

---

### Post by Frogs Hair on 2011-05-25
I added many quick lists before this application came out and thought it may be worth looking at . Classic Gnome is available at login if Unity is not for you. [http://www.webupd8.org/2011/05/quicklist-editor-for-ubuntu-unity.html](http://www.webupd8.org/2011/05/quicklist-editor-for-ubuntu-unity.html)

---

### Post by Ian Clark on 2011-11-26
> **Frogs Hair said:**
> I added many quick lists before this application came out and thought it may be worth looking at . Classic Gnome is available at login if Unity is not for you. [http://www.webupd8.org/2011/05/quicklist-editor-for-ubuntu-unity.html](http://www.webupd8.org/2011/05/quicklist-editor-for-ubuntu-unity.html)

Ain't available now.

---

### Post by Frogs Hair on 2011-11-26
> **Ian Clark said:**
> Ain't available now.

The thread was started before 11.10 was released  and the application was for 11.04  .

---

