---
title: "[SOLVED] usps shipping label printing in linux"
date: 2009-04-19
forum: General Help
---

### Post by maclenin on 2009-04-19
This issue (and my wife) had been haunting me (about it) for a long while...until I stumbled across this "combination" solution, as articulated:  [_here_]("https://bugs.launchpad.net/ubuntu/+source/poppler/+bug/310750") + [_here_]("http://fixunix.com/mozilla/537442-solution-problem-usps-website-re-label-printing.html").

Essentially...

...install a .pdf reader that can interact with the USPS label printing interface (evince and acroread had not worked for me)...
```
sudo aptitude install xpdf
```
...set the browser up (Firefox 3) to open the label file (a .pdf) when the USPS printing applet is launched...
```
1. Edit
2. Preferences
3. Applications
4. Under "Content Type" find "PDF document"
5. Under "Action" select "Use xpdf"
6. Close the Applications window
```

...after a few anxious seconds (back at USPS.com)...
...xpdf opens the label file...
...a mouse pointer engages the print button...
...and the printer attached to my Intrepid desktop spits out a shiny new USPS shipping label!

---

### Post by celem on 2009-11-09
Adobe didn't work for me (infinite loop connect/download). I switched to evince and it works perfectly. I use Ubuntu 8.04 Mint variant.

---

### Post by maclenin on 2009-11-10
Thanks for the info. **celem**....

---

