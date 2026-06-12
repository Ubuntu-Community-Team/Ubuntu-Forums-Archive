---
title: "Need help setting up a proper Eterm launch at startup"
date: 2005-08-12
forum: Desktop Environments
---

### Post by Ghost Freeman on 2005-08-12
Hi, i've been using Eterm for some time now and I like it so far, but every time I try to start it up using Gnome sessions, the background is different from my desktop, and in order to get it to match, I haveta launch it again from a terminal (my graphics card dosen't support transparency so I haveta fake it with -O). I took a picture of it running with the wrong background here: [http://img359.imageshack.us/img359/6850/whatthehell3yy.png](http://img359.imageshack.us/img359/6850/whatthehell3yy.png)

The command I run in Sessions is set to order 60, and is shown below:
```
Eterm -f white -g 70x20+0+0 -n DeskTerm -O -x --buttonbar false --scrollbar false
```

Anyone know how to make this work properly?

---

