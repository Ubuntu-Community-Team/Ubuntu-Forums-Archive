---
title: "Conky Help!!!"
date: 2008-04-15
forum: Desktop Effects &amp; Customization
---

### Post by JECHO on 2008-04-15
Hey guys i was trying to set up conky... i got everything set but when i reboot and have conky run at startup, it sits on top of other windows. i reboot and let everything load (including conky) then when i open up firefox, or any other app, it opens underneath the conky display. how do i  it so that conky runs behind all other open windows? staying only on the desktop.



also: ive tried using all different kinds of .conkyrc files but i have the same problem.:confused:

---

### Post by cammin on 2008-04-15
There should be a line in the conky config file that probably says

**own_window_type=override**

change it to 

**own_window_type=normal**
or
**own_window_type=desktop**

If it says **normal** now.
go to the line that says

**own_window_hints=**

and delete the word **above** if it's there.

---

