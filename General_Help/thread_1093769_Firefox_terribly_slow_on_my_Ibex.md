---
title: "Firefox terribly slow on my Ibex"
date: 2009-03-11
forum: General Help
---

### Post by Unikraken on 2009-03-11
I need help troubleshooting an issue with my browser, Firefox 3.0.7, on Ubuntu 8.10 Intrepid Ibex. If I get more than 4 or 5 tabs open the thing slows down to a crawl. It only started recently and I can't think of anything that would have done this. 

I have a gig of ram and a dual core processor, and I really only use this lap top for internet surfing so nothing else is running the background that should be doing this.

I'm running the following addons: download statusbar, speed dial, tab mix plus, urlbar extensions, and ubuntu firefox modifications.

I really don't know where to begin on fixing this issue. Does anyone know a way to up the amount of memory or cache FF uses? Many thanks to anyone who responds.

---

### Post by madverb on 2009-03-11
Disable Add-ons until you find the one causing the problem. If it's none than you will have to try something different. Possibly recreating your firefox profile in your home folder.

---

### Post by martrn on 2009-03-11
Switch off tracker on the ubuntu desktop.  (Its on your top bar and slows thing down lots).  Install the correct X11 graphics drivers/kernel modules for your graphics card.  Make sure you install upto-date flash plugin from adobe.  The flash player is pretty buggy, but the most upto date one always works better.  Not the one from any repository.
[URL="http://www.psychocats.net/ubuntu/flash"]
http://www.psychocats.net/ubuntu/flash[/URL].  Un-install any buggy Firefox plug-ins.

Run system monitor by System-->Administration-->SystemMonitior   and see what processors are running that slow down your system.  If its just firefox that is using up cpu time and memory then it maybe a plug-in firefox or flash.  If X11 is at the top of the list it maybe compiz, a driver problem or something else.

---

### Post by Sircaa on 2009-03-11
If it's a problem with memory usage, try this:

Go to about:config, it will load the FF config page.

Type in browser.cache.disk.capacity into the filter.

Double click on it.  Raise the number to allow FF to use more memory, just experiment with this number until you get it right.

Try raising it in increments of 10,000 or so.

Good luck,

Sircaa

---

### Post by thehipho on 2009-03-27
There's nothing that can be done to improve speed in Firefox,
 except to turn-off Compiz, hehe.

---

