---
title: "Firefox crashes"
date: 2005-04-09
forum: Desktop Environments
---

### Post by beeldings on 2005-04-09
When I attempt to print from within Firefox, the browser shuts down. I always use File>Print using to print with Firefox. This error also occurs when I try to view the Print Preview (File>Print Preview) of a web page.

Also, when I try to download files using Firefox, usually by right-clicking on the link and choosing Save Link As, either the browser will shut down or the location dialog box will appear prompting me to choose a download location. I can choose the download location just fine, but when I click save, nothing happens, meaning that the file is not downloaded. The only way I can download something is if I run wget from a terminal. I have a few extensions installed on Firefox including Web Developer and Flashblock.

The printing problem appears to be exclusive to Firefox as I can print using other applications on my system.

Has anyone else experienced this problem? If so, how did you fix it?

---

### Post by soul_rebel on 2005-04-10
rename your ~/.mozilla to something different, restart firefox and see if the problem is still there.

---

### Post by beeldings on 2005-04-10
I renamed my ~/.mozilla folder to _.mozilla_ and I restarted Firefox. Suprisingly, this solved my problem and I can now print in Firefox without it crashing.

---

### Post by soul_rebel on 2005-04-11
I am not surprised :wink:

---

