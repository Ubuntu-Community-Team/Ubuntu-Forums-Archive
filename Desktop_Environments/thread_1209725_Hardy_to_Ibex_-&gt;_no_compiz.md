---
title: "Hardy to Ibex -&gt; no compiz"
date: 2009-07-10
forum: Desktop Environments
---

### Post by frogotronic on 2009-07-10
Just upgraded to Ibex and lost my compiz.  I get a "no composite extension" warning and when I try compiz --replace i get this output
```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: /usr/bin/metacity 
Xlib:  extension "RANDR" missing on display ":0.0".
```


What am I missing?

---

### Post by raymondh on 2009-07-10
Some thoughts:

1.  System > administration > hardware drivers and enable the driver for your card.
2.  RT. Click on your desktop > Change desktop background > Visual effects > set to normal or extra
3.  Do a compiz-check

[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

Good luck.

---

