---
title: "Wallpaper-Tray issue"
date: 2009-06-04
forum: General Help
---

### Post by ZosoPage1963 on 2009-06-04
Hello, I just switched to Ubuntu 9.04 from Windows 7, love it, and learning a ton, sorry if this is in the wrong place but I found other threads in here regarding Wallpaper Tray.  I mistakenly set Wallpaper Tray to rotate 0 seconds... so, it is constantly changing and I can not get to the interface to change it or uncheck the timed interval.  I have removed completely from synaptic, and reinstalled, but it does the same thing.  I also did a search for wallpaper and found nothing related to wallpaper tray to delete.  What am I missing?  Thanks for your help!!!

---

### Post by pastalavista on 2009-06-04
There should be a hidden folder in your home directory probably (most programs are like this) called .wallpaper-tray. The dot before it makes it invisible. In nautilus, press control-h to hide/reveal hidden folders... or you could search for .wallpaper-tray... don't forget the dot :)

---

### Post by Irihapeti on 2009-06-04
The configuration file is 
/home/[your user name]/.gconf/apps/wp_tray/%gconf.xml 

It's in a hidden folder, and you'll need to follow pastalavista's instructions to see it.

It looks as though "n_timeout" is the value you need to change.

---

### Post by ZosoPage1963 on 2009-06-04
thank you!

I have deleted the files that you listed and did a search for .wallpaper .wp-tray, .wp and anything I can think of to search for.  after I reinstall wallpaper tray, the same issues is happening.  The background is changing so much that the menu system from the tray is not available. any more ideas?

---

### Post by pastalavista on 2009-06-04
Did you reboot after the changes? Did you edit the file Irihapeti mentioned?
```
gksu gedit /home/[your user name]/.gconf/apps/wp_tray/%gconf.xml
``` use your user name.. no brackets..

---

### Post by ZosoPage1963 on 2009-06-04
I followed your instructions to a tee... EXCEPT the reboot part.... issue is resolved now, reinstalled the app and it is all good again.  Thanks again for the help... breaking things is how you learn!!!!

---

