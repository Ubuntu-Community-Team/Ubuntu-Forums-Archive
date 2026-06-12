---
title: "XFCE xkb Layout switcher problem"
date: 2006-03-16
forum: Desktop Environments
---

### Post by Sydney Hieronymous Zitbag on 2006-03-16
Hi folks,

my problem is quite odd. Currently I am using US,HU,IT keyboard layouts. 
1) When I change it with setxkbmap, the layout is changed but the indicator is not updated. On the other hand, clicking on the button works well (changes to the next layout)
2) The indicated layout flag / code does not correspond with the real layout. That is,
when I set US, the plugin is showing 'PC'
then I change to HU, the plugin switches to 'US'
then I change again to 'IT', and the plugin says 'HU'
the next change resets US keyboard layout (and the label 'PC') ofcourse.

any ideas?

---

### Post by Sydney Hieronymous Zitbag on 2006-03-16
I made some investigation, but unfortunately with no ssuccess. Obviously only the language indication is affected by this problem, the keyboard layout changer is operating perctly anyways. My naive intention is, that there should be a configuration file below the standard xorg.conf that tells the xkb-switcher which codes/flags to show.
Does such a file exist? Could anyone give me a hint how to figure out, how this applet works?

---

