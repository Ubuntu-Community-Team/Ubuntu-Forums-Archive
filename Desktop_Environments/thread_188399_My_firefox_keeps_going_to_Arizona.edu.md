---
title: "My firefox keeps going to Arizona.edu"
date: 2006-06-04
forum: Desktop Environments
---

### Post by cobbweb on 2006-06-04
Hey, 
  My firefox keeps going to arizona.edu on startup, however my home is set to [www.ubuntuforums.org](www.ubuntuforums.org) .... 

 I think I have some type of spy ware because It said it was updating firefox and so I let it go but I guess it must have not been. Is there anywayto fix this problem? I really don't like going to Ariziana.edu every time on start up. Thanks.. 

 Cobbweb

---

### Post by aysiu on 2006-06-04
Maybe [this](http://ubuntuforums.org/showthread.php?t=160680) might help.

---

### Post by cobbweb on 2006-06-04
Ok, um but how to I look at my firefox path? I checked prefrences but can't seem to find the place... 

 Thanks 

cobbweb

---

### Post by aysiu on 2006-06-04
Are you using KDE or Gnome? Or XFCE?

---

### Post by cobbweb on 2006-06-04
Gnome

---

### Post by aysiu on 2006-06-04
It's in Preferred Applications. Select **Custom** and remove the **%s** at the end.

---

### Post by cobbweb on 2006-06-04
Great... I can run with a terminal and works fine, hower, I can't edit it. Im not sure why, but it's not letting me edit my prefered aplications. Im the super user so it should. Can i somehow edit it in the terminal?

---

### Post by aysiu on 2006-06-04
Superuser meaning that you've somehow logged in as root...? Or that you have *sudo* privileges?

When you click on **Preferred Applications**, what happens? Does it try to launch and just disappear?

**Edit**: I think the file you're looking for is ~/.gconf/desktop/gnome/url-handlers/unknown/%gconf.xml or /home/cobbweb/.gconf/desktop/gnome/url-handlers/unknown/%gconf.xml

---

### Post by robgue on 2006-06-21
[QUOTE=aysiu]It's in Preferred Applications. Select **Custom** and remove the **%s** at the end.[/QUOTE]

thanks, i was having same problem. the above worked. also removed it from starterbar launcher just in case

---

