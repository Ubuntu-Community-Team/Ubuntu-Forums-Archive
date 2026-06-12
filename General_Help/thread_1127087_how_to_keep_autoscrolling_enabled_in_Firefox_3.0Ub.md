---
title: "how to keep autoscrolling enabled in Firefox 3.0/Ubuntu 9.04 beta"
date: 2009-04-16
forum: General Help
---

### Post by szenith on 2009-04-16
okay so I'm having trouble keeping autoscrolling enabled in Firefox 3 with Ubuntu beta 9.04.. 

for example I've set the autoscroll in about:config to true

general.autoScroll;true

and I've set the preferences in Advanced-->General "[x]enable auto scrolling"

but whenever I restart Firefox it doesn't seem to save the settings and I'm left to enable auto scrolling again. 

A problem I had earlier was, since this is an install I did next to a Windows XP partition, I for some reason decided to import my information from windows, and what was happening when I was trying to run Firefox was that all the buttons were greyed out, untill I ran it once as owner and then it didn't do that anymore. But now I'm having this autoscrolling problem and enabling those settings (for autoscrolling) as owner does  not keep them saved. So I don't know what to do really. 

Thank you!

---

### Post by szenith on 2009-04-16
oh and in case anyone doesn't know, autoscrolling is when you click the mouse wheel and drag the mouse to quickly scroll a page, but you should know this!!

---

### Post by szenith on 2009-04-16
well, the fix for this was actually easy, i just renamd my .mozilla directory to .mozilla_old and let it make a new profile..and that basically got rid of the problems that i assume were created with ubuntu importing stuff from windows firefox during the install

---

