---
title: "printing margins"
date: 2007-04-14
forum: Desktop Environments
---

### Post by nadamsieee on 2007-04-14
Whenever I try to print using my [HP-PSC-1210xi]("http://h10025.www1.hp.com/ewfrf/wc/genericDocument?lc=en&cc=us&docname=bpu00691"), the bottom of the image/document/whatever gets cut off. I've tried fiddling with the HWMargins settings in my PPD file, but it doesn't seem to help.

Any ideas?

---

### Post by Seisen on 2007-04-16
What driver are you using this could cause the problem?

---

### Post by nadamsieee on 2007-04-21
The problem was due to [user error on my part]("http://permalink.gmane.org/gmane.comp.printing.hplip.user/3055").

For posterities' sake, here was what I had to do: set the correct default paper size.
[LIST=1]
[*]browse to [http://localhost:631/printers/](http://localhost:631/printers/)
[*]select **Select Printer Options**
[*]select the appropriate page size (in my case Letter)
[*]click **Set Printer Options**
[*]enter your login name and password
[/LIST]

---

