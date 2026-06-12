---
title: "font problem in ubuntu 6.06"
date: 2006-09-16
forum: Desktop Environments
---

### Post by poly on 2006-09-16
I have tried to search for a solution, but I haven't found anything... 
When I try to run an application I get the following and application exits:
2006-09-10 14:52 XLoadQueryFont: failed creating font set -*-lucida-medium-r-*-*-10-*-*-*-*-*-iso10646,-*-helvetica-medium-r-*-*-11-*-*-*-*-*-iso8859-5,-*-*-*-r-*-*-10,*
2006-09-10 14:52 XLoadQueryFont: failed creating font set -*-lucida-medium-r-*-*-10-*-*-*-*-*-iso10646,-*-helvetica-medium-r-*-*-11-*-*-*-*-*-iso8859-5,-*-*-*-r-*-*-10,*
2006-09-10 14:52 XLoadQueryFont: failed creating font set -*-lucida-bold-r-*-*-10-*-*-*-*-*-iso10646,-*-efont serif,-*-goha tibeb-zemen,-*-helvetica-bold-r-*-*-11-*-*-*-*-*-iso8859-5,-*-*-*-r-*-*-10,*
2006-09-10 14:52 XLoadQueryFont: failed creating font set -*-lucida-medium-r-*-*-10-*-*-*-*-*-iso10646,-*-helvetica-medium-r-*-*-11-*-*-*-*-*-iso8859-5,-*-*-*-r-*-*-10,*
2006-09-10 14:52 XLoadQueryFont: failed creating font set -*-times-medium-r-*-*-10-*-*-*-*-*-iso10646,-*-times-medium-r-*-*-11-*-*-*-*-*-iso8859-5,-*-*-*-r-*-*-10,*
2006-09-10 14:52 XLoadQueryFont: failed creating font set -*-times-bold-r-*-*-10-*-*-*-*-*-iso10646,-*-times-medium-r-*-*-11-*-*-*-*-*-iso8859-5,-*-*-*-r-*-*-10,*
2006-09-10 14:52 XLoadQueryFont: failed creating font set -misc-fixed-bold-r-*-*-10,-*-*-*-*-*-*-10,*

I guess, I need to install some fonts, I tried to install msttcorefonts and tried to copy fonts from Windows and run fc-cache, edit xorg.conf FontPath to include full path to copied fonts. Nothing helped.

---

### Post by statue on 2006-09-16
Is it whenever you try to run any application?

---

### Post by poly on 2006-09-16
Yes, this happens every time I try t run the application

---

### Post by statue on 2006-09-16
Did you just install ubuntu? If so, has this been going on ever since you installed it?

---

