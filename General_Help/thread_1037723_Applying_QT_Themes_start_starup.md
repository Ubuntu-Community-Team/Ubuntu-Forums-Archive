---
title: "Applying QT Themes start starup"
date: 2009-01-12
forum: General Help
---

### Post by lviggiani on 2009-01-12
Hallo guys,
I have successfully installed this QT rendering engine
[http://labs.trolltech.com/page/Projects/Styles/GtkStyle](http://labs.trolltech.com/page/Projects/Styles/GtkStyle)
which applies current GTK theme to QT applications so making a more consistent desktop look.
The problem is that, to make it work, **each time I log** in, I have to run
```
qtconfig-qt4
```
then select some other theme (as Gtk is already selected), then select Gtk theme again and click save, to have the rendering engine actually applied to running QT applications (i.e. Skype). And this is not confortable at all... :(
I'm wondering if there is an automatic way to do that.

My system is running Ubuntu 8.10 i386.

Thanks in advance for any help!

---

### Post by deanjm1963 on 2009-01-12
Install qtcurve (which you'll find with synaptic) which has some basic qt-themes and you can edit the palette for the right colors

Works for me

Hope this helps

Edit: if your programs are qt3 apps, not qt4 apps you will find qt3-qtconfig in the repos.

---

### Post by linuxuser21 on 2009-01-12
To get it to start up on login: System>Prefences>Sessions.  Click Add.  Add whatever name for it.  For the command type: qtconfig-qt4.  Now it should Start up with it.

---

### Post by lviggiani on 2009-01-12
> **linuxuser21 said:**
> To get it to start up on login: System>Prefences>Sessions.  Click Add.  Add whatever name for it.  For the command type: qtconfig-qt4.  Now it should Start up with it.

Thanks but I don't think this is a solution as it will pop up the qt theme selector and I will have to manually set the theme anyway...

---

### Post by lviggiani on 2009-01-12
> **deanjm1963 said:**
> Install qtcurve (which you'll find with synaptic) which has some basic qt-themes and you can edit the palette for the right colors

Works for me

Hope this helps

Edit: if your programs are qt3 apps, not qt4 apps you will find qt3-qtconfig in the repos.

Thanks but I need to do the opposite: I want that QT applications look like GTK ones.

---

### Post by deanjm1963 on 2009-01-12
you can't get qt apps to directly use the gtk themes. you can only get them to "look" or "appear" similar. Did you install the Ubuntu version of qt4-qtconfig?

The version in the repos has an inbuilt theme that looks very similar to "plastik", if you install "qtcurve" there are other qt themes that look like clearlooks, etc. You need to edit the palette of the themes, e.g. colours, select the fonts, etc.

I have a few qt apps, and when qt3/qt4-qtconfig is setup properly you would think they are native gtk themes.

---

### Post by lviggiani on 2009-01-12
> **deanjm1963 said:**
> you can't get qt apps to directly use the gtk themes. you can only get them to "look" or "appear" similar. Did you install the Ubuntu version of qt4-qtconfig?

The version in the repos has an inbuilt theme that looks very similar to "plastik", if you install "qtcurve" there are other qt themes that look like clearlooks, etc. You need to edit the palette of the themes, e.g. colours, select the fonts, etc.

I have a few qt apps, and when qt3/qt4-qtconfig is setup properly you would think they are native gtk themes.

No, that's not the point...
by installing the engine at my post #1, qt apps actually uses my current Gtk theme (look at my skype screenshot - Skype is a QT application).
The point is how to automatically apply the theme rather than having to do manually at each login.

---

