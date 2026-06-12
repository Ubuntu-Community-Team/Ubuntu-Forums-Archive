---
title: "Beryl not enabled on start-up"
date: 2007-02-03
forum: Desktop Environments
---

### Post by Razer on 2007-02-03
I just installed beryl and it works like a charm except for the fact that I have to manually start it. I added /usr/bin/beryl-start into the startup programs and it won't work. Is there something else I need to include?

---

### Post by Razer on 2007-02-03
By the way I used the guide on this page [http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit)

---

### Post by insert_name_here on 2007-02-03
When you get to the login screen, click the menu in the lower left corner, click "settings" and choose XGL (or AIGLX).  It should start, if its the same as my system.

---

### Post by Razer on 2007-02-03
I looked into sessions but there was no xgl or anything like that. The only options were default and gnome. What do I have to do in order to be able to select it from there?

---

### Post by Razer on 2007-02-03
I'm using 6.10 if that matters

---

### Post by jjross on 2007-02-03
I think your on the right track, try "usr/bin/beryl" leave the start off of it

---

### Post by Razer on 2007-02-03
I typed that in and it did not make the xgl session show up and also made the top bar of my windows to disappear. I'm kinda a newb so I don't know if this matters or not but when I type "usr/bin/beryl" into the terminal it says "no such file or directory".

---

### Post by rsambuca on 2007-02-03
Why don't you just add "beryl-manager" into your sessions startup manager?

---

### Post by mysticrider92 on 2007-02-03
You will need to add beryl, emerald --replace, and beryl-manager to your startup programs, and it should work fine. You don't need file paths.

---

### Post by Razer on 2007-02-03
Thanks for all the replies. I typed "beryl-manger" into the startup programs list and beryl started automatically during login.

---

