---
title: "kde system tray two rows of icons"
date: 2007-07-02
forum: Desktop Environments
---

### Post by Neuralgia on 2007-07-02
for some reason on my "system tray" icons, i get only one line of them (bottom right)

I used to have two lines (rows?) just like the quick launch icons (bottom left)

how can i get this back... i've tried everything, and can't seem to find the correct menu

Thnks

[IMG]http://img242.imageshack.us/img242/4592/snapshot4fy3.jpg[/IMG]

---

### Post by linuxwizard on 2007-07-02
You have to change the size of your kicker. Make it bigger. I do it on my Dapper Kubuntu.

---

### Post by Neuralgia on 2007-07-02
i can't seem to resize, i can MOVE the whole System Tray, but can't resize.

Pretty weird, since i didn't mess with anything :?

---

### Post by Erunno on 2007-07-02
Right-Click on the panel, choose Configure Panel, goto Layout. You'll find a slider where you can adjust the hight.

---

### Post by Neuralgia on 2007-07-02
i think i'm not explaining myself correctly.

it's not the WHOLE bar... its just the System tray section

still, not being able to fix this :(

---

### Post by linuxwizard on 2007-07-02
I don't know how you can resize just the system tray. I am not on my Kubuntu now using Ubuntu looking at some of my notes. I right click the kicker > configure panel > the window that comes up should be the one you want. On there is a drop down menu with i think is small, tiny, large, custom > choose custom. Than below that should say size: 56 pixels change it to 48 > hit apply. That is how I get double row setup.

---

### Post by Neuralgia on 2007-07-02
didn't change

my desktop looks like this
[IMG]http://img103.imageshack.us/img103/3812/snapshot4od3.jpg[/IMG]

my laptop used to be the same... now it's like this
[IMG]http://img240.imageshack.us/img240/2738/snapshot5lf8.jpg[/IMG]

:(

---

### Post by Neuralgia on 2007-07-03
Ok, found put what the problem was: Google Desktop.

This icon has a size that makes it impossible to display two rows.

End of story :(

---

### Post by strabes on 2007-07-30
here's a replacement for google desktop: ```
find -name <string>
```

---

### Post by perspectoff on 2008-05-06
When you configure your panel ( <i>Right Click</i> on the Panel bar-->Arrangement->Size-->"Custom" ) so that the size is less than 34 pixels, it will display as a single row.

When it is more than 34 pixels but less than 52 pixels, it will display as a double row. When it is greater than 52 pixels, it will display as a triple row.

(You can also choose "Tiny" or "Small" and it will be a single row, whereas "Normal" will display as a double row, and "Large" will display as a triple row.)

---

