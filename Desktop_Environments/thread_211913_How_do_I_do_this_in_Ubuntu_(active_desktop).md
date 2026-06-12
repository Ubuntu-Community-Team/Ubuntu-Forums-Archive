---
title: "How do I do this in Ubuntu (active desktop)"
date: 2006-07-09
forum: Desktop Environments
---

### Post by natan- on 2006-07-09
Basically I have a .asp web page that my router has in its web interface, with various stats that it update every few seconds.  I want to display it (or just the info in another form?) embedded into my desktop. Here is a an example of what i want to do but in windows xp.

[IMG]http://myweb.wit.edu/keddemn/ad01.jpg[/IMG]

---

### Post by aysiu on 2006-07-09
I don't think it can be done in Gnome, but in KDE, if you configure the background (right-click on the desktop), select **No Picture** and then go to the advanced settings, you can use KWebDesktop to do what you want.

You have to click **Modify** to specify what web address you want as your background image. I think it can be refreshed every five or ten minutes--not every few seconds.

---

### Post by natan- on 2006-07-09
So i would need Kubuntu? Is there an easier way to get there than to install all the Kubuntu files? What about something like all those applets that people have for displaying the weather or the system resources they are using, you couldn't implement firefox or another browser into an applet on the panels? I found some program called gnome-swallow-applet but i'm not really sure how I could use it, but it seems like it should do what i want. It sopposedly takes in any X11 window to a panel.  Are their any x11 web browsers?

---

### Post by aysiu on 2006-07-09
You can do a kind of minimal KDE install with ```
sudo aptitude update
sudo aptitude install kde-core
``` or go even more minimal with ```
sudo aptitude update
sudo aptitude install kdebase
```

---

