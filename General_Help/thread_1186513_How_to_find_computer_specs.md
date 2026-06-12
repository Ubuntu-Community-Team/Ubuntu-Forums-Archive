---
title: "How to find computer specs"
date: 2009-06-13
forum: General Help
---

### Post by miggerish on 2009-06-13
Where can I find my computer specs for knowing if I can run WoW or not?  I have the latest version of Ubuntu.

---

### Post by Bucky Ball on 2009-06-13
System->Administration->System Monitor, under the general tab.

---

### Post by Evontroy on 2009-06-13
Click on System>Administration>System Monitor. You will then need to click on the tab that says "System".

---

### Post by Bucky Ball on 2009-06-13
Yep, system, not general. :)

---

### Post by miggerish on 2009-06-13
Thanks for your help!

---

### Post by Evontroy on 2009-06-13
There's also a really cool app called "PerlMon" that can give you a more expanded view of your system. Here's the link: [http://www.overclock.net/3950718-post249.html]("http://www.overclock.net/3950718-post249.html")

---

### Post by ajgreeny on 2009-06-13
All you really need for all the system info you could possibly get is *hwinfo*, a gui app, or even simpler ```
sudo lshw >hardware.txt
``` in the terminal. This will produce a simple text file (hardware.txt) in your home folder, with all the system hardware information, absolutely everything.

---

### Post by Cheesemill on 2009-06-13
Or for an easier read you can do:
```
lshw -html > hardware.html
```

And then open the resulting file n a browser.

Cheesemill

---

