---
title: "Bar graphs not working in Kubuntu's system monitor?"
date: 2006-09-26
forum: Desktop Environments
---

### Post by kwilliam on 2006-09-26
I'm using Kubuntu, and trying to set up the System Monitor applet to show my CPU load. I want a small, narrow meter that just shows the instantaneous CPU load. However, I can't seem to get any BarGraph (or "dancing bar") plots. I can get the other graph styles, e.g. "Signal Plotters" and "Multimeter". I can't get "BarGraph" to work in either KSysGuard or the applet. All I get is an error icon like seen in the screenshots.

Any idea if I'm doing wrong, or if this is a bug? And are there any simple alternatives to using the default System Monitor applet?

---

### Post by Mr Frosti on 2006-09-26
I am guessing that you might have an atypical processor in your machine. Are you running  a 64 bit, Dual Core, or PPC processor? If so, then the program might not be able to interpret the data for this type of configuration.

There are many alternatives to the ksysguard utility. If you are just curious as to the load of the machine, "top" if a fantastic utility that runs in a teminal. 

Other options can be discovered by doing a search on [Google]("http://www.google.com/search?q=kde+cpu+monitor")

---

### Post by kwilliam on 2006-09-27
I'm just using an Athlon XP processor, so I doubt it has to do with the processor.  For now I'll just have a really thin time plot.

---

### Post by kwilliam on 2006-09-27
I found a space efficient monitor I like. I searched for "system monitor applet" in Symantic, and installed "kicker-applets". It has a Simple System Monitor that shows just the current CPU, memory, swap usage in vertical (or horizontal) bars.

Thanks for the tip Mr. Frosti.

---

