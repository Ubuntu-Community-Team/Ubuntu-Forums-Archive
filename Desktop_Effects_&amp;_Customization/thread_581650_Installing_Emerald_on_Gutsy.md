---
title: "Installing Emerald on Gutsy"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by orbital on 2007-10-19
I have Desktop Effects working properly and now I need to get Emerald installed. How can I install it?

---

### Post by ravenus on 2007-10-19
Search for 'emerald' in synaptic and you will find the emerald theme manager. As of now there's only one theme available by default (red border) and the link to fetch GPL themes seems to be non-functional.

---

### Post by joshuachad on 2007-10-19
make sure you have subversion installed

---

### Post by Ylang on 2007-10-19
> **joshuachad said:**
> make sure you have subversion installed

What does that mean? I am kind of new to linux, sorry.

---

### Post by em007a on 2007-10-19
This worked for me...

[URL="https://svn.generation.no/emerald-themes"]> sudo svn ls https://svn.generation.no/emerald-themes


[/URL]

---

### Post by neymac on 2007-10-20
You can download the emerald-themes from
[http://packages.ubuntu.com/feisty/x11/emerald-themes](http://packages.ubuntu.com/feisty/x11/emerald-themes)
This package is for Feisty, but works with Gutsy here.

---

### Post by Tachyon1000 on 2007-10-20
You can also get themes here:

[http://themes.beryl-project.org/](http://themes.beryl-project.org/)

---

### Post by Redenbacher on 2007-10-20
I downloaded emerald right through synaptic, works like a charm ;)

---

### Post by mahado051 on 2007-10-22
i installed emerald on gutsy gibbon, but it doesn't work... it's necessary configure it?

---

### Post by Redenbacher on 2007-10-23
If you have the compiz-fusion config settings manager installed, go in to it and enable the Window Decorator Plugin. Go into it's settings, and type "emerald" in to the command portion of the window. This will allow compiz-fusion to decorate the windows with emerald :)

---

### Post by dennis.groome on 2007-10-23
I have emerald installed and the Windows Decoration plug-in enabled as well as "emerald" filled in for command. How do I get emerald to load so I can load my theme I was using in Beryl before I upgraded to Gutsy?

---

### Post by marsmissionaries on 2007-10-23
alt + F2 and type in emerald --replace

---

