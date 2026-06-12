---
title: "Gnucash starts and then disappears"
date: 2006-03-16
forum: Desktop Environments
---

### Post by Nick Payne on 2006-03-16
I used the instructions at [http://help.ubuntu.com/starterguide/C/ch03s04.html](http://help.ubuntu.com/starterguide/C/ch03s04.html) to install Gnucash in Ubuntu 5.10. When I try to run it, the splash screen comes up saying Gnucash 1.8.10, and a succession of messages at the bottom of the splash screen about loading modules. Then the splash screen disappears but no application window appears, and ps -fe doesn't show any running process that would seem related. Any ideas on this?

Nick

---

### Post by Nick Payne on 2006-03-16
I did what I should have done previously, and ran Gnucash from the command line. Upon which I see the error messages:

Warning: gnucash_style_set_register...(): Cannot load font: -adobe-helvetica-medium-r-normal--*-120-*-*- *-*-*-*

Fatal Error: gnucash_style_set_register...(): Cannot load fallback font: -adobe-helvetica-medium-r-norma l--*-120-*-*-*-*-*-*

Warning: gnucash_style_set_register...(): Cannot load font: -adobe-helvetica-medium-o-normal--*-120-*-*- *-*-*-*

Fatal Error: gnucash_style_set_register...(): Cannot load fallback font: -adobe-helvetica-medium-o-norma l--*-120-*-*-*-*-*-*

How do I fix this (not knowing Linux very well)?

---

### Post by Nick Payne on 2006-03-16
Further investigation shows that the problem is due to running Guncash from a FreeNX client session. If I use it at the actual Linux machine console then it works. So So I guess I need to setup a font server - I had a quick hunt through the forums and wiki but didn't find any coverage of this topic.

---

