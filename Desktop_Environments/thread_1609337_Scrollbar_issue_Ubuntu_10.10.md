---
title: "Scrollbar issue Ubuntu 10.10"
date: 2010-10-30
forum: Desktop Environments
---

### Post by jazz_air_312 on 2010-10-30
Hy! I am using the GAIA Sprout Theme ([http://lassekongo83.deviantart.com/art/GAIA-Sprout-179554275](http://lassekongo83.deviantart.com/art/GAIA-Sprout-179554275)) and the problem i have is that the theme doesn't use the intended scrollbar in normal user mode, just in administrator mode. So, in nautilus (it's easier to show it here) when i scroll in a large folder, the displayed scrollbar seems to be (as far as i can tell) a default murrine style scrollbar. When i open a folder as administrator, the theme makes use of it's standard scrollbar. I attached a screenshot so you can see the problem, the top window is in normal use mode (with ugly scrollbar), the bottom window is in administrator mode (with theme scrollbar). 
I have the Gaia Sprout/gtk-2.0 folder in /home/username/.themes as well as in /usr/share/themes and i have all the necessary engines installed and up to date.
The theme includes a scrollbar.rc file that i added to the gtkrc (include "scrollbar.rc"), however this doesn't fix the problem.
Any help is really appreciated :D

---

### Post by jazz_air_312 on 2010-11-01
i've looked into the matter a bit more and i've noticed that it only happens with themes that come with multiple .rc files. There is no problem with the default ubuntu themes or murrine themes that only have the gtkrc config file and the scrollbars defined there. Any ideas?

---

