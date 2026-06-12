---
title: "GUI Tool as Consol for Apache and MySql ?"
date: 2010-02-24
forum: Desktop Environments
---

### Post by saidbakr on 2010-02-24
Hello,
Any one know a GUI tool that acts as a consol for Apache and/or MySQL in which I could able to start, restart and stop Apache and MySql servers on my computer that running Ubuntu desktop?

Of course, the tool should be Gnome compatible and it is better to be able finding it in Synaptic.

Best Regards

---

### Post by Richard1979 on 2010-02-24
Try Webmin, it runs in your browser and it's open source.

---

### Post by wojox on 2010-02-24
```
sudo service apache2 restart
```

Replace apache2 with mysql and restart with start or stop. Pretty simple from the cli.

---

### Post by saidbakr on 2010-02-24
Where could I find webmin? in addition you regarded that it runs from the web browser, so it may need a web server and this will add a new performance tasks to the computer.

---

### Post by saidbakr on 2010-02-24
> **wojox said:**
> ```
sudo service apache2 restart
```Replace apache2 with mysql and restart with start or stop. Pretty simple from the cli.

yes I know this is simple, however, Clicking is more simple than writing in cli, is not it? ;)

However, If there any way to make this command in a short cut that placed on the desktop I will be appreciated to know it.

---

### Post by mthalis on 2010-02-24
Refer this [http://www.webmin.com/download.html](http://www.webmin.com/download.html)  or [http://www.webxpert.ro/andrei/2009/10/29/install-webmin-on-ubuntu-server-or-desktop-9-10-karmic-koala/](http://www.webxpert.ro/andrei/2009/10/29/install-webmin-on-ubuntu-server-or-desktop-9-10-karmic-koala/)  those links help you to instaled webmin.

---

### Post by saidbakr on 2010-02-25
After some thinking I found that the solution of wojox is fine but it needs a little modification to meat my requirement. The modification is a question.

How could I make something like batch file *.bat like those in Windows but in linux to perform the regarded command by just double click on a file?

---

