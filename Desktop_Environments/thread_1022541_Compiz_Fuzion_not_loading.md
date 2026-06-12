---
title: "Compiz Fuzion not loading?"
date: 2008-12-26
forum: Desktop Environments
---

### Post by siddartha on 2008-12-26
I discovered some time ago that some of the compiz fuzion effects were missing, also, although the apps could be send to other virtual desktops, the user could not switch the desktop. The one workaround solution I have found is loading the compiz-fuzion icon and after each log in to click on that and chose reload window manager. I have no idea what is causing this weird behavior. I even changed the window decorator from gtk to emerald themes so the change will be obvious. Is there a fix?

---

### Post by gettinoriginal on 2008-12-27
In terminal type:

emerald --replace

---

### Post by eshant_engineer on 2008-12-27
In spite of above you can go to system->preferences->session click add, paste the above code.:popcorn: you would get rid of running this code at every startup.

---

### Post by siddartha on 2008-12-28
Nope.

Emerald is used just to be there as a visual reminder that compiz has not load well.

Some time ago it used to load well with virtual desktops and all, now, after a X restart I have to reload the window manager by hand each time.

Compiz should load properly from the begining.

---

### Post by gettinoriginal on 2008-12-28
System > Preferences > Session > Options > Automatically remember running applications when logging out.

---

