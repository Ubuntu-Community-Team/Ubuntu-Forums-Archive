---
title: "Editing clock in 12.04 (Gnome classic)?"
date: 2012-09-17
forum: Desktop Environments
---

### Post by ShadowVegan on 2012-09-17
I just switched from 10.04 to 12.04. When I click the clock and click 'Time & Date Settings' it opens up the general System Settings menu (which itself is a problem, it should go directly to Time/Date settings, but that doesn't concern me). From there I navigate to 'Date and Time'. It gives me the option to switch between AM/PM and 24 hour, but regardless of which I choose, it stays at AM/PM. Is there any way to fix this? I also want it to display seconds, and the day of the week, both of which were options in 10.04 but I can't find options for those in 12.04, is there any way to add those features?

---

### Post by Krytarik on 2012-09-18
Please see both of these links:

[LIST]
[*][http://askubuntu.com/questions/129985/how-to-make-the-date-appear-next-to-the-time-indicator-in-gnome-classic](http://askubuntu.com/questions/129985/how-to-make-the-date-appear-next-to-the-time-indicator-in-gnome-classic)
[/LIST]

[LIST]
[*][http://ubuntuforums.org/showthread.php?p=11818848#post11818848](http://ubuntuforums.org/showthread.php?p=11818848#post11818848)
[/LIST]
Regards.

---

### Post by ShadowVegan on 2012-09-18
It worked, thanks!

```
gsettings set com.canonical.indicator.datetime time-format custom && gsettings set com.canonical.indicator.datetime custom-time-format "%a %d %b %k:%M:%S"
```

---

