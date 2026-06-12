---
title: "Want a fuzzy clock for the GNOME panel? Here you go, please test."
date: 2008-12-14
forum: Desktop Environments
---

### Post by dsm iv tr on 2008-12-14
I recall that people were asking for a "fuzzy" clock applet for the GNOME panel, it being something in KDE that GNOME lacked, and I really missed. Coincidentally, I also needed to learn to use PyGTK.

So I made one + an installer script. :)

You can also run it manually in a window with
$ python ./FuzzClock.py --in-window

I hope some people will find this useful either in the transition from KDE or just for the heck of it. Constructive suggestions/bug reports are welcome. I'm sure there's at least a few things I could do to make it better.

[http://code.google.com/p/fuzzy-clock/](http://code.google.com/p/fuzzy-clock/)

As of 1.0.3, I've added a proper README, clarified the installer script, and made *12 hour* mode the default mode, as per requests.

---

### Post by benerivo on 2008-12-14
Nice, i hate being constantly told exactly what time it is. Could you get it to read in a 12hr clock rather than 24hr, so that it syas 'twenty past ten' rather than 'twenty past twenty-two'.

---

### Post by dsm iv tr on 2008-12-14
As of version 1.0.2, 12-hour support is working and toggleable by a right-click menu item.

Thanks again for your input, benerivo!

---

### Post by Sabljak on 2009-05-10
> **dsm iv tr said:**
> 

I hope some people will find this useful either in the transition from KDE or just for the heck of it.

Very nice, i like this clock! How could I translate it in German? If I do replace the timeways in FuzzClock.py with german timeways, I get a Error:Can't load »OAFIID:GNOME_FuzzClock«. What more should I do to have it in other languages?

---

### Post by Sabljak on 2009-05-17
> **Sabljak said:**
> Error:Can't load »OAFIID:GNOME_FuzzClock«

I've solved the Problem, it was the "Umlaut" (üöä) that Python was not able to read. I've changed it in "ue" "oe" and "ae", it's working fine now. Thanks anyway!

---

### Post by Stenudd on 2009-06-28
> **Sabljak said:**
> Very nice, i like this clock! How could I translate it in German? If I do replace the timeways in FuzzClock.py with german timeways, I get a Error:Can't load »OAFIID:GNOME_FuzzClock«. What more should I do to have it in other languages?

Simply add this
    # -*- coding: utf-8 -*-
after
    #!/usr/bin/env python

it will look like this 
    #!/usr/bin/env python
    # -*- coding: utf-8 -*-

Then you can use it with all your special chars

Thanks for great app :-)

---

