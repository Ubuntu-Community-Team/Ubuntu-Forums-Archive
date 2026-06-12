---
title: "ubuntu panel &amp; internet"
date: 2009-05-25
forum: Desktop Environments
---

### Post by mr_gourami on 2009-05-25
is there a way to add a button on the standard ubuntu panel that will open a specific web page? 

i know i can add a button to open firefox, i just want a button to open like [www.google.com](www.google.com) and [www.podiobooks.com](www.podiobooks.com) etc...

---

### Post by Sarai the Geek on 2009-05-25
Add an application launcher and set the command to:

```
firefox http://www.google.com
```

You can change the address to whatever you want, just don't forget the [http://!](http://!)

---

### Post by Cery on 2009-05-25
Add to Panel > Custom Application Launcher

In command, 

```
firefox "your url here"
```

E.g. firefox "http://www.gmail.com" to open Gmail

:)

---

### Post by Cery on 2009-05-25
Beat me to it, but I'm glad we concur. :P

---

### Post by mr_gourami on 2009-05-25
thanks yall. last question. is there a way to add more icons? this way i dont have a dozen icons for these webpages exactly the same? i know how to change the icon however there is only a dozen or so options. i tried browsing other folders but no icons show up in the browser

---

### Post by Sarai the Geek on 2009-05-25
> **mr_gourami said:**
> thanks yall. last question. is there a way to add more icons? this way i dont have a dozen icons for these webpages exactly the same? i know how to change the icon however there is only a dozen or so options. i tried browsing other folders but no icons show up in the browser

Try these locations:

/usr/share/icons/Human/scalable/apps
/usr/share/icons/Human/scalable/categories
/usr/share/icons/gnome/scalable/apps
/usr/share/icons/gnome/scalable/categories

You can also download more icons from various places around the internet. I recommend you check gnome-look first:
[http://www.gnome-look.org/index.php?xcontentmode=120x121](http://www.gnome-look.org/index.php?xcontentmode=120x121)

---

