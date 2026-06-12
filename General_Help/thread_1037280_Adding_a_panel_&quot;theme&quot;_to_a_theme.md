---
title: "Adding a panel &quot;theme&quot; to a theme"
date: 2009-01-11
forum: General Help
---

### Post by Jameshardy88 on 2009-01-11
Hey all i was just wondering how easy it would be to add a panel picture to a custom theme so that wen i change to between say a standard theme and one of my custom themes made from a combination of assorted downloaded themes i would not have to fiddle around with my panel each time

thanks for any help 

JamesHardy

---

### Post by blackened on 2009-01-11
It's really not that hard. Browse through your themes folder and find one that includes a panel.rc file. From there you should be able to sift through until you find what you're looking for. Remember that panel.rc needs to be listed as an include in the gtkrc file.

When editing pre-existing themes, I find it useful to make a copy of the theme and work on that. That way if I trash something and can't fix it, then I can always start again from scratch without having to re-download the theme.

---

