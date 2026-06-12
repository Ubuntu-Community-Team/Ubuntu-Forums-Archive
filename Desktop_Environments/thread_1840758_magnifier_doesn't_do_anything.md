---
title: "magnifier doesn't do anything"
date: 2011-09-08
forum: Desktop Environments
---

### Post by Arndt on 2011-09-08
I am trying to use the Gnome magnifier (/usr/bin/magnifier). When I start it from the command line, all windows are redrawn, so it looks like it does something, but then everything looks like before and I don't see any magnification anywhere. The warnings on stdout are these:

```
(lt-magnifier:4240): Bonobo-WARNING **: Assigning a default value to a non readable property 'source-display-screen'

(lt-magnifier:4240): Bonobo-WARNING **: Assigning a default value to a non readable property 'target-display-screen'
** Message: added event source to xfixes cursor-notify connection
** Message: added event source to composite connection
** Message: set source bounds to 0,0; 1920,1080
initial viewport 1920 1080

```

The program then just sits there, although I can use all windows just as before. When I interrupt the program with ^C, all windows are redrawn again, so it does nothing harmful, it just doesn't work for me.

What could be wrong?

I'm using Lucid (10.04).

---

### Post by Arndt on 2011-09-09
bump

---

### Post by Copper Bezel on 2011-09-09
Are you using Compiz? If so, it would make more sense to use the Enhanced Zoom Desktop plugin in ccsm. Gnome (2) Magnifier is written for Metacity.

---

### Post by Arndt on 2011-09-09
> **Copper Bezel said:**
> Are you using Compiz? If so, it would make more sense to use the Enhanced Zoom Desktop plugin in ccsm. Gnome (2) Magnifier is written for Metacity.

I am using metacity.

---

### Post by sureshvv on 2012-11-23
Looks like you need to use either -h or -v flags (horizontal or vertical). But half the screen is unavailable. So this looks pretty useless. kmag may be better.

---

### Post by wildmanne39 on 2012-11-23
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

