---
title: "Ubuntu Themes problems"
date: 2007-08-26
forum: Desktop Environments
---

### Post by chee on 2007-08-26
hello     i was running beryl as my theme manager but found it a little annoying after a while(mainly when watching certain videos on the internet) so i used my synaptics manager and marked the files for removal and applied it. that worked fine except that now when i open a window the border seems to be missing and the top block that you would click and hold to drag the window and that also has the minimize , maximize and close buttons is not there.  any suggestions would be great.

---

### Post by mtbsoft on 2007-08-26
It could be that the Window Manager is somehow remembering the Decorator (the buttons and border) settings from when you were running Beryl - I occasionally find the decorators are missing and have to run the Reload Window Decorator menu option to reset them.

It might be worth reloading Beryl and explicitly setting the Window Manager to Metacity and then remove Beryl again - hopefully this will clear whatever is blocking the correct decorator from appearing.  Better still, select Metacity then reboot before removing Beryl, just to be sure.

Hope this works.

---

### Post by mcduck on 2007-08-27
Try running "metacity --replace" in a terminal.

---

### Post by chee on 2007-08-27
actually that worked perfect   thank you! you don't know how annoying it it to surf the net and have to right click and close every window that pops up.  plus i was pretty sure that there was an easy way , but i am kinda new. thanks again

---

