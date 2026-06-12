---
title: "LibreWriter and Java Conflict"
date: 2017-11-19
forum: Desktop Environments
---

### Post by Country squire on 2017-11-19
I know there is an answer to this, but I can't find it.

I am running Ubuntu 16.04 with Unity
Installed Packages
LibreOffice 5
JavaJDK Java 8 and Policy Tool
Iced Tea Web Control Panel

Platform: HP ProBook 4520S

Ubuntu runs perfectly.
This morning, 20 November, I did a successful update.
I started LibreWriter and it asked me if I wanted Java.
I accepted.
LibreOffice dropped out. If I try to restart it, the first screen starts, then it disappears off the screen.
LibreCalc runs well.

I clearly have a conflict somewhere.
Can someone tell me how I can fix it.

Regards

Country Squire

---

### Post by ajgreeny on 2017-11-20
Open a calc page and go to Tools Options. From there uncheck the option to use java as shown in my screenshot.  Hopefully that will allow you to start LO Writer once again, assuming java really is the problem.

Do you really need java in LO for the way you use it; it is shown as enabled in my screenshot but normally I do not have it enabled and do not miss it, though your use of LO may require it.

If disabling java does not work for you try renaming the **~/.config/libreoffice** folder as a backup and then start LO to see if it is now solved.

---

### Post by Country squire on 2017-11-20
Thank you ajgreeny.
Thank you for your prompt response. Your suggestion succeeded. I don't have a use for Java in LO, so I will leave it unchecked.
Thanks once again
Country Squire

---

### Post by ajgreeny on 2017-11-21
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

