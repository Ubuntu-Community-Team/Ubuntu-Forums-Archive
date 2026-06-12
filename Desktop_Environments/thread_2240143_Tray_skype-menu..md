---
title: "Tray skype-menu."
date: 2014-08-18
forum: Desktop Environments
---

### Post by colotunbabay2010 on 2014-08-18
How to make a Skype menu in the system tray without scrolling? 
Now this:

[IMG]http://sd.uploads.ru/t/PuOiv.jpg[/IMG]


I want this:


[IMG]http://www.adminreseau.fr/wp-content/uploads/2014/06/98704__skype-43-linux-indicator-icons.png[/IMG]


On the Internet, I do not even close like not found.

Found the magic: 
If you detach the panel from the bottom and move up on a menu without any problems. Even if after drag it down again and fix the problems at the bottom of the same does not arise. But after restarting Skype history repeats itself.

[http://youtu.be/ijOB07RU0Ao](http://youtu.be/ijOB07RU0Ao)


OS: xfce@ubuntu 14.04x64

---

### Post by bizhat on 2014-08-18
Nice. On Ubuntu 14.04 the tray indicator is completely missing. Hope microsoft will fix it one day :)

---

### Post by colotunbabay2010 on 2014-08-18
> **bizhat said:**
> Nice. On Ubuntu 14.04 the tray indicator is completely missing. Hope microsoft will fix it one day :)
Your bug has solved, you must install ```
[COLOR=#000000][FONT=Ubuntu Beta]sudo apt-get install sni-qt:i386[/FONT][/COLOR]
```

---

### Post by bizhat on 2014-08-18
> **colotunbabay2010 said:**
> Your bug has solved, you must install ```
[COLOR=#000000][FONT=Ubuntu Beta]sudo apt-get install sni-qt:i386[/FONT][/COLOR]
```

Thank you, got it working, keep posting tips like this :D

---

### Post by colotunbabay2010 on 2014-09-02
Solved [COLOR=#000000][FONT=Ubuntu Beta]sudo apt-get purge sni-qt:i386[/FONT][/COLOR]

---

