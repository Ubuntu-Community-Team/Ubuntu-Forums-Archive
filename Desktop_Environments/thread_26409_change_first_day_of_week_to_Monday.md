---
title: "change first day of week to Monday?"
date: 2005-04-12
forum: Desktop Environments
---

### Post by savanna on 2005-04-12
I've just upgraded one of my machines to Ubuntu Hoary - very nice.

I've noticed however that the first day of the week defaults to Sunday
rather than Monday, and I can't find a way of changing it. Any pointers?

For example, in the date applet (bottom right hand corner) and JPilot
(Palm Pilot app). I've trawled thru the Configuration Editor
(Applications, System Tools), couldn't find anything.

Aside from the religious issue (I'm not Christian) and the nationality 
issue (I'm not American) :-P , there's also the <religious> issue - 
one of the reasons I use linux is that I can configure things 
how **I** want them... :-)

---

### Post by gozala on 2008-04-19
* check which locale is running, using the locale command (ie en_US)
    * sudo gedit /usr/share/i18n/locales/en_US and change first_weekday to 2
    * regenerate the locale using sudo locale-gen
    * get the calendar to reload using killall gnome-panel

---

