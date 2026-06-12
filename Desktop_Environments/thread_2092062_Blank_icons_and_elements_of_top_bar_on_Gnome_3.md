---
title: "Blank icons and elements of top bar on Gnome 3"
date: 2012-12-06
forum: Desktop Environments
---

### Post by edvar on 2012-12-06
I'm using Ubuntu 12.04 with Gnome 3 and NVidia driver 304.64. After login everything works fine but eventually all icons go blank and some elements of the top bar don't display correctly, mostly also going blank. It can only be fixed by restarting X. Any ideas?? It's really annoying. 

I attached 2 pictures, one with the normal desktop and another after the problem happens.

[ATTACH]228299[/ATTACH]

[ATTACH]228300[/ATTACH]

---

### Post by edvar on 2012-12-16
bump

---

### Post by Frogs Hair on 2012-12-16
Check Looking Glass for errors. Alt + F2 ```
lg
```Esc key to exit.

---

### Post by jbicha on 2012-12-18
Does it still happen if you use the default themes?

---

### Post by edvar on 2012-12-18
Yes, using the default Adwaita theme was the first thing I tried however I still have the same problem. I noticed it happens more often if I try to open firefox or nautilus.

In regards to "lg", it doesn't work:

$ lg
lg: command not found
$ sudo apt-get install lg
[sudo] password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package lg

---

### Post by Frogs Hair on 2012-12-19
The fact that Looking Glass doesn't appear makes me wonder if the installation went badly. There should be a semi transparent window that appears and displays information. Errors would appear first and this feature has been there since Gnome 3 was released.

Use Alt +F2 instead of the terminal. ```
lg
```

---

