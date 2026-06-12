---
title: "How do I create a force-quit with Nice priority -20"
date: 2012-04-11
forum: Desktop Environments
---

### Post by lotuseclat79 on 2012-04-11
I use Ubuntu Natty (11.04) from a USB flash drive, and have my own setup scripts for the way I like it, and use Firefox 3.6.28 (for numerous add-ons which are not yet supported by later versions of Firefox) which will soon be retired from Mozilla support later this month.

AFAIK, Firefox still suffers from the mouse-click freeze problem, and I assume that when this happens (maybe if I am lucky), this may only affect the browser.  The mouse can be moved, but nothing happens when the regular force-quit button is clicked on and all seems to be frozen (but is that really the case, e.g. are OS components being scheduled when this happens?).

Another assumption I am making is that if a force-quit button can be created with the -20 Nice priority, then maybe I will have a chance to kill Firefox and restart the old session (before the frozen mouse click) or start an entirely new Firefox session.  This may be a faulty assumption on my part, but if it works, then it is worth a try.

One problem I see with the current force-quit with the current Add to Panel default is that it does not have a right-click Properties pull-down like the gnome-terminal icon added to the launcher panel.

I assume that I may have to recompile the source code for force-quit which may be xkill (if I remember a file I saved from a thread in these forums) in order to instantiate a launcher with the Properties right-click option (presumably it would make it easier to create the Nice -20 priority at launch with this feature).

Thanks for any help,

-- Tom

---

### Post by Frogs Hair on 2012-04-11
> AFAIK, Firefox still suffers from the mouse-click freeze problem I have never experienced this on the six Ubuntu releases I have used . You would have change the force quit to include the features you want. This link may be of interest. [http://saravananthirumuruganathan.wordpress.com/2011/08/05/tutorial-on-writing-ubuntu-lensesplaces-in-python/](http://saravananthirumuruganathan.wordpress.com/2011/08/05/tutorial-on-writing-ubuntu-lensesplaces-in-python/)

---

