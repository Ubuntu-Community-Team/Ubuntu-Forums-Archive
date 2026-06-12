---
title: "compiz + fglrx = stottering video playback ?"
date: 2008-03-13
forum: Desktop Effects &amp; Customization
---

### Post by desperado666 on 2008-03-13
Hi

I Have installled catalyst 8.3 and i see a blank screen with activated compiz and totem. If i play around with multimedia system i can get a video playyback but with stottering. with deactivated compiz there are no problems at all. 

Fixes?

---

### Post by cHrIs89 on 2008-04-08
Same problem here.. I hope  I will find a solution, it's annoying.

---

### Post by +++ IGOR +++ on 2008-04-08
I had the same problem. The easiest solution is to use VLC and enable the X11 output module.

This gave me fine consistent videoplayback without tearing.

What you have to do is: In VLC. Open preferences -> video -> output modules -> (choose advanced) and then choose "X11" module.

---

