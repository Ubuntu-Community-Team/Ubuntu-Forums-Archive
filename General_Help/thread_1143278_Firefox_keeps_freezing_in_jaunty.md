---
title: "Firefox keeps freezing in jaunty"
date: 2009-04-29
forum: General Help
---

### Post by josephellengar on 2009-04-29
I'm in gnome 64 bit.  My computer is 800 mhz dual core, 1 gb ram, and a 128 mb nvidia graphics card.  Firefox keeps freezing.  This is a new problem, since I installed jaunty, and occurs when I am navigating between  pages.  I currently have a number of addons installed, including adblock plus, greasemonkey (not that many scripts at all), stumbleupon, WOT, speed dial, personal menu, user agent switcher, and webmail notifier.  This is a completely new problem.  I'm sorry if something has already been posted about this, but I coldn't find anything recent about this problem.

---

### Post by oOarthurOo on 2009-04-29
First thing to try is to create a new profile and not add any extensions. Hit Alt+F2 then type "firefox -P" ... create a new profile called test.

See if you can reproduce the freezing error. If you can't, then the problem is likely with one of the plugins, and I'd recommend disabling them all then re-enabling one at a time to try and locate the offending one. 

If the problem persists the the problem is in fact with firefox, so next I'd run firefox from the terminal (just open the terminal and type "firefox") then when it freezes flip over to the terminal and copy the output back here.

---

### Post by josephellengar on 2009-04-29
> **oOarthurOo said:**
> First thing to try is to create a new profile and not add any extensions. Hit Alt+F2 then type "firefox -P" ... create a new profile called test.

See if you can reproduce the freezing error. If you can't, then the problem is likely with one of the plugins, and I'd recommend disabling them all then re-enabling one at a time to try and locate the offending one. 

If the problem persists the the problem is in fact with firefox, so next I'd run firefox from the terminal (just open the terminal and type "firefox") then when it freezes flip over to the terminal and copy the output back here.

I'll try it.  Thanks.

---

### Post by pluckypigeon on 2009-05-20
did you fix this problem?

---

### Post by josephellengar on 2009-05-20
> **pluckypigeon said:**
> did you fix this problem?

No.  I had to go back to ibex.

---

