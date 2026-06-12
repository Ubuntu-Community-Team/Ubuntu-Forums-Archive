---
title: "Nestopia Packages"
date: 2008-08-16
forum: Gaming &amp; Leisure
---

### Post by Master O on 2008-08-16
Just for future reference in this sub-forum, what are the names of the specific packages that Nestopia needs in order to compile properly in Ubuntu?

The nestopia site just says:

> - General development (also called &#8220;GCC&#8221; and &#8220;G++&#8221;) plus their dependancies
- GTK+ 2.4 or later and the development packages
- The ALSA library and it&#8217;s development packages
- SDL 1.2.12 or later and it&#8217;s development package

---

### Post by Perfect Storm on 2008-08-16
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install build-essential
sudo apt-get install libgtk1.2-dev libasound2-dev libsdl1.2-dev
```

---

### Post by Loranga on 2008-09-16
I manage to compile it, but when I run it I just get a grey screen. :S

---

### Post by disturbedite on 2008-09-16
you need to run it from command line & post the output.

---

