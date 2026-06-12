---
title: "Weather Report"
date: 2007-03-11
forum: Desktop Environments
---

### Post by z987k on 2007-03-11
I like the applet that give the weather and temperature on a panel, but I really wish it had a few more features.  One way or another it gets it's information from a metar, but it doesn't display everything... like cloud height, anything that's not in the automated report, etc.  

So my question is, is there a program out there similar with more features, yet is still an applet?

Also, if none exist where can I find the source for the applet?  I might be able to modify it to suit my needs.

---

### Post by yabbadabbadont on 2007-03-11
If you can figure out the name of the package, "sudo apt-get source package", should pull down the source deb for you.

---

### Post by z987k on 2007-03-11
it comes in the gnome-applets package... I guess that'll be a big source file.

---

### Post by yabbadabbadont on 2007-03-11
Probably not that big as there aren't that many applets in that package.  You will probably want to run, "sudo apt-get build-dep gnome-applets", first so that you will have all the stuff required to rebuild them after you change them.

---

### Post by yabbadabbadont on 2007-03-11
Ok, it just depends on what you consider "big".  ;)

```
/home/daffy # apt-get -s source gnome-applets
Reading package lists... Done
Building dependency tree... Done
Need to get 9611kB of source archives.
Fetch source gnome-applets

```
With my connection, it would take about 15 to 20 seconds.  :mrgreen:

---

### Post by z987k on 2007-03-11
Well I think it's beyond my very limited programing.  Out to find a new app, or mail the devs, lol.

---

### Post by z987k on 2007-03-13
I've still found nothing that really fits my needs.  I would be happy with even something that sits on the desktop and displays the metar in it's coded form.  TAF's to but i'll not get too picky.

---

