---
title: "WINE display problem"
date: 2007-06-25
forum: Gaming &amp; Leisure
---

### Post by Jordan777 on 2007-06-25
When the little box comes up when I type in **winecfg** in the Terminal it is just small enough so that is cuts off apply and whatever else is down there.  Is there a way for me to expand the I guess what you'd call the virtual desktop?  Any help is appreciated.:KS

---

### Post by cogadh on 2007-06-25
Make sure Wine is not running and open the user.reg file (found in your .wine directory) in a text editor. Find this entry:
[Software\\Wine\\X11 Driver]
It should be at the very end of the file. Immediately after that entry will be your virtual desktop setting, change it to at least 800x600 to get access to all the buttons, but don't set it to your current desktop resolution, it will be too big to fit on the screen properly.

---

### Post by Jordan777 on 2007-06-25
Thank you very much worked perfectly! :p

---

### Post by cogadh on 2007-06-25
No problem, good luck "Wine"ing :)

---

